# Redis-Backed Chat Memory

Redis-Backed Chat Memory 노드는 고속의 인메모리 데이터 저장소인 Redis를 기반으로 대화 히스토리를 저장하는 메모리 노드입니다. 빠른 응답 속도와 TTL(Time-To-Live) 설정을 통해 일시적 또는 세션 기반 메모리에 적합합니다.

***

### 주요 기능

* Redis를 백엔드로 사용하여 고속 대화 히스토리 저장 및 조회
* Session ID 및 Timeouts 설정을 통한 세션 단위 관리 지원
* Window Size 설정을 통해 히스토리 유지 범위 제어 가능
* Memory Key를 통해 LLM과 연동되는 히스토리 항목 지정

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-16 174952.png" alt=""><figcaption><p>WindyFlo Redis-Backed Chat Memory</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-16 175000.png" alt=""><figcaption><p>WindyFlo Redis-Backed Chat Memory Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                      | 필수 여부 |
| ------------------ | --------------------------------------- | ----- |
| Connect Credential | Redis 접속 정보 (Credential에 등록 필요)         | 필수    |
| Session Id         | 사용자 또는 세션 고유 식별자                        | 선택    |
| Session Timeouts   | 세션 만료 시간 (초 단위 TTL, 예: `3600`)          | 선택    |
| Memory Key         | LLM과 연결되는 히스토리 키 이름 (예: `chat_history`) | 필수    |
| Window Size        | 유지할 대화 히스토리 수 (예: `5` → 최근 5턴만 유지)      | 선택    |

***

### 출력값 (Outputs)

| 출력 항목                 | 설명                     |
| --------------------- | ---------------------- |
| RedisBackedChatMemory | Redis 기반의 대화 메모리 객체 반환 |

***

### 활용 예시

* 사용자별 대화 상태를 짧은 시간 동안 유지해야 하는 실시간 서비스 (예: 퀴즈 챗봇)
* TTL 기반 세션 자동 만료가 필요한 시스템 (예: 인증 흐름 등)
* 최근 대화 일부만 유지하면서 응답 속도를 최우선시 하는 경량 챗봇
* 실시간성이 중요한 비즈니스 채팅 상담 서비스

***

### 사용 팁

* Session Timeouts 설정 시 Redis TTL 기능을 활용하여 메모리를 자동 정리할 수 있습니다.
* Window Size를 설정하면 과거 히스토리 과잉 누적을 방지할 수 있습니다.
* LLM 노드에서도 동일한 Memory Key를 설정해야 일관된 히스토리 전달이 가능합니다.
* Redis Cluster 환경에서는 접속 포트, 호스트 등 Credential 등록 값을 정확히 지정해야 합니다.

***

### 주의사항

* Connect Credential 미등록 시 Redis 서버에 접근할 수 없습니다.
* TTL이 너무 짧게 설정되면 대화 도중 세션이 만료될 수 있습니다.
* Window Size가 설정되지 않으면 전체 히스토리를 저장하게 되므로, 토큰 초과 주의 필요
* 단독 사용은 불가하며, 반드시 Agent 또는 LLM 노드와 함께 연결해야 의미가 있습니다.
