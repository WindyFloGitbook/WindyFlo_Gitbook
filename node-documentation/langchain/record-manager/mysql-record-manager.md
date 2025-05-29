# MySQL Record Manager

MySQL 데이터베이스에 기록을 저장하거나 갱신하는 작업을 관리하기 위한 노드입니다. LLM의 응답이나 워크플로우 결과를 구조화된 형태로 MySQL에 자동 저장할 수 있으며, 기존 데이터를 식별 기준에 따라 덮어쓰기(upsert)하거나 새로운 레코드로 추가하는 기능을 지원합니다.

***

### 주요 기능

* MySQL 데이터베이스에 연결하여 **레코드 저장 및 업데이트(upsert)** 기능 제공
* `Namespace`, `SourceId Key` 등 식별자 기준에 따른 **정교한 기록 관리**
* 자동 테이블 생성 및 관리(기본 테이블명: `upsertion_records`)
* `Cleanup` 옵션을 통해 기록 정리 조건 설정 가능
* 다양한 LLM 결과나 사용자 입력 데이터를 DB에 저장하는 워크플로우에 활용 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-20 181351.png" alt=""><figcaption><p>WindyFlo MySQL Record Manager</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-20 181402.png" alt=""><figcaption><p>WindyFlo MySQL Record Manager Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                    | 필수 여부 |
| ------------------ | ------------------------------------- | ----- |
| Connect Credential | MySQL 접속 정보를 담은 Credential에 등록된 항목 선택 | 필수    |
| Host               | MySQL 서버 주소 또는 도메인                    | 필수    |
| Database           | 기록을 저장할 대상 데이터베이스 이름                  | 필수    |
| Port               | 접속 포트 번호 (기본값: 3306)                  | 선택    |

#### Additional Parameters

| 항목           | 설명                                              | 필수 여부 |
| ------------ | ----------------------------------------------- | ----- |
| Table Name   | 데이터를 저장할 테이블 이름 (기본값: `upsertion_records`)      | 선택    |
| Namespace    | 레코드를 그룹화할 논리적 구분값. 복수 워크플로우 구분 시 활용             | 선택    |
| Cleanup      | 기존 레코드 정리 기준. `None`, `full`, `partial` 등 선택 가능 | 필수    |
| SourceId Key | 중복 판단 기준이 되는 필드명. 기본값: `source`                 | 선택    |

***

### 출력값 (Outputs)

| 출력 항목              | 설명                                    |
| ------------------ | ------------------------------------- |
| MySQLRecordManager | 구성된 레코드 관리자 객체. 이후 워크플로우에서 저장 처리에 사용됨 |

***

### 활용 예시

* LLM 응답 결과를 자동 저장하고 싶을 때 (예: 상담 기록, 요약 결과 등)
* 반복되는 워크플로우 결과를 **식별 기준(SourceId Key)** 으로 관리하고 싶을 때
* DB 기반으로 **프롬프트 결과 추적** 및 리포트 작성 워크플로우에 활용할 때
* 복수 워크플로우를 **Namespace 기준으로 구분**하여 기록 관리하고자 할 때

***

### 사용 팁

* `Cleanup`을 `full`로 설정하면 이전 데이터 전체 삭제 후 저장되므로 백업이 필요할 수 있습니다.
* `SourceId Key`는 LLM 응답에 포함되는 고유 키를 지정하면 자동 upsert에 유리합니다.
* `Namespace`를 활용하면 같은 테이블 내에서도 프로젝트 단위로 데이터 분리 관리가 가능합니다.

***

### 주의사항

* `Connect Credential`은 사전에 WindyFlo의 Credential에 등록된 유효한 MySQL 정보여야 합니다.
* Host, Database, Port 정보 중 하나라도 누락되면 연결에 실패합니다.
* 테이블이 존재하지 않으면 자동 생성되지만, 구조 변경이 필요한 경우 수동 설정 필요
* Cleanup 설정이 적절하지 않으면 불필요한 데이터 중복 또는 손실 발생 가능성 있음
