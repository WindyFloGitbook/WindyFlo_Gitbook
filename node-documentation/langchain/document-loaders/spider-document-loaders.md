# Spider Document Loaders

Spider Document Loaders 노드는 지정된 웹 페이지 또는 동일 도메인의 다수 페이지를 스크래핑하여 문서 형태로 가져오는 웹 크롤링 전용 노드입니다. 단일 페이지 정보 수집부터 도메인 기반 크롤링까지 대응할 수 있어, RAG 기반 검색, 웹 정보 수집 자동화에 활용됩니다.

***

### 주요 기능

* 단일 페이지 또는 전체 도메인 크롤링 모드 지원 (`Scrape`, `Crawl`)
* 최대 페이지 수 제한(Limit) 및 세부 크롤링 조건 설정 가능
* 결과를 Document 객체로 반환하여 벡터 저장소 저장 및 LLM 입력에 적합
* 메타데이터 추가 및 필요 없는 필드 제외 설정 가능

<figure><img src="../../../.gitbook/assets/image (74).png" alt=""><figcaption><p>WindyFlo Spider Document Loaders</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (75).png" alt=""><figcaption><p>WindyFlo Spider Document Loaders Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목            | 설명                                             | 필수 여부 |
| ------------- | ---------------------------------------------- | ----- |
| Credential    | Spider API Key (Credential에 등록)                | 필수    |
| Mode          | 크롤링 방식 선택: `Scrape`(단일 페이지) 또는 `Crawl`(전체 도메인) | 필수    |
| Web Page URL  | 스크래핑 대상 웹 페이지 또는 시작 URL                        | 필수    |
| Limit         | 크롤링 시 최대 문서 수 (기본값: 25)                        | 필수    |
| Text Splitter | 텍스트 분할 방식 설정                                   | 선택    |

***

### 파라미터 (Parameters)

| 항목                    | 설명                                                  |
| --------------------- | --------------------------------------------------- |
| Additional Metadata   | 수집된 문서에 삽입할 사용자 정의 메타데이터                            |
| Additional Parameters | Spider API 호출 시 사용할 추가 파라미터 (예: 필터, CSS selector 등) |
| Omit Metadata Keys    | 메타데이터에서 제외할 키 (쉼표로 구분 입력)                           |

***

### 출력값 (Outputs)

| 출력 항목    | 설명                                     |
| -------- | -------------------------------------- |
| Document | 페이지에서 수집한 텍스트와 메타데이터가 포함된 Document 배열  |
| Text     | Document들의 pageContent를 병합한 단일 텍스트 문자열 |

***

### 활용 예시

* 특정 블로그나 제품 소개 페이지에서 다수의 콘텐츠 자동 수집
* 기업 뉴스룸이나 PR 아카이브에서 크롤링 후 요약 생성
* 자사 사이트 구조 점검 및 콘텐츠 분석 파이프라인 자동화

***

### 사용 팁

* `Mode`를 `Crawl`로 설정할 경우 도메인 내 하위 페이지 전체를 탐색하므로 `Limit` 값을 적절히 설정해야 성능 저하 방지 가능
* Additional Parameters에 CSS selector 또는 페이지 조건을 설정하면 노이즈 감소 가능
* Additional Metadata에 검색어, 실행 시각 등 삽입 시 디버깅 및 재사용에 유용

***

### 주의사항

* 크롤링 대상 사이트가 robots.txt 또는 anti-scraping 정책을 갖고 있는 경우 작동하지 않을 수 있음
* Spider API의 요금제에 따라 호출 횟수 제한이 발생할 수 있음
* 동일한 URL로 반복 호출 시 동일 결과가 수집되므로 중복 처리 고려 필요
