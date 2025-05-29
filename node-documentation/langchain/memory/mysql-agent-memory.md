# MySQL Agent Memory

MySQL Agent Memory 노드는 에이전트의 장기 기억을 MySQL 데이터베이스에 저장하고 불러오는 기능을 제공합니다. 대화형 AI의 지속적인 맥락 유지가 필요한 경우, 외부 DB 기반 메모리 저장소로 활용됩니다.

***

### 주요 기능

* 에이전트 메모리를 MySQL에 영구 저장하여 세션 간 기억 유지
* Host, Database, Port 등 연결 정보 입력을 통한 유연한 설정
* 다양한 Additional Connection Configuration 설정을 통한 고급 연결 구성 가능
* 대용량 데이터 저장과 복수 세션 관리에 적합

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 134926.png" alt=""><figcaption><p>WindyFlo MySQL Agent Memory</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 134936.png" alt=""><figcaption><p>WindyFlo MySQL Agent Memory Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                                 | 필수 여부 |
| ------------------ | -------------------------------------------------- | ----- |
| Connect Credential | MySQL 사용자 인증 정보(Credential에 등록 필요)                 | 필수    |
| Host               | MySQL 서버 호스트 주소 (예: `127.0.0.1`, `db.example.com`) | 필수    |
| Database           | 연결할 데이터베이스 이름                                      | 필수    |
| Port               | MySQL 포트 번호 (기본값: 3306)                            | 선택    |

***

### 파라미터 (Parameters)

| 항목                                  | 설명                                                |
| ----------------------------------- | ------------------------------------------------- |
| Additional Connection Configuration | DB 파일 위치 등 추가 설정 가능. 예: `{"path": "./memory.db"}` |

***

### 출력값 (Outputs)

| 출력 항목       | 설명                                   |
| ----------- | ------------------------------------ |
| AgentMemory | 에이전트 메모리 객체로 반환되며, 이후 에이전트 노드에 연결 가능 |

***

### 활용 예시

* 고객 지원 챗봇에서 사용자의 이전 문의 이력을 기억하는 기능 구현
* 장기적 대화 상태 유지가 필요한 멀티턴 대화형 시스템에 사용
* 복수 사용자별 세션 ID 기반 기억 저장을 통한 개인화 응답 처리
* 에이전트 테스트 시, 이전 기록 로깅과 분석을 위한 DB 백업 용도로 사용

***

### 사용 팁

* Credential에 사용자 이름, 비밀번호, 호스트 등 기본 연결 정보를 사전 등록해두면 편리합니다.
* Database 이름은 사전에 생성되어 있어야 하며, 접근 권한도 확인해야 합니다.
* Additional Connection Configuration을 활용해 TLS 설정, 타임아웃 설정 등을 추가할 수 있습니다.

***

### 주의사항

* Connect Credential이 누락되면 연결이 되지 않으며, 실행 시 오류가 발생합니다.
* Database가 존재하지 않거나 권한이 없을 경우 연결 실패합니다.
* 외부 DB에 저장된 메모리는 보안 이슈가 발생할 수 있으므로 접근 제어에 유의해야 합니다.
* 반드시 Agent 노드와 함께 사용해야 하며, 단독 사용 시 의미가 없습니다.
