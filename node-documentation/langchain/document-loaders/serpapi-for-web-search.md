# SerpApi For Web Search

SerpApi For Web Search 노드는 SerpAPI를 통해 Google 검색 결과를 수집하고 이를 문서 객체(Document)로 변환합니다. RAG 기반 응답, 트렌드 분석, 실시간 정보 확보가 필요한 워크플로우에 적합합니다.

***

### 주요 기능

* SerpAPI를 활용한 실시간 Google 검색 결과 수집
* 검색 결과를 Document 형식으로 반환하여 LLM 입력에 적합하게 구성
* Text Splitter와 연계하여 텍스트를 자동 분할 가능
* 메타데이터 삽입 및 불필요한 키 제거 지원

<figure><img src="../../../.gitbook/assets/image (72).png" alt=""><figcaption><p>WindyFlo SerpApi For Web Search</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (73).png" alt=""><figcaption><p>WindyFlo SerpApi For Web Search Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                   | 필수 여부 |
| ------------------ | ------------------------------------ | ----- |
| Connect Credential | SerpAPI 인증 정보 (Credential에 등록)       | 필수    |
| Query              | 검색할 키워드 또는 문장                        | 필수    |
| Text Splitter      | 수집된 텍스트를 분할하는 데 사용할 Text Splitter 노드 | 선택    |

***

### 파라미터 (Parameters)

| 항목                  | 설명                                          |
| ------------------- | ------------------------------------------- |
| Additional Metadata | 출력 문서에 삽입할 추가 메타데이터 (예: query, timestamp 등) |
| Omit Metadata Keys  | 제거할 메타데이터 키 지정 (쉼표로 구분 입력)                  |

***

### 출력값 (Outputs)

| 출력 항목    | 설명                              |
| -------- | ------------------------------- |
| Document | 검색 결과를 기반으로 생성된 문서 객체 리스트       |
| Text     | 모든 pageContent를 병합한 하나의 텍스트 문자열 |

***

### 활용 예시

* 검색 기반 질의응답 시스템에서 최신 정보 검색 후 LLM에 입력
* 특정 키워드에 대한 실시간 시장 동향 파악 및 콘텐츠 생성
* SEO 키워드 관련 Google 상위 문서 분석 및 RAG 파이프라인 구성

***

### 사용 팁

* SerpAPI 자체 기능으로 뉴스, 쇼핑, 이미지 등 검색 유형 분류가 가능하므로, 필요 시 API 쿼리 구성 시 활용
* Text Splitter를 함께 설정하면 긴 결과 응답을 안정적으로 처리 가능
* Additional Metadata를 활용하면 검색어 또는 응답 시간 등 출처를 추적 가능

***

### 주의사항

* SerpAPI 키가 없으면 실행되지 않으며, 무료 계정은 일일 제한이 존재함
* 검색 결과가 Google의 정책에 따라 필터링될 수 있으며, 일부 정보는 누락될 수 있음
* 반복 실행 시 동일 검색어에 대해 다른 결과가 나올 수 있음 (실시간성 고려)
