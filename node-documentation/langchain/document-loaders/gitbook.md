# GitBook

GitBook 노드는 지정한 GitBook 문서의 웹 경로를 입력하면 해당 페이지의 콘텐츠를 자동으로 불러와 문서 데이터로 변환합니다. 문서 기반 RAG 파이프라인 구축 시, 최신 온라인 매뉴얼이나 기술 문서를 불러오는 데 적합합니다.

***

#### 주요 기능

* GitBook 기반 웹 문서의 내용을 자동 수집하여 Document 형식으로 출력
* 단일 페이지 또는 전체 하위 경로 페이지까지 로딩 가능
* 불필요한 메타데이터는 제외하고 필요한 정보만 필터링 가능
* 추가 메타데이터를 직접 삽입하여 문서에 태그 부여 가능

<figure><img src="../../../.gitbook/assets/image (56).png" alt=""><figcaption><p>WindyFlo GitBook</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (57).png" alt=""><figcaption><p>WindyFlo GitBook Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                    | 설명                                                       | 필수 여부 |
| --------------------- | -------------------------------------------------------- | ----- |
| Web Path              | 불러올 GitBook 문서의 전체 URL (예: https://docs.gitbook.com/...) | 필수    |
| Should Load All Paths | 하위 경로까지 포함해 전체 문서를 불러올지 여부 (기본값: false)                  | 선택    |
| Text Splitter         | 불러온 문서의 텍스트를 분할하는 데 사용할 Text Splitter 노드                 | 선택    |

***

#### 파라미터 (Parameters)

| 항목                  | 설명                                      |
| ------------------- | --------------------------------------- |
| Additional Metadata | 로딩된 문서에 수동으로 삽입할 추가 메타데이터 (JSON 형식)     |
| Omit Metadata Keys  | 제외할 메타데이터 키 목록 (쉼표 구분, 예: `key1, key2`) |

***

#### 출력값 (Outputs)

| 출력 항목    | 설명                                          |
| -------- | ------------------------------------------- |
| Document | 수집된 GitBook 페이지 내용을 포함한 문서 객체 리스트           |
| Text     | 수집된 GitBook 페이지 내용을 포함한 문서를 Text 형태로 출력합니다. |

***

#### 활용 예시

* 최신 GitBook 기반 SaaS 제품 문서를 자동 수집하여 RAG 응답 기반으로 활용
* 특정 기능 문서만 필터링하여 고객 응대 챗봇의 응답 근거로 사용
* 팀 내 기술 문서를 검색 가능한 벡터 DB로 변환하는 워크플로우에 활용

***

#### 사용 팁

* `Should Load All Paths`를 활성화하면 메뉴 구조 전체를 한 번에 수집 가능하지만, 로딩 시간과 비용이 증가할 수 있습니다
* `Omit Metadata Keys`를 활용해 `title`, `breadcrumbs` 등 불필요한 정보는 미리 필터링하면 후처리 부담이 줄어듭니다
* Text Splitter 노드를 연결하면 대용량 문서를 자동으로 분할하여 벡터화에 최적화할 수 있습니다

***

#### 주의사항

* 대상 GitBook 문서가 로그인 필요하거나 접근 제한이 있는 경우 로딩되지 않습니다
* 불러온 콘텐츠가 HTML 기반으로 변환되므로, 원본 스타일이 일부 손실될 수 있습니다
* 잘못된 URL을 입력할 경우 오류 없이 빈 결과가 출력될 수 있으므로 반드시 사전 검증해야 합니다
