# Playwright Web Scraper

Playwright Web Scraper 노드는 동적 웹 페이지에서 데이터를 직접 크롤링하여 문서 객체(Document)로 변환합니다. JavaScript 기반 콘텐츠를 포함한 페이지에서도 안정적인 데이터 수집이 가능하며, 크롤링된 데이터는 RAG나 요약 등 다양한 AI 파이프라인에 활용할 수 있습니다.

***

### 주요 기능

* 지정된 URL의 웹 페이지에서 콘텐츠를 실시간으로 크롤링
* Web Crawl 기능을 통해 내부 링크도 함께 탐색 가능
* DOM 요소 로딩 완료 후 텍스트를 추출하여 정확도 향상
* 메타데이터 필터링, 커스텀 삽입 가능

<figure><img src="../../../.gitbook/assets/image (41).png" alt=""><figcaption><p>WindyFlo Playwright Web Scraper</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (42).png" alt=""><figcaption><p>WindyFlo Playwright Web Scraper Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목            | 설명                                    | 필수 여부 |
| ------------- | ------------------------------------- | ----- |
| URL           | 크롤링 대상 웹 페이지의 주소                      | 필수    |
| Text Splitter | 크롤링된 텍스트를 분할하는 데 사용할 Text Splitter 노드 | 선택    |

***

### 파라미터 (Parameters)

| 항목                        | 설명                                           |
| ------------------------- | -------------------------------------------- |
| Get Relative Links Method | 내부 링크 탐색 방식 (None, Web Crawl 등)              |
| Get Relative Links Limit  | 내부 링크 탐색 시 수집할 최대 링크 수 (기본값 예: 10)           |
| Wait Until                | 페이지 로딩 완료 조건 (load, domcontentloaded 등)      |
| Wait for selector to load | 지정된 셀렉터가 로드될 때까지 대기 (예: `.main`, `#content`) |
| Additional Metadata       | 수집된 문서에 삽입할 메타데이터 (예: { "source": "web" })   |
| Omit Metadata Keys        | 문서에서 제외할 메타데이터 키 목록                          |

***

### 출력값 (Outputs)

| 출력 항목    | 설명                              |
| -------- | ------------------------------- |
| Document | 크롤링된 페이지 내용을 기반으로 생성된 문서 객체 리스트 |
| Text     | 크롤링된 전체 텍스트를 하나의 문자열로 병합한 값     |

***

### 활용 예시

* 동적 웹사이트(React, Vue 등)의 기술 문서 페이지를 실시간 수집하여 RAG 응답 품질 향상
* 마케팅, 제품 소개 페이지의 텍스트를 수집하여 요약 및 인사이트 추출
* 고객사 웹사이트 데이터를 벡터화하여 경쟁사 비교나 트렌드 분석에 활용

***

### 사용 팁

* `Wait for selector to load`를 활용하면 비동기 콘텐츠까지 안정적으로 수집 가능
* Web Crawl 사용 시 링크 수가 많으면 처리 시간이 급증하므로 `Limit` 설정 필수
* SPA 또는 JavaScript 기반 웹사이트는 Playwright로 처리하는 것이 가장 안정적임

***

### 주의사항

* 로그인/인증이 필요한 웹사이트는 정상적으로 크롤링되지 않을 수 있음
* 상태 변화(다른 URL 입력, 파라미터 변경 등)가 발생하면 내부 링크 재수집 발생
* 크롤링 대상 페이지 구조가 자주 변경되는 경우 오류 발생 가능성 있음
