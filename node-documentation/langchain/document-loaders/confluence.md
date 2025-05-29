# Confluence

Atlassian Confluence에서 특정 Space의 콘텐츠를 불러와 문서(Document) 형식으로 변환하는 로더 노드입니다. 팀 위키, 정책 문서, 기술 매뉴얼 등 다양한 협업 지식을 LLM 기반 파이프라인에서 재활용할 수 있습니다.

***

#### 주요 기능

* Confluence API를 통해 지정한 Space의 페이지 데이터를 불러옴
* Text Splitter와 연동하여 장문 페이지도 처리 가능
* 추가 메타데이터 설정 및 특정 필드 제외 기능 제공
* 실시간 문서 업데이트에 따른 파이프라인 자동화 가능
* SaaS 기반 협업 지식을 AI 활용으로 확장 가능

<figure><img src="../../../.gitbook/assets/image (44).png" alt=""><figcaption><p>WindyFlo Confluence</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 133456.png" alt=""><figcaption><p>WindyFlo Confluence Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                 | 설명                                                              | 필수 여부 |
| ------------------ | --------------------------------------------------------------- | ----- |
| Text Splitter      | 페이지 내용을 문단 단위로 분할                                               | 선택    |
| Connect Credential | Confluence API 토큰을 Credential에 등록 후 선택                          | 필수    |
| Base URL           | Confluence 사이트 기본 주소 (예: https://yourdomain.atlassian.net/wiki) | 필수    |
| Space Key          | 크롤링 대상 Space 식별자                                                | 필수    |
| Limit              | 불러올 페이지 수 제한 (예: 50)                                            | 선택    |

***

#### 파라미터 (Parameters)

| 항목                  | 설명                                             |
| ------------------- | ---------------------------------------------- |
| Additional Metadata | 문서에 포함할 사용자 정의 메타데이터 항목                        |
| Omit Metadata Keys  | 제외할 metadata 키 목록 (예: `version, _links.webui`) |

***

#### 출력값 (Outputs)

| 출력 항목    | 설명                                                  |
| -------- | --------------------------------------------------- |
| Document | 페이지 내용을 포함한 Document 객체 배열 (pageContent + metadata) |
| Text     | 모든 문서 내용을 하나의 텍스트로 병합한 문자열                          |

***

#### 활용 예시

* 사내 정책 문서, 개발 문서 등을 자동으로 문서화하여 QA 파이프라인에 연동
* Confluence에 정리된 기술 문서 기반 FAQ 생성
* Space Key 별로 분리된 프로젝트 문서를 각각 분석하거나 요약
* 사내 지식 기반 시스템을 생성해 검색 및 응답 시스템에 활용
* 여러 Space를 노드별로 나눠 프로젝트별 파이프라인 구성
* Text Splitter 연결 시 문단 단위로 처리하여 검색 최적화
* RAG 파이프라인의 Knowledge Base로 직접 활용 가능

***

#### 사용 팁

* `Limit` 값을 적절히 설정하여 과도한 페이지 수 불러오는 것을 방지
* Base URL은 `/wiki`까지 포함된 전체 주소를 입력해야 정상 작동
* API 토큰은 개인이 아닌 앱 단위로 발급 받아 Credential에 등록
* Text Splitter를 함께 사용하면 페이지 분할 처리에 용이

***

#### 주의사항

* Space Key는 정확한 값 입력 필수 (오타 시 데이터 불러오기 실패)
* API 호출량이 많은 경우 Atlassian API 속도 제한 발생 가능
* 페이지 내 이미지, 첨부파일 등은 크롤링 대상에 포함되지 않음
* Credential 누락 또는 Base URL 오입력 시 인증 실패 발생
