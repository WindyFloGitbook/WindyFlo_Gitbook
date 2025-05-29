# FireCrawl

웹 페이지 또는 다수의 하위 페이지를 크롤링하여 텍스트 콘텐츠를 문서 형식으로 추출하는 노드입니다. Flowise와 연동되는 FireCrawl API를 활용하며, 크롤링 범위와 필터 조건을 자유롭게 설정할 수 있습니다.

***

#### 주요 기능

* 지정된 URL의 콘텐츠를 HTML 구조 기반으로 크롤링 또는 스크래핑
* 서브페이지까지 포함해 전체 구조를 수집하거나 단일 페이지만 수집 가능
* 크롤링된 콘텐츠를 Document 또는 Text 형식으로 출력
* 이미지 ALT 텍스트 생성, 본문 필터링 등 고급 옵션 제공
* Text Splitter와 연계 시 대용량 페이지도 안정적으로 처리 가능

<figure><img src="../../../.gitbook/assets/image (52).png" alt=""><figcaption><p>WindyFlo FireCrawl</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (53).png" alt=""><figcaption><p>WindyFlo FireCrawl Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목            | 설명                                         | 필수 여부 |
| ------------- | ------------------------------------------ | ----- |
| Text Splitter | 장문 콘텐츠를 분할 처리할 노드 연결                       | 선택    |
| FireCrawl API | FireCrawl 서비스의 API 키 (Credential에 등록 후 선택) | 필수    |
| URLs          | 크롤링 대상 URL 목록 (쉼표로 구분)                     | 필수    |
| Crawler type  | 크롤링 방식 선택 (Crawl or Scrape)                | 필수    |

**Crawler type 옵션**:

* **Crawl**: 입력된 URL과 그 하위 모든 링크 페이지를 순차적으로 크롤링
* **Scrape**: 지정된 URL의 단일 콘텐츠만 추출

***

#### 파라미터 (Parameters)

| 항목                      | 설명                                         |
| ----------------------- | ------------------------------------------ |
| Max Crawl Pages         | 최대 크롤링 페이지 수 제한 (예: 10, 100)               |
| Generate Image Alt Text | 이미지의 대체 텍스트 생성 여부 (기본값: 비활성)               |
| Return Only URLs        | URL만 결과로 반환할지 여부 (문서 미생성, 기본값: false)      |
| Only Main Content       | 헤더/푸터 제거 및 본문 중심 콘텐츠만 추출할지 여부 (기본값: false) |

***

#### 출력값 (Outputs)

| 출력 항목    | 설명                               |
| -------- | -------------------------------- |
| Document | 페이지별 콘텐츠와 metadata가 포함된 문서 객체 배열 |
| Text     | 모든 페이지의 텍스트를 하나로 병합한 문자열         |

***

#### 활용 예시

* 기업 공식 사이트를 RAG 파이프라인에 입력해 질의응답 구현
* 고객지원 페이지 내용을 요약하거나 FAQ 문서로 재생성
* 기술 문서 사이트 전체를 수집해 내부 검색 시스템 구축
* 블로그, 뉴스 페이지 등의 콘텐츠를 수집해 카테고리 분류 및 태깅
* 고객센터 하위 페이지 전체 수집 후 요약 챗봇 구성
* 제품 소개 페이지 텍스트 추출 후 AI 기반 마케팅 카피 생성
* 기술 블로그 전체를 학습 데이터로 전처리
* 크롤링한 페이지 내 텍스트를 요약해 인사이트 리포트 자동 생성

***

#### 사용 팁

* **Crawl**은 전체 링크를 탐색하므로 최대 페이지 수를 제한하는 것이 좋음
* 콘텐츠에 광고/푸터가 많을 경우 **Only Main Content** 옵션을 활성화
* 여러 개의 URL을 동시에 처리할 경우 쉼표(,)로 구분
* ALT 텍스트가 중요한 경우 **Generate Image Alt Text** 옵션 활용

***

#### 주의사항

* FireCrawl API 키가 누락되거나 유효하지 않으면 실행되지 않음
* 과도한 크롤링은 속도 저하 및 요청 제한에 걸릴 수 있음
* **Return Only URLs** 옵션을 활성화하면 콘텐츠가 아닌 링크만 반환됨
* 일부 사이트는 크롤링 차단 정책으로 인해 실패할 수 있음
