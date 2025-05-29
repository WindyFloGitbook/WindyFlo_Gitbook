# Conversation Summary Memory

Conversation Summary Memory 노드는 이전 대화 기록을 LLM을 활용해 지속적으로 요약하며 저장하는 구조의 메모리입니다. 토큰 수를 효율적으로 관리하면서도 장기적인 대화 흐름을 유지하고자 할 때 적합합니다.

***

### 주요 기능

* 전체 대화 내용을 실시간으로 요약하여 컨텍스트 부담을 줄임
* LLM 기반 요약 기능을 통해 맥락 손실 없이 요약 유지 가능
* `Chat Model`을 활용한 자동 요약 처리
* Session ID 기반 다중 사용자 구분 및 상태 추적 지원

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 162435.png" alt=""><figcaption><p>WindyFlo Conversation Summary Memory</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 162443.png" alt=""><figcaption><p>WindyFlo Conversation Summary Memory Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목         | 설명                                                    | 필수 여부 |
| ---------- | ----------------------------------------------------- | ----- |
| Chat Model | 대화 내용을 요약할 LLM 노드 지정 (예: ChatOpenAI, ChatAnthropic 등) | 필수    |
| Session Id | 세션 또는 사용자 식별자 (빈 값일 경우 고정 세션으로 동작)                    | 선택    |
| Memory Key | 대화 히스토리를 저장할 키 (예: `chat_history`)                    | 필수    |

***

### 출력값 (Outputs)

| 출력 항목                     | 설명                      |
| ------------------------- | ----------------------- |
| ConversationSummaryMemory | 요약된 대화 히스토리가 포함된 메모리 객체 |

***

### 활용 예시

* 전체 대화를 요약해 유지하며 빠르게 맥락을 파악해야 하는 업무용 챗봇
* 사용자의 주요 요청을 자동 요약하여 후속 질의 응답에 활용
* 장기 세션을 다루는 AI 상담사나 비서 서비스에서의 컨텍스트 유지
* 매번 전체 대화를 재전달하는 대신 요약본으로 효율적인 응답 제공

***

### 사용 팁

* `Chat Model`은 요약에 최적화된 모델을 사용하는 것이 좋습니다 (예: GPT-4, Claude 등).
* `Session Id`를 명확히 지정하면 사용자별 상태 추적 및 개별 기록 유지에 유리합니다.
* 요약된 결과는 LLM 입력 컨텍스트에 직접 포함되므로, 요약 품질이 응답 품질에 영향을 미칩니다.

***

### 주의사항

* `Chat Model`을 지정하지 않으면 요약 기능이 작동하지 않으며, 실행 시 오류가 발생합니다.
* Token 제한은 자동 관리되지 않으므로, 매우 긴 세션에서는 요약 누락 가능성이 존재합니다.
* 요약이 반복될수록 초반 내용이 점차 단순화될 수 있어, 중요한 정보는 별도로 보관하는 것이 좋습니다.
* 반드시 Agent 또는 LLM 노드와 함께 연결하여 사용해야 의미가 있습니다.
