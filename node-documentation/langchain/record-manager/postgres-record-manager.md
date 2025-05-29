# Postgres Record Manager

PostgreSQL 데이터베이스에 AI 파이프라인 결과를 저장하고 관리할 수 있도록 구성된 노드입니다. 특정 테이블에 대한 자동 upsert 기능과 namespace 기반 분류, cleanup 설정을 통한 데이터 정리가 가능하여 반복 실행되는 자동화 워크플로우와 통합 활용에 적합합니다.

***

### 주요 기능

* PostgreSQL과 연동하여 **AI 처리 결과를 구조화된 형태로 저장 및 업데이트**
* Namespace, SourceId 기반으로 **워크플로우별 데이터 분리 및 중복 방지**
* Cleanup 옵션을 통한 데이터 정리 전략 적용 가능
* SSL 옵션 제공으로 보안 연결 지원
* 기본 테이블 자동 생성(`upsertion_records`) 또는 사용자 지정 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-20 181509.png" alt=""><figcaption><p>WindyFlo Postgres Record Manager</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-20 181515.png" alt=""><figcaption><p>WindyFlo Postgres Record Manager Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                         | 필수 여부 |
| ------------------ | ------------------------------------------ | ----- |
| Connect Credential | PostgreSQL 접속 정보를 담은 Credential에 등록된 항목 선택 | 필수    |
| Host               | PostgreSQL 서버 주소 또는 도메인                    | 필수    |
| Database           | 연결할 대상 데이터베이스 이름                           | 필수    |
| Port               | 접속 포트 번호 (기본값: 5432)                       | 선택    |

#### Additional Parameters

| 항목           | 설명                                              | 필수 여부 |
| ------------ | ----------------------------------------------- | ----- |
| SSL          | 보안 연결을 위한 SSL 사용 여부 (기본값: 비활성화)                 | 선택    |
| Table Name   | 데이터를 저장할 테이블 이름 (기본값: `upsertion_records`)      | 선택    |
| Namespace    | 레코드를 논리적으로 구분하는 키. 프로젝트 단위 구분 시 유용              | 선택    |
| Cleanup      | 기존 데이터 정리 방식. `None`, `full`, `partial` 등 설정 가능 | 필수    |
| SourceId Key | 중복 판단 기준이 되는 필드명. 기본값: `source`                 | 선택    |

***

### 출력값 (Outputs)

| 출력 항목                 | 설명                                              |
| --------------------- | ----------------------------------------------- |
| PostgresRecordManager | 구성된 PostgreSQL 레코드 관리자 객체. 워크플로우 내 저장 처리에 활용 가능 |

***

### 활용 예시

* 상담 내용, 요약 결과, 사용자의 입력 데이터 등을 **PostgreSQL에 자동 저장**
* 동일 SourceId 기준으로 **기존 데이터를 upsert(덮어쓰기)** 하여 중복 방지
* 프로젝트별로 Namespace를 나누어 **분리된 데이터 관리**
* LangChain 기반 응답 결과를 **SQL 기반 리포트 작성 시스템과 연동**

***

### 사용 팁

* `Namespace`를 지정하면 여러 워크플로우에서 동일 테이블을 공유하면서도 논리적 분리가 가능합니다.
* `Cleanup`을 `partial`로 설정하면 SourceId 기준으로 일부 레코드만 정리하여 유연한 업데이트가 가능합니다.
* 보안이 중요한 환경에서는 SSL 옵션을 활성화하여 데이터 전송 보호가 가능합니다.

***

### 주의사항

* `Connect Credential`은 WindyFlo의 Credential에 등록된 유효한 PostgreSQL 정보여야 하며, 필수 항목 누락 시 연결 오류 발생
* `Cleanup`을 `full`로 설정하면 지정된 namespace의 기존 레코드가 모두 삭제될 수 있으므로 주의 필요
* 테이블 생성 또는 필드 변경은 자동으로 이루어지지 않으므로 사전 DB 설계가 필요할 수 있음
* SSL 사용 시, 서버가 이를 지원해야 정상 연결 가능
