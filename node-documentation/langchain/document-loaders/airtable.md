# Airtable

Airtable에서 지정한 테이블 데이터를 불러와 문서(Document) 형식으로 변환하는 로더 노드입니다. 사전 정의된 Base, Table, View 정보를 기반으로 원하는 레코드만 선택적으로 로딩할 수 있어 데이터 필터링에 유용합니다.

***

#### 주요 기능

* Airtable API와 연결하여 레코드 데이터를 문서로 변환
* View ID, 필드 포함 여부, 수량 제한 등 세부 필터링 가능
* Text Splitter를 통해 텍스트 기반 처리까지 연결 가능
* Additional Metadata 삽입으로 문서 후처리 용이
* API 호출 시 포함할 메타데이터 키 제외 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 132503.png" alt=""><figcaption><p>WindyFlo Airtable</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 132514 (1).png" alt=""><figcaption><p>WindyFlo Airtable Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                 | 설명                                  | 필수 여부 |
| ------------------ | ----------------------------------- | ----- |
| Text Splitter      | 긴 텍스트 분할을 위한 노드 연결                  | 선택    |
| Connect Credential | Airtable API 키를 Credential에 등록 후 선택 | 필수    |
| Base Id            | Airtable Base 식별자                   | 필수    |
| Table Id           | Airtable Table 식별자                  | 필수    |
| View Id            | Airtable View 식별자 (필터링 목적)          | 선택    |

***

#### 파라미터 (Parameters)

| 항목                  | 설명                                                 |
| ------------------- | -------------------------------------------------- |
| Include Only Fields | 지정한 필드만 로드 (쉼표로 구분된 필드 ID 또는 이름)                   |
| Return All          | 전체 레코드 반환 여부 (기본값: true)                           |
| Limit               | 반환 레코드 수 제한 (기본값: 100)                             |
| Additional Metadata | 각 문서에 추가할 메타데이터 항목                                 |
| Omit Metadata Keys  | 제외할 metadata 키 (예: `key1, key2.nestedKey`)         |
| Filter By Formula   | Airtable Formula를 이용한 조건 필터링 (예: `NOT([id] = "")`) |

***

#### 출력값 (Outputs)

| 출력 항목    | 설명                                                    |
| -------- | ----------------------------------------------------- |
| Document | Airtable 레코드를 pageContent + metadata 형태로 변환한 문서 객체 배열 |

***

#### 활용 예시

* Airtable로 운영 중인 콘텐츠 데이터베이스를 문서로 불러와 LLM 분석에 활용
* 특정 View로 필터링된 고객 피드백만 문서화하여 Q\&A 파이프라인에 적용
* 프로젝트 관리 테이블을 자동 문서화하여 보고서나 리포트 생성에 활용
* 템플릿 필드만 추출하여 FAQ 문서 자동 생성
* 수집 후 Vector Store에 바로 연결 가능
* 비개발자가 Airtable만 관리해도 콘텐츠 자동 연동 가능

***

#### 사용 팁

* `Return All` 옵션을 끄면 `Limit`이 적용됨 (대량 테이블 필터링 시 유용)
* `Filter By Formula`를 활용하면 Airtable의 조건식을 그대로 적용 가능
* 특정 필드만 로딩하려면 `Include Only Fields`에 필드명/ID를 정확히 기입
* Credential은 Airtable API Key를 미리 Credential에 등록 후 선택

***

#### 주의사항

* Base ID, Table ID는 정확히 복사하여 입력해야 연결 오류 방지
* View ID를 입력하지 않으면 기본 View 기준으로 로드됨
* 필드명이 아닌 필드 ID 입력 시 가독성 떨어질 수 있으므로 주의
* 필드 수 제한, API 속도 제한 등 Airtable 측 제약에 주의
