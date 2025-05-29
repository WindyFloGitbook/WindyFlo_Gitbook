# Supervisor

Supervisor 노드는 복수의 Worker 노드(작업 에이전트)를 관리하고 조율하는 메타 에이전트 노드입니다. 주어진 사용자 요청에 따라 적절한 Worker를 선택해 작업을 분배하고, 결과를 바탕으로 다음 작업을 이어가는 멀티 에이전트 운영 시나리오에서 사용됩니다.

***

### 주요 기능

* Worker 노드들을 통제하고 순차적 협업 수행
* Supervisor Prompt를 통해 역할 기반 지시 가능
* Recursion Limit 설정을 통한 실행 깊이 제어
* Summarization 옵션으로 중간 결과 요약 기능 제공

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-19 180050.png" alt=""><figcaption><p>WindyFlo Supervisor</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-19 180059.png" alt=""><figcaption><p>WindyFlo Supervisor Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                      | 설명                             | 필수 여부 |
| ----------------------- | ------------------------------ | ----- |
| Tool Calling Chat Model | Supervisor가 사용하는 메인 LLM 노드     | 필수    |
| Agent Memory            | Supervisor용 메모리 노드 (대화 상태 유지용) | 선택    |
| Input Moderation        | 입력 검열을 위한 Moderation 노드 연결     | 선택    |

***

### 파라미터 (Parameters)

| 항목                | 설명                                             |
| ----------------- | ---------------------------------------------- |
| Supervisor Name   | Supervisor 에이전트의 이름 (예: `Supervisor`)          |
| Supervisor Prompt | Supervisor가 작업을 조율하기 위한 시스템 프롬프트               |
| Summarization     | 각 워커 응답을 요약할지 여부 (기본값: false)                  |
| Recursion Limit   | Supervisor가 워커와 상호작용할 수 있는 반복 최대 횟수 (예: `100`) |

***

### 출력값 (Outputs)

| 출력 항목      | 설명                               |
| ---------- | -------------------------------- |
| Supervisor | Supervisor 실행 결과 및 워커 상호작용 기록 반환 |

***

### 활용 예시

* LLM 기반 문서 생성, 검수, 배포를 여러 Worker에 나눠 실행할 때
* 사용자 요청을 분석하고 적절한 처리 순서를 자동으로 조정하는 다단계 업무 시스템
* 복잡한 분석이나 협업적 응답이 필요한 AI 고객 응대 시스템
* 체계적인 역할 분담 및 자동 순서 제어가 필요한 오케스트레이션 파이프라인

***

### 사용 팁

* Supervisor Prompt는 `{team_members}` 프롬프트 변수를 포함해야 하며, 각 워커의 역할을 명확히 정의해야 효과적입니다.
* Recursion Limit은 무한 루프 방지를 위해 적절한 숫자로 설정하는 것이 좋습니다 (예: 50\~100).
* Summarization 기능을 켜면 결과 로그가 간결해지나, 정보 손실 가능성도 있습니다.
* Input Moderation 노드를 연결하면 악의적 입력에 대한 방어력을 확보할 수 있습니다.

***

### 주의사항

* Tool Calling Chat Model 연결 없이 Supervisor는 작동하지 않습니다.
* Supervisor Prompt가 불명확하거나 team\_members 정의가 부적절할 경우, 워커 선택이 비효율적으로 이루어질 수 있습니다.
* Recursion Limit이 지나치게 크면 성능 저하 및 비용 증가가 발생할 수 있습니다.
* Worker 노드는 별도로 구성 및 연결되어 있어야 하며, Supervisor는 이들을 호출만 수행합니다.
