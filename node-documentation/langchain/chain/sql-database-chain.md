# Sql Database Chain

W**Sql Database Chain**은 자연어 질문을 SQL 쿼리로 변환하고, 지정한 데이터베이스에서 실행하여 결과를 반환하는 체인입니다.\
PostgreSQL, MySQL, MSSQL, SQLite 등 다양한 RDB와 연동하여 사용자가 데이터베이스에 질의하고 결과를 확인할 수 있습니다.

***

### 주요 기능

* 자연어 입력을 SQL 쿼리로 변환하여 실행
* 쿼리 실행 결과를 LLM이 자연어 응답으로 요약
* SQLite 로컬 파일부터 원격 PostgreSQL 등 다양한 DB 지원
* 쿼리 대상 테이블 지정, 프롬프트 커스터마이징 기능 제공

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-09 174314.png" alt=""><figcaption><p>WindyFlo Sql Database Chain</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-09 174306 (1).png" alt=""><figcaption><p>WindyFlo Sql Database Chain Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                                 | 설명                                                    | 필수 여부                                                                                        |
| ---------------------------------- | ----------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| **Language Model**                 | SQL 쿼리 생성 및 결과 요약에 사용될 언어 모델 (예: GPT)                 | 필수                                                                                           |
| **Input Moderation**               | 유해 입력 필터링 기능                                          | 선택                                                                                           |
| **Database**                       | 연결할 데이터베이스 종류 (SQLite, PostgreSQL, MSSQL, MySQL 중 선택) | 필수                                                                                           |
| **Connection String or File Path** | DB 연결 경로 또는 SQLite 파일 경로                              | 필수                                                                                           |
| **Include Tables**                 | 포함할 테이블 목록 (쉼표로 구분)                                   | 선택                                                                                           |
| **Ignore Tables**                  | 제외할 테이블 목록 (쉼표로 구분)                                   | 선택                                                                                           |
| **Sample Table’s Rows Info**       | 테이블 구조 유추를 위한 샘플 데이터 개수                               | 선택 (기본값: 3)                                                                                  |
| **Top Keys**                       | 상위 키 개수 제한 (기본값: 10)                                  | 선택                                                                                           |
| **Custom Prompt**                  | 직접 작성한 SQL 생성 프롬프트                                    | <p>선택<br>(<code>{input}</code>, <code>{dialect}</code>, <code>{table_info}</code> 포함 필수)</p> |

***

### 출력값 (Outputs)

| 항목                   | 설명                        |
| -------------------- | ------------------------- |
| **SqlDatabaseChain** | 자연어 응답 형식으로 출력된 SQL 실행 결과 |

***

### 활용 예시

* 사내 데이터베이스에 질의하여 인사이트 도출\
  예: "지난달 신규 가입자 수 알려줘"
* 고객, 주문, 매출 관련 데이터 분석 자동화\
  예: "가장 많이 판매된 상품 5개는?"
* 비기술 직무 사용자를 위한 SQL 자동화 인터페이스 구축

***

### 사용 팁

* **SQLite 파일 경로**는 `.db` 파일 절대 경로로 설정해야 하며, 서버에 해당 파일이 업로드되어 있어야 합니다.
* 프롬프트 커스터마이징 시 `{input}`, `{dialect}`, `{table_info}` 변수를 반드시 포함해야 정상 동작합니다.
* Include/Ignore 설정으로 대상 테이블을 한정하면 불필요한 데이터 노출을 방지할 수 있습니다.
* 반환 결과가 길 경우 `Chain Tool`을 연결해 후처리할 수 있습니다.

***

### 주의사항

* SQL 인젝션 방지를 위해 신뢰된 사용자만 입력하게 하거나, moderation 기능을 켜는 것을 권장합니다.
* 데이터베이스 연결이 실패할 경우 전체 체인이 중단될 수 있으므로 연결 정보를 정확히 설정해야 합니다.
* MSSQL 및 MySQL 사용 시 드라이버 환경이 미리 설치되어 있어야 작동합니다.
* SQLite 외 DB는 반드시 연결 정보(`host`, `port`, `database`, `user`, `password`)를 포함한 connection string을 사용해야 합니다.

***

**Sql Database Chain**은 기술적 허들이 있는 SQL을 자연어로 접근 가능하게 해주는 강력한 노드입니다.\
비개발자도 데이터베이스에서 원하는 정보를 쉽게 추출하고 응답받을 수 있도록 지원합니다.
