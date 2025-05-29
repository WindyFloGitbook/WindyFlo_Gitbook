# Puppeteer Web Scraper

Puppeteer Web Scraper 노드는 Chromium 기반 브라우저 자동화를 통해 지정한 웹 페이지의 콘텐츠를 크롤링하여 문서 객체(Document)로 변환합니다. 렌더링이 필요한 복잡한 웹 페이지에서도 안정적으로 텍스트를 수집할 수 있어 다양한 실무 자동화 시나리오에 활용됩니다.

***

### 주요 기능

* JavaScript 기반 웹페이지를 포함한 콘텐츠를 정확하게 크롤링
* Web Crawl 옵션을 활용해 내부 링크까지 확장 수집 가능
* 특정 요소가 로딩될 때까지 대기 후 추출 가능
* 메타데이터 삽입 및 필터링 설정 가능

<figure><img src="../../../.gitbook/assets/image (21).png" alt=""><figcaption><p>WindyFlo Puppeteer Web Scraper</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (22).png" alt=""><figcaption><p>WindyFlo Puppeteer Web Scraper Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목            | 설명                                   | 필수 여부 |
| ------------- | ------------------------------------ | ----- |
| URL           | 크롤링할 웹 페이지의 주소                       | 필수    |
| Text Splitter | 수집된 텍스트를 분할하는 데 사용할 Text Splitter 노드 | 선택    |

***

### 파라미터 (Parameters)

| 항목                        | 설명                                          |
| ------------------------- | ------------------------------------------- |
| Get Relative Links Method | 내부 링크 탐색 방식 설정 (예: Web Crawl)               |
| Get Relative Links Limit  | 크롤링할 최대 내부 링크 수 (예: 10)                     |
| Wait Until                | 페이지 로딩 완료 조건 지정 (load, domcontentloaded 등)  |
| Wait for selector to load | 특정 DOM 셀렉터가 로드될 때까지 대기 (예: `.main`, `#app`) |
| Additional Metadata       | 크롤링된 문서에 삽입할 메타데이터 (JSON 형식)                |
| Omit Metadata Keys        | 제거할 메타데이터 키 목록 지정 (쉼표로 구분 입력)               |

***

### 출력값 (Outputs)

| 출력 항목    | 설명                             |
| -------- | ------------------------------ |
| Document | 추출된 텍스트 및 메타데이터를 포함한 문서 객체 리스트 |
| Text     | 모든 pageContent를 병합한 단일 문자열 텍스트 |

***

### 활용 예시

* 로그인 없이 접근 가능한 웹사이트의 블로그/뉴스 페이지 크롤링
* 프론트엔드 렌더링 기반 SaaS 웹사이트 콘텐츠를 수집해 요약
* 크롤링한 데이터를 벡터화하여 유사 콘텐츠 추천 모델에 활용

***

### 사용 팁

* `Wait for selector to load` 항목을 지정하면 비동기 콘텐츠도 안정적으로 수집 가능
* `Get Relative Links Limit`을 조절해 성능과 정확도 간 균형 조정
* Text Splitter를 활용하면 크롤링한 긴 텍스트도 효과적으로 분할 가능

***

### 주의사항

* 인증이 필요한 페이지는 Credential 기능 없이 접근 불가
* 자바스크립트 무한 렌더링 또는 비표준 구조 페이지는 처리 실패 가능성 있음
* 크롤링 속도가 느릴 수 있으며, 대량 처리 시 Rate Limit에 유의 필요
