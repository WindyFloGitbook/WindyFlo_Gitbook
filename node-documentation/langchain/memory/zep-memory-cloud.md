# Zep Memory - Cloud

Zep Memory - Cloud 노드는 클라우드 기반 Zep API와 연동하여, 대화 히스토리를 영속적(perpetual)으로 저장하고 관리하는 메모리 노드입니다. 사용자와 AI의 발화를 구분하고 다양한 키 지정이 가능하여, 구조화된 고급 챗봇 시스템에 적합합니다.

***

### 주요 기능

* Zep Cloud API와 연동된 고가용성 메모리 저장소 제공
* `perpetual` 타입을 통해 장기 보존 메모리 구현 가능
* 사용자/AI 발화 구분을 위한 Prefix 지정
* 다양한 Key 설정으로 LLM과 유연하게 연동 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-19 175506 (1).png" alt=""><figcaption><p>WindyFlo Zep Memory - Cloud</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-19 175520.png" alt=""><figcaption><p>WindyFlo Zep Memory - Cloud Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                      | 필수 여부 |
| ------------------ | --------------------------------------- | ----- |
| Connect Credential | Zep Cloud API 인증 정보 (Credential에 등록 필요) | 필수    |

***

### 파라미터 (Parameters)

| 항목           | 설명                                      |
| ------------ | --------------------------------------- |
| Session Id   | 사용자 또는 세션 고유 식별자                        |
| Memory Type  | 메모리 보존 방식 지정 (`perpetual`, `session` 등) |
| AI Prefix    | AI 발화에 붙는 접두어 (예: `ai`)                 |
| Human Prefix | 사용자 발화에 붙는 접두어 (예: `human`)             |
| Memory Key   | LLM과 연결할 히스토리 키 (예: `chat_history`)     |
| Input Key    | 입력 메시지를 담는 키 (예: `input`)               |
| Output Key   | 출력 메시지를 담는 키 (예: `text`)                |

***

### 출력값 (Outputs)

| 출력 항목     | 설명                      |
| --------- | ----------------------- |
| ZepMemory | Zep Cloud 기반의 메모리 객체 반환 |

***

### 활용 예시

* 사용자별 장기 기억 기능이 필요한 AI 상담 시스템
* 세션 종료 후에도 대화 기록을 유지해야 하는 퍼시스턴트 챗봇
* 사용자와 AI의 메시지를 명확히 구분해 기록·분석하는 서비스
* 클라우드 기반으로 확장성 있는 대화 데이터 관리 구조 구성

***

### 사용 팁

* Zep Cloud 가입 후 발급받은 API Key를 Credential에 등록해야 합니다.
* Memory Type은 `perpetual` 외에도 `session` 등으로 설정 가능하나, 장기 저장에는 `perpetual` 사용 권장
* Input/Output Key 설정은 연결되는 LLM 노드의 Key 설정과 반드시 일치시켜야 합니다.
* AI/Human Prefix를 설정하면 Zep에서 메시지 역할을 정확히 판단하여 요약·검색 기능의 품질이 향상됩니다.

***

### 주의사항

* Connect Credential이 누락되면 Zep Cloud API 호출이 불가능합니다.
* Zep Cloud는 요금제에 따라 저장량, API 호출 횟수 등에 제한이 있으므로 사전 확인이 필요합니다.
* Session ID가 없을 경우, 전체 세션이 하나로 취급되어 사용자별 히스토리 분리가 어렵습니다.
* 반드시 Agent 또는 LLM 노드와 함께 연결하여 사용해야 실제 동작합니다.
