# File Loader

다양한 포맷의 로컬 파일을 업로드하여 문서 객체로 변환하는 범용 로더 노드입니다. PDF, JSONL, 텍스트 등 파일 기반 데이터를 AI 파이프라인에서 즉시 활용할 수 있습니다.

***

#### 주요 기능

* 다양한 파일 포맷(PDF, JSONL, TXT 등)을 지원하는 범용 파일 로더
* PDF는 페이지 단위 또는 파일 전체 단위로 문서화 가능
* JSONL 파일은 특정 키만 추출하여 문서 구성 가능
* Text Splitter 연동으로 대용량 파일 처리 가능
* 사용자 정의 메타데이터 추가 및 필요 없는 키 필터링 기능 포함

<figure><img src="../../../.gitbook/assets/image (50).png" alt=""><figcaption><p>WindyFlo File Loader</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (51).png" alt=""><figcaption><p>WindyFlo File Loader Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목            | 설명                          | 필수 여부 |
| ------------- | --------------------------- | ----- |
| Text Splitter | 장문 텍스트를 분할 처리할 노드           | 선택    |
| File          | 업로드할 파일 (PDF, JSONL, TXT 등) | 필수    |

***

#### 파라미터 (Parameters)

| 항목                       | 설명                                                                                                                                        |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Pdf Usage                | <p>PDF 분할 방식 설정 (기본값: One document per page)<br>- One document per page: 페이지별로 개별 문서 생성<br>- One document per file: 전체 파일을 하나의 문서로 처리</p> |
| JSONL Pointer Extraction | JSONL 파일 내 추출 대상 키 지정 (예: `content`, `text`)                                                                                              |
| Additional Metadata      | 각 문서에 추가할 사용자 정의 메타데이터 입력                                                                                                                 |
| Omit Metadata Keys       | 출력 문서에서 제외할 metadata 키 목록 (쉼표 구분)                                                                                                         |

***

#### 출력값 (Outputs)

| 출력 항목    | 설명                                       |
| -------- | ---------------------------------------- |
| Document | 추출된 pageContent 및 metadata를 포함한 문서 객체 배열 |
| Text     | 모든 문서를 텍스트로 병합한 문자열 (선택 출력 형식)           |

***

#### 활용 예시

* PDF 백서/매뉴얼 파일을 AI 요약 파이프라인에 입력
* JSONL 형식의 코퍼스를 특정 필드만 추출해 LLM 학습에 사용
* 내부 저장소의 TXT 파일을 문서로 변환해 검색 시스템에 등록
* CSV/Excel이 아닌 구조화되지 않은 파일도 RAG에 활용
* 전사 정책 PDF를 페이지 단위로 요약
* JSONL 뉴스 코퍼스에서 `title + content`만 추출해 활용
* 법률 문서 PDF를 조건 검색형 AI 응답 시스템에 적용

***

#### 사용 팁

* PDF는 페이지 수가 많을 경우 Text Splitter를 연결해 병렬 처리 추천
* JSONL 파일 사용 시, pointer 키 경로를 정확히 입력해야 함
* 출력 형식을 `Document`로 설정하면 metadata 활용이 가능
* 동일 포맷의 파일 여러 개를 병합하려면 Store 노드와 조합 활용 가능

***

#### 주의사항

* 지원하지 않는 포맷(ex. `.doc`, `.xls`) 업로드 시 오류 발생
* JSONL 파일은 줄 단위 JSON 객체여야 하며, 포맷 오류 시 처리 실패
* PDF 분할 설정을 `One document per page`로 하면 문서 수가 크게 증가할 수 있음
* pointer 키 미입력 시 JSONL에서는 텍스트가 비어 있을 수 있음
