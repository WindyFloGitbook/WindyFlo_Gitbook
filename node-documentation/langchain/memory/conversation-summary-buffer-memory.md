# Conversation Summary Buffer Memory

Conversation Summary Buffer Memory 노드는 전체 대화 히스토리를 요약하여 유지하는 방식의 메모리입니다. Token 제한을 초과하지 않으면서도 대화 맥락을 장기적으로 보존하고자 할 때 사용됩니다. 자동 요약을 통해 긴 대화도 간결하게 전달할 수 있습니다.

***

### 주요 기능

* 이전 대화 내용을 LLM을 사용해 요약하고, 요약 내용만 유지
* `Max Token Limit`을 초과하지 않도록 자동으로 문맥을 축약
* `Chat Model`을 활용하여 요약을 생성하므로 더 정교한 맥락 유지 가능
* 긴 대화 세션에서도 전체 맥락을 잃지 않고 압축된 형태로 전달

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 141926.png" alt=""><figcaption><p>Conversation Summary Buffer Memory</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 141932.png" alt=""><figcaption><p>Conversation Summary Buffer Memory Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목              | 설명                                       | 필수 여부 |
| --------------- | ---------------------------------------- | ----- |
| Chat Model      | 요약을 수행할 Chat LLM 노드 지정 (예: ChatOpenAI 등) | 필수    |
| Max Token Limit | 요약 결과 포함 전체 히스토리의 최대 토큰 수 (예: 2000)      | 필수    |
| Session Id      | 사용자 또는 세션 구분 식별자                         | 선택    |
| Memory Key      | 히스토리를 저장할 키 (예: `chat_history`)          | 필수    |

***

### 출력값 (Outputs)

| 출력 항목                           | 설명                     |
| ------------------------------- | ---------------------- |
| ConversationSummaryBufferMemory | 요약된 대화 기록을 포함하는 메모리 객체 |

***

### 활용 예시

* 고객 상담 기록을 요약된 형태로 유지하며 대화 컨텍스트를 반영하는 챗봇 구축
* 장시간 세션에서도 토큰 수 초과 없이 전체 흐름을 유지해야 하는 대화 시스템
* 회의 요약 챗봇, AI 비서 등 장기 문맥 추적이 필요한 시나리오
* 반복적인 질문에도 누적된 맥락 요약을 통해 일관된 응답 유지

***

### 사용 팁

* `Chat Model`은 반드시 요약에 적합한 모델(예: OpenAI GPT, Claude 등)을 지정하십시오.
* `Max Token Limit`은 일반적으로 전체 컨텍스트 토큰 한도(예: 4000)의 절반 이하로 설정하는 것이 좋습니다.
* 동일한 `Session Id`를 사용하면 사용자별로 요약 히스토리를 개별 관리할 수 있습니다.

***

### 주의사항

* `Chat Model`이 누락되면 요약 기능이 작동하지 않으며, 실행 시 오류가 발생합니다.
* 요약 품질은 지정한 LLM의 성능에 따라 달라질 수 있습니다.
* Max Token Limit을 너무 작게 설정할 경우 중요한 맥락이 누락될 수 있습니다.
* 단독 사용은 불가하며, 반드시 Agent 또는 LLM 노드와 함께 연결해야 합니다.
