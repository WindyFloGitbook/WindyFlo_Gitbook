# SQLite Agent Memory

SQLite Agent Memory 노드는 로컬 파일 기반의 경량 데이터베이스인 SQLite를 사용하여 에이전트 메모리를 저장할 수 있는 노드입니다. 별도의 DB 서버가 필요하지 않아 로컬 테스트나 소규모 프로젝트에 적합합니다.

***

### 주요 기능

* 별도 서버 없이 파일 기반으로 에이전트 메모리 저장 가능
* 간단한 구조로 빠르게 메모리 기능 구현 가능
* Additional Connection Configuration을 통한 경로 및 파일 설정 가능
* 로컬에서 반복 테스트 시, 상태를 유지한 대화 시뮬레이션에 유리

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 135525.png" alt=""><figcaption><p>WindyFlo SQLite Agent Memory</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 135538.png" alt=""><figcaption><p>WindyFlo SQLite Agent Memory Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                    | 설명                                 | 필수 여부 |
| --------------------- | ---------------------------------- | ----- |
| Additional Parameters | 메모리 파일 경로 등 커스텀 설정 입력 (JSON 형식 사용) | 선택    |

***

### 파라미터 (Parameters)

| 항목                                  | 설명                                                |
| ----------------------------------- | ------------------------------------------------- |
| Additional Connection Configuration | DB 파일 위치 등 추가 설정 가능. 예: `{"path": "./memory.db"}` |

***

### 출력값 (Outputs)

| 출력 항목             | 설명                       |
| ----------------- | ------------------------ |
| SQLiteAgentMemory | SQLite 기반 에이전트 메모리 객체 반환 |

***

### 활용 예시

* 로컬 테스트 환경에서 대화 상태를 저장하고 재사용하는 에이전트 개발
* 파일 기반 저장소로 외부 DB 없이 간단한 챗봇 메모리 기능 구현
* 서버 없이도 작동 가능한 간단한 AI 데모 및 PoC(Proof of Concept) 시나리오 구축
* 일시적 대화 기록을 남겨두고 결과를 비교하는 QA 테스트 환경 구성

***

### 사용 팁

* 기본적으로 메모리 파일은 로컬 디렉토리에 생성되며, 경로를 명시하지 않으면 프로젝트 루트에 저장됩니다.
* Additional Connection Configuration에서 `"path"` 키를 활용하여 저장 경로를 명확히 설정하는 것이 좋습니다.
* 공유 폴더에 설정하면 여러 사용자 간 메모리 공유도 가능합니다.

***

### 주의사항

* 파일 시스템에 쓰기 권한이 없는 경로를 지정하면 에러가 발생합니다.
* SQLite는 경량 DB이므로 다수의 동시 접근이나 고속 트랜잭션 처리에는 적합하지 않습니다.
* 고정된 스키마를 사용하므로, 커스텀 필드나 구조 변경은 제한적입니다.
* 단독 사용은 불가하며 반드시 Agent 노드와 함께 연결해야 의미가 있습니다.
