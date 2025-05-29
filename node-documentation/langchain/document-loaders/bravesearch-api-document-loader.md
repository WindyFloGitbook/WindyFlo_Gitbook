# BraveSearch API Document Loader

Brave Search API를 통해 실시간 웹 검색 결과를 수집하고, 해당 결과를 문서(Document) 형식으로 변환하는 로더 노드입니다. 최신 정보를 기반으로 하는 AI 파이프라인이나 검색 기반 QA에 활용됩니다.

***

#### 주요 기능

* BraveSearch API를 이용해 쿼리 기반 실시간 웹 검색 수행
* 검색 결과를 pageContent + metadata 구조의 문서로 변환
* 추가 메타데이터 설정 및 특정 필드 제외 가능
* Text Splitter와 연동 시 장문 응답 처리 가능
* Chat 기반 응답 강화나 최신 정보 보강 목적에 적합

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 133042.png" alt=""><figcaption><p>WindyFlo BraveSearch API Document Loader</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 133030.png" alt=""><figcaption><p>WindyFlo BraveSearch API Document Loader Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                 | 설명                                       | 필수 여부 |
| ------------------ | ---------------------------------------- | ----- |
| Text Splitter      | 검색 결과 텍스트 분할 용도                          | 선택    |
| Connect Credential | BraveSearch API Key를 Credential에 등록 후 선택 | 필수    |
| Query              | 웹 검색에 사용할 키워드 또는 문장                      | 필수    |

***

#### 파라미터 (Parameters)

| 항목                  | 설명                                               |
| ------------------- | ------------------------------------------------ |
| Additional Metadata | 생성된 문서에 포함할 추가 메타데이터 항목                          |
| Omit Metadata Keys  | 제외할 메타데이터 키 목록 (쉼표 구분, 예: `source.url, snippet`) |

***

#### 출력값 (Outputs)

| 출력 항목    | 설명                                 |
| -------- | ---------------------------------- |
| Document | 검색 결과를 기반으로 생성된 Document 객체 배열     |
| Text     | 모든 문서를 하나의 텍스트로 연결한 문자열 (선택 출력 형식) |

***

#### 활용 예시

* 실시간 검색 결과를 기반으로 최신 동향 요약 또는 뉴스 콘텐츠 분석
* 쿼리 기반 웹 검색 결과를 AI 답변에 반영 (ex. “OpenAI GPT-5 출시일”)
* 빠르게 변화하는 산업 동향/이슈 추적 파이프라인 구성
* 기존 문서 외에 외부 검색 정보도 함께 학습/응답에 활용
* 경쟁사 트렌드 추적용 파이프라인 구축
* 실시간 검색 질의 기반 Context Injection
* 블로그/마케팅 콘텐츠 생성을 위한 최신 정보 활용

***

#### 사용 팁

* BraveSearch는 실시간 웹 검색이므로 쿼리는 구체적일수록 정확도 상승
* Text Splitter를 함께 연결하면 각 검색 결과 설명을 문단 단위로 분할 가능
* `Omit Metadata Keys`를 활용해 불필요한 필드를 제외하고 경량화된 문서 구성
* BraveSearch API Key는 사전 발급 후 Credential에 등록해야 선택 가능

***

#### 주의사항

* API 호출량이 많을 경우 BraveSearch 요금이 발생할 수 있음
* Query 입력값이 부정확할 경우 무의미한 결과가 반환될 수 있음
* BraveSearch API는 검색 정확도가 상황에 따라 달라질 수 있음
* Credential 누락 시 실행되지 않음
