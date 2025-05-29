# Upstash Redis-Backed Chat Memory

Upstash Redis-Backed Chat Memory 노드는 서버리스 Redis 서비스인 Upstash를 백엔드로 사용하여, LLM과의 대화 히스토리를 저장 및 관리할 수 있는 메모리 노드입니다. REST 기반 API를 활용하므로 백엔드 환경에 제약 없이 경량화된 서비스 구현이 가능합니다.

***

### 주요 기능

* Upstash Redis를 기반으로 한 외부 저장형 메모리 제공
* REST API URL 기반 설정으로 서버리스 아키텍처에 적합
* Session Timeout을 통한 TTL 기반 자동 만료 기능 지원
* Session ID 기반 사용자별 대화 흐름 구분 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-19 174753.png" alt=""><figcaption><p>WindyFlo Upstash Redis-Backed Chat Memory</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-19 174805.png" alt=""><figcaption><p>WindyFlo Upstash Redis-Backed Chat Memory Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                     | 설명                                                            | 필수 여부 |
| ---------------------- | ------------------------------------------------------------- | ----- |
| Connect Credential     | Upstash Redis 접속 정보 (Credential에 등록 필요)                       | 필수    |
| Upstash Redis REST URL | Redis 호출에 사용할 고유 REST URL (예: `https://<your-db>.upstash.io`) | 필수    |

***

### 파라미터 (Parameters)

| 항목               | 설명                                         |
| ---------------- | ------------------------------------------ |
| Session Id       | 세션 또는 사용자 고유 식별자                           |
| Session Timeouts | 세션 만료 시간 설정 (초 단위, 예: `3600`)              |
| Memory Key       | LLM 연결 시 사용할 히스토리 키 이름 (예: `chat_history`) |

***

### 출력값 (Outputs)

| 출력 항목                        | 설명                          |
| ---------------------------- | --------------------------- |
| UpstashRedisBackedChatMemory | Upstash Redis 기반의 메모리 객체 반환 |

***

### 활용 예시

* 서버리스 기반의 챗봇에서 외부 메모리 저장소로 Upstash 사용
* 단기 세션 대화 기록 저장 및 자동 만료 처리
* 브라우저 환경에서도 REST API 기반 메모리 연동이 필요한 경우
* 실시간 반응 속도가 중요한 SaaS 서비스에서 사용자별 대화 유지

***

### 사용 팁

* Upstash 콘솔에서 Redis 인스턴스를 생성하고 REST URL과 Token을 Credential에 등록해야 합니다.
* Session Timeout을 활용하면 일정 시간 이후 자동으로 세션 데이터를 제거할 수 있어 자원 최적화에 유리합니다.
* Memory Key는 LLM 또는 Agent 노드에서 동일한 키로 지정되어야 히스토리 연동이 정상적으로 작동합니다.

***

### 주의사항

* Connect Credential 또는 REST URL이 누락되면 Redis 호출 자체가 불가능합니다.
* Upstash는 요금제에 따라 API 호출 수 및 데이터량 제한이 존재하므로 사용 전 확인 필요
* TTL이 너무 짧게 설정되면 사용 중 세션 만료로 인해 대화 맥락이 사라질 수 있습니다.
* 반드시 Agent 또는 LLM 노드와 함께 연결해 사용해야 의미가 있습니다.
