# Folder with Files

지정한 폴더 경로 내의 모든 문서를 불러와 하나의 파이프라인에서 처리할 수 있도록 도와주는 노드입니다. PDF, JSONL, 텍스트, Word 등 다양한 포맷의 파일을 동시에 로드할 수 있으며, 하위 폴더 포함 여부도 설정할 수 있습니다.

***

#### 주요 기능

* 폴더 내 다수의 파일을 한 번에 문서 형태로 로드
* 하위 폴더까지 포함할지 여부 설정 가능 (Recursive)
* 다양한 파일 포맷에 대한 자동 처리 (PDF, JSONL, TXT 등)
* PDF 및 JSONL 파일에 대한 세부 처리 옵션 지원
* 결과를 Document 배열 또는 병합된 Text 형태로 출력

<figure><img src="../../../.gitbook/assets/image (54).png" alt=""><figcaption><p>WindyFlo Folder with Files</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (55).png" alt=""><figcaption><p>WindyFlo Folder with Files Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목            | 설명                            | 필수 여부 |
| ------------- | ----------------------------- | ----- |
| Text Splitter | 텍스트 분할용 노드 연결 (선택적)           | 선택    |
| Folder Path   | 파일이 포함된 폴더 경로 (로컬 또는 서버 내 경로) | 필수    |
| Recursive     | 하위 폴더까지 포함 여부 (기본값: 비활성)      | 필수    |

***

#### 파라미터 (Parameters)

| 항목                       | 설명                                                                                                                                        |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Pdf Usage                | <p>PDF 파일 분할 방식 설정<br>- <strong>One document per page</strong>: 페이지 단위로 분리<br>- <strong>One document per file</strong>: 전체 파일을 하나로 처리</p> |
| JSONL Pointer Extraction | JSONL 파일 처리 시 특정 필드만 추출할 경우 포인터 경로 지정                                                                                                     |
| Additional Metadata      | 로드된 각 문서에 추가할 키-값 메타데이터 설정                                                                                                                |
| Omit Metadata Keys       | 불필요한 메타데이터 키를 생략 (예: `key1`, `nested.key2`)                                                                                               |

***

#### 출력값 (Outputs)

| 출력 항목    | 설명                                                      |
| -------- | ------------------------------------------------------- |
| Document | 각 파일 또는 페이지 단위로 나뉜 문서 객체 배열 (metadata + pageContent 포함) |
| Text     | 모든 파일의 pageContent를 연결한 하나의 문자열                         |

***

#### 활용 예시

* 여러 PDF 리포트를 일괄 로드하여 RAG 기반 질의응답 구성
* 교육 자료 폴더를 통째로 불러와 챗봇 학습에 활용
* JSONL 로그 파일에서 특정 필드만 추출 후 분석
* 특정 디렉토리 기반 문서 대시보드 구성

***

#### 사용 팁

* JSONL 파일의 경우 Pointer 경로를 정확히 지정하지 않으면 로드되지 않음
* PDF는 페이지 수가 많을 경우 **One document per page**로 설정하는 것이 효율적
* 여러 문서 포맷이 혼합된 폴더는 Text Splitter와 함께 사용하는 것이 안정적
* 폴더 경로에 한글이 포함된 경우 인코딩 이슈가 없는지 확인

***

#### 주의사항

* 폴더 내 비지원 포맷(.exe 등)은 자동으로 무시되며 오류가 발생하지 않음
* 너무 많은 파일을 한 번에 불러오면 처리 시간이 지연될 수 있음
* JSONL 파일 내 구조가 일정하지 않으면 Pointer 지정 시 오류 가능성 있음
* Text 출력 선택 시 metadata 정보는 모두 누락됨
