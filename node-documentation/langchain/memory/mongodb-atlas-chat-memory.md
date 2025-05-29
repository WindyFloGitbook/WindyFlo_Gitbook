# MongoDB Atlas Chat Memory

MongoDB Atlas Chat Memory 노드는 클라우드 기반 NoSQL 데이터베이스인 MongoDB Atlas에 대화 히스토리를 저장하고 불러올 수 있는 메모리 노드입니다. 높은 확장성과 유연한 스키마 구조를 활용하여 다양한 대화형 AI 서비스에 적합합니다.

***

### 주요 기능

* MongoDB Atlas 클라우드 환경에 대화 기록 영구 저장 가능
* Database, Collection 이름 지정으로 유연한 데이터 분리 관리
* Session ID 기반 사용자 구분 및 멀티 세션 동시 지원
* 메모리 키 설정을 통해 LLM과의 연동 포맷 제어

<figure><img src="../../../.gitbook/assets/image (86).png" alt=""><figcaption><p>WindyFlo MongoDB Atlas Chat Memory</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (87).png" alt=""><figcaption><p>WindyFlo MongoDB Atlas Chat Memory Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                      | 필수 여부 |
| ------------------ | --------------------------------------- | ----- |
| Connect Credential | MongoDB Atlas 인증 정보 (Credential에 등록 필요) | 필수    |
| Database           | 연결할 MongoDB 데이터베이스 이름 (예: `ai_chat_db`) | 필수    |
| Collection Name    | 저장할 컬렉션 이름 (예: `chat_memory`)           | 필수    |
| Session Id         | 사용자 또는 세션 구분 식별자                        | 선택    |
| Memory Key         | 대화 히스토리를 저장할 키 (예: `chat_history`)      | 필수    |

***

### 출력값 (Outputs)

| 출력 항목                  | 설명                        |
| ---------------------- | ------------------------- |
| MongoDBAtlasChatMemory | MongoDB 기반 에이전트 메모리 객체 반환 |

***

### 활용 예시

* AI 고객 상담 서비스에서 사용자별 대화 기록을 장기 보관
* 데이터베이스 중심으로 세션 관리가 필요한 엔터프라이즈 챗봇
* 다양한 프로젝트·서비스 단위로 분리된 Collection 운영
* MongoDB의 복잡 쿼리 및 분석 기능을 활용한 대화 데이터 분석 시스템

***

### 사용 팁

* Database와 Collection은 사전에 생성되어 있어야 하며, Credential에 등록된 계정에 쓰기 권한이 있어야 합니다.
* Session ID는 사용자 구분뿐 아니라, 특정 대화 흐름을 분리 관리할 때 유용합니다.
* Memory Key는 LLM 노드에서 사용하는 히스토리 키와 동일하게 유지해야 정상 작동합니다.

***

### 주의사항

* Connect Credential에 MongoDB URI를 등록하지 않으면 연결이 불가능합니다.
* Database 또는 Collection 이름이 잘못되었거나 권한이 없는 경우, 실행 시 오류 발생
* MongoDB 요금제에 따라 저장량 및 처리량에 제한이 있을 수 있으므로 사전 확인 필요
* 단독 사용은 의미가 없으며, 반드시 Agent 또는 LLM 노드와 연결하여 사용해야 합니다.
