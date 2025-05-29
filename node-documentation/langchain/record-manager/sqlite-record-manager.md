# SQLite Record Manager

SQLite 기반의 로컬 데이터베이스에 AI 처리 결과를 저장하고 관리할 수 있도록 구성된 노드입니다. 외부 DB 서버 연결 없이 빠르게 기록 저장이 가능하며, 파일 기반으로 동작하므로 테스트 환경이나 소규모 프로젝트에서 유용하게 사용됩니다.

***

### 주요 기능

* SQLite 파일 기반의 **로컬 데이터 저장 및 upsert 기능 제공**
* Namespace, SourceId Key를 기반으로 **구조화된 데이터 관리** 가능
* `Cleanup` 옵션을 통해 자동 정리 조건 설정 가능
* MySQL, PostgreSQL과 동일한 방식으로 Record Manager 기능 구현

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-20 181628.png" alt=""><figcaption><p>WindyFlo SQLite Record Manager</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-20 181638.png" alt=""><figcaption><p>WindyFlo SQLite Record Manager Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                    | 설명                   | 필수 여부 |
| --------------------- | -------------------- | ----- |
| Additional Parameters | 저장 관련 상세 설정을 구성하는 영역 | 선택    |

#### Additional Parameters

| 항목           | 설명                                           | 필수 여부 |
| ------------ | -------------------------------------------- | ----- |
| Table Name   | 데이터를 저장할 테이블 이름 (기본값: `upsertion_records`)   | 선택    |
| Namespace    | 레코드를 그룹화하여 논리적으로 분리하기 위한 문자열                 | 선택    |
| Cleanup      | 기존 데이터 정리 방식. `None`, `full`, `partial` 중 선택 | 필수    |
| SourceId Key | 중복 판단 기준이 되는 필드명 (기본값: `source`)             | 선택    |

***

### 출력값 (Outputs)

| 출력 항목               | 설명                                         |
| ------------------- | ------------------------------------------ |
| SQLiteRecordManager | 구성된 SQLite 레코드 관리자 객체. 저장 및 업데이트 처리에 활용 가능 |

***

### 활용 예시

* 서버 없이 로컬 환경에서 **AI 결과 기록을 테스트하거나 임시 저장소로 활용**할 때
* 소규모 앱 또는 단일 사용자 워크플로우에서 **빠른 로깅 및 데이터 저장**이 필요할 때
* MySQL이나 PostgreSQL 도입 전 **로컬 환경에서 검증 및 파일 기반 저장**용도로 사용할 때
* LLM 응답 결과를 반복 저장하고, SourceId 기준으로 **중복 없이 관리하고자 할 때**

***

### 사용 팁

* SQLite는 파일 기반 DB이므로, 해당 워크플로우가 실행되는 환경의 **쓰기 권한**을 반드시 확인하세요.
* 동일 파이프라인 내 여러 Record Manager 노드를 사용할 경우, Namespace를 설정해 **데이터 분리를 명확히 관리**할 수 있습니다.
* Cleanup을 `partial`로 설정하면 기존 데이터와 SourceId 기준으로 병합 저장(upsert)됩니다.

***

### 주의사항

* 별도 Credential 입력이 없으므로, 워크플로우 실행 환경 내 SQLite 사용 가능 여부를 사전에 확인해야 합니다.
* 저장 파일의 경로 지정 및 파일 권한 설정이 필요할 수 있으며, 권한 부족 시 실행 오류 발생 가능
* 대용량 데이터 처리에는 부적합하므로, 장기 운영보다는 테스트/개발 목적에 적합
