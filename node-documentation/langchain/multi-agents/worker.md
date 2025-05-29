# Worker

Worker 노드는 Supervisor 노드로부터 할당받은 작업을 수행하는 개별 실행 에이전트입니다. 각 Worker는 고유한 역할과 프롬프트를 가지고 있으며, 외부 도구를 사용할 수 있고, LLM을 기반으로 반복적 작업 수행이 가능합니다.

***

### 주요 기능

* Supervisor로부터 요청받은 작업을 LLM 기반으로 수행
* Worker Prompt를 기반으로 개별 역할 설정 가능
* 도구(Tools) 연결을 통해 Web 검색, 계산 등 확장 작업 지원
* Format Prompt Values로 프롬프트 변수 치환 기능 지원

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-19 180519.png" alt=""><figcaption><p>WindyFlo Worker</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-19 180553 (1).png" alt=""><figcaption><p>WindyFlo Worker Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                      | 설명                                                     | 필수 여부 |
| ----------------------- | ------------------------------------------------------ | ----- |
| Tools                   | Worker가 사용할 수 있는 도구 리스트 (예: Web Browser, Calculator 등) | 선택    |
| Supervisor              | 연결된 Supervisor 노드 (작업 지시자 역할)                          | 필수    |
| Tool Calling Chat Model | 실행에 사용할 LLM 노드                                         | 필수    |

***

### 파라미터 (Parameters)

| 항목                   | 설명                                                            |
| -------------------- | ------------------------------------------------------------- |
| Worker Name          | Worker의 고유 이름 (예: `Researcher`)                               |
| Worker Prompt        | Worker의 역할과 작업 방식 정의 (예: `"You are a research assistant..."`) |
| Format Prompt Values | 프롬프트 내 `{변수}` 값을 동적으로 설정할 수 있는 매핑 객체                          |
| Max Iterations       | 해당 Worker가 Supervisor 요청에 응답할 수 있는 최대 반복 횟수 (기본값 없음)          |

***

### 출력값 (Outputs)

| 출력 항목  | 설명                      |
| ------ | ----------------------- |
| Worker | Worker 실행 결과 및 수행 로그 반환 |

***

### 활용 예시

* Researcher, Planner, Coder 등 역할별 Worker를 구성하여 다단계 문제 해결
* Web Browser, Search API 등 도구와 결합한 정보 수집/처리 Agent
* 포맷팅된 변수 값 기반 프롬프트 생성 시나리오
* Supervisor 노드와 함께 멀티에이전트 기반 자동화 워크플로우 구현
* MCP 도구를 활용해 외부 서비스와의 연동

***

### 사용 팁

* Worker Prompt는 작업의 역할을 명확히 기술해야 Supervisor와의 협업이 효과적으로 이루어집니다.
* Format Prompt Values는 프롬프트에 포함된 `{변수}`를 외부 입력으로 제어할 때 유용합니다.
* Max Iterations는 무한 루프 방지 및 비용 제어를 위한 제한값으로 설정하는 것이 좋습니다.
* 각 Worker는 실행 종료 후 Supervisor에게 결과를 반환하며, 후속 실행 흐름은 Supervisor가 제어합니다.

***

### 주의사항

* Supervisor 노드와 연결되지 않은 상태에서는 Worker가 트리거되지 않습니다.
* Tool Calling Chat Model 미지정 시 프롬프트 실행 자체가 불가능합니다.
* Worker가 사용하는 Tools는 해당 프롬프트와 기능에 맞게 선택적으로 연결해야 합니다.
* 반복 횟수 제한이 없을 경우, Supervisor와의 상호작용이 예상보다 길어질 수 있으니 주의가 필요합니다.
