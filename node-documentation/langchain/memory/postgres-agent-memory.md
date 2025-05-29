# Postgres Agent Memory

Postgres Agent Memory 노드는 에이전트의 기억 데이터를 PostgreSQL 데이터베이스에 저장 및 불러올 수 있도록 설계된 노드입니다. 세션 간 대화 맥락 유지가 필요한 다양한 에이전트 시나리오에 활용됩니다.

***

### 주요 기능

* PostgreSQL 기반 장기 메모리 저장 기능 제공
* Host, Database, Port 입력을 통해 유연한 연결 구성 가능
* Additional Connection Configuration으로 고급 DB 연결 설정 지원
* 멀티 유저 또는 세션 기반 대화 기록 저장에 최적화

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 135231.png" alt=""><figcaption><p>WindyFlo Postgres Agent Memory</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 135246.png" alt=""><figcaption><p>WindyFlo Postgres Agent Memory Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                                    | 필수 여부 |
| ------------------ | ----------------------------------------------------- | ----- |
| Connect Credential | PostgreSQL 접속 정보 (Credential에 등록 필요)                  | 필수    |
| Host               | PostgreSQL 서버 주소 (예: `localhost`, `pg.mycompany.com`) | 필수    |
| Database           | 대상 데이터베이스 이름                                          | 필수    |
| Port               | 포트 번호 (기본값: 5432)                                     | 선택    |

***

### 파라미터 (Parameters)

| 항목                                  | 설명                                                |
| ----------------------------------- | ------------------------------------------------- |
| Additional Connection Configuration | DB 파일 위치 등 추가 설정 가능. 예: `{"path": "./memory.db"}` |

***

### 출력값 (Outputs)

| 출력 항목       | 설명                           |
| ----------- | ---------------------------- |
| AgentMemory | PostgreSQL 기반 에이전트 메모리 객체 반환 |

***

### 활용 예시

* 다중 사용자의 대화 이력을 세션 단위로 기록 및 복원하는 고객 상담 에이전트 구현
* PostgreSQL을 기존에 사용 중인 인프라에 통합하여 운영 중인 에이전트 메모리 관리
* 고가용성 서버에 저장된 메모리 데이터를 통한 대화 분석 및 모델 튜닝
* 장기 유지형 멀티턴 챗봇에 기억 기능을 부여하여 사용 경험 향상

***

### 사용 팁

* Credential에 사용자명, 비밀번호, 호스트, 포트 정보를 등록해두면 반복 입력 없이 연결 가능
* Database 이름은 사전에 생성되어 있어야 하며 접근 권한도 확인 필요
* Additional Configuration을 통해 SSL 암호화, 커넥션 타임아웃 등 세부 설정이 가능

***

### 주의사항

* Credential이 등록되지 않으면 실행 시 오류가 발생합니다.
* Database나 Host 정보가 정확하지 않으면 연결 실패 및 세션 저장 불가
* PostgreSQL 인스턴스가 외부 접근을 허용하는지 방화벽 설정을 반드시 확인해야 합니다.
* 단독 사용은 불가하며, 반드시 Agent 노드와 연결하여 메모리 기능을 구현해야 합니다.
