# SearchApi For Web Search

SearchApi For Web Search 노드는 지정된 검색어(Query)를 기반으로 외부 검색 API를 호출하여 검색 결과를 수집하고, 이를 문서 객체(Document)로 변환합니다. 최신 정보가 필요한 응답 생성이나 실시간 트렌드 기반 분석에 유용합니다.

***

### 주요 기능

* 검색어(Query)에 기반한 실시간 웹 검색 실행
* 결과를 pageContent와 metadata가 포함된 Document로 변환
* Custom Parameters를 통해 검색 API 세부 설정 가능
* 텍스트 분할 및 메타데이터 삽입 기능 제공

<figure><img src="../../../.gitbook/assets/image (70).png" alt=""><figcaption><p>WindyFlo SearchApi For Web Search</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (71).png" alt=""><figcaption><p>WindyFlo SearchApi For Web Search</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                   | 필수 여부 |
| ------------------ | ------------------------------------ | ----- |
| Connect Credential | SearchApi 인증 정보 (Credential에 등록)     | 필수    |
| Query              | 검색 키워드 또는 문장                         | 필수    |
| Text Splitter      | 수집된 텍스트를 분할하는 데 사용할 Text Splitter 노드 | 선택    |

***

### 파라미터 (Parameters)

| 항목                  | 설명                                    |
| ------------------- | ------------------------------------- |
| Custom Parameters   | 검색 API 호출 시 사용할 커스텀 쿼리 파라미터 (JSON 형식) |
| Additional Metadata | 결과 문서에 삽입할 사용자 정의 메타데이터               |
| Omit Metadata Keys  | 제거할 메타데이터 키 (쉼표로 구분 입력)               |

***

### 출력값 (Outputs)

| 출력 항목    | 설명                              |
| -------- | ------------------------------- |
| Document | 검색 결과를 기반으로 구성된 문서 객체 리스트       |
| Text     | 검색 결과의 pageContent를 병합한 텍스트 문자열 |

***

### 활용 예시

* 특정 주제의 실시간 정보나 뉴스 기사 검색 후 요약·정리
* 고객 질의에 대해 최신 정보를 기반으로 답변하는 RAG 파이프라인 구축
* 키워드 기반 마켓 트렌드 수집 후 벡터 저장소에 입력

***

### 사용 팁

* Query는 문장 형태로 입력할수록 더 정교한 검색 결과를 기대할 수 있음
* Custom Parameters에 정렬 방식, 응답 개수 등 세부 옵션 지정 가능
* Additional Metadata를 활용해 출처 정보(예: query, timestamp 등) 추가 가능

***

### 주의사항

* Credential 누락 시 API 인증 실패로 검색 결과를 가져올 수 없음
* 일부 API 제공자의 경우 응답 지연 또는 호출 제한(Rate Limit)이 발생할 수 있음
* 결과 콘텐츠가 간략하거나 중복된 경우에는 Document로 활용하기 어려울 수 있음
