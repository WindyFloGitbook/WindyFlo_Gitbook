# Docx File

Microsoft Word 형식의 `.docx` 파일을 업로드하고, 내용을 문서(Document) 형식으로 변환하는 로더 노드입니다. 사내 문서, 보고서, 회의록 등의 정보를 파이프라인에 바로 연결할 수 있습니다.

***

#### 주요 기능

* .docx 형식 문서를 텍스트 기반 문서로 자동 변환
* 각 문서를 pageContent + metadata 형태로 구성
* Text Splitter와 연결해 장문 문서도 처리 가능
* 필요 시 사용자 메타데이터 추가 및 불필요한 키 제거 가능
* 출력 형식을 선택하여 유연한 파이프라인 구성 가능

<figure><img src="../../../.gitbook/assets/image (46).png" alt=""><figcaption><p>WindyFlo Docx File</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 142341.png" alt=""><figcaption><p>WindyFlo Docx File Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목            | 설명                      | 필수 여부 |
| ------------- | ----------------------- | ----- |
| Text Splitter | 장문 텍스트 분할 처리용 노드 연결     | 선택    |
| Docx File     | 업로드할 Word (.docx) 문서 파일 | 필수    |

***

#### 파라미터 (Parameters)

| 항목                  | 설명                                              |
| ------------------- | ----------------------------------------------- |
| Additional Metadata | 문서에 추가할 사용자 정의 메타데이터 (예: 문서 유형, 출처 등)           |
| Omit Metadata Keys  | 제외할 metadata 키 목록 (쉼표 구분, 예: `author, version`) |

***

#### 출력값 (Outputs)

| 출력 항목    | 설명                                  |
| -------- | ----------------------------------- |
| Document | pageContent와 metadata를 포함한 문서 객체 배열 |
| Text     | 모든 문서 내용을 하나로 연결한 문자열 (선택 출력 형식)    |

***

#### 활용 예시

* 회의록이나 프로젝트 보고서 파일을 불러와 요약 파이프라인에 연결
* 내부 정책 문서를 문서화하여 LLM 기반 QA에 활용
* HR 문서를 자동 추출하여 직원 응답 챗봇에 활용
* 사내 배포 자료를 벡터 DB에 등록해 검색 기반 응답 구성
* 사내 Word 문서의 일괄 처리 자동화
* 문서 유형별 메타데이터 태깅 후 분류
* 법률 문서나 계약서 등도 문장 단위로 분할 가능

***

#### 사용 팁

* `.docx` 파일만 지원되며 `.doc` 또는 기타 포맷은 비호환
* 문서가 길 경우 반드시 Text Splitter와 함께 사용하는 것이 권장됨
* Additional Metadata를 활용하면 문서 출처 관리에 유리
* 파일 업로드 이후 별도 저장 필요 없이 즉시 파이프라인 활용 가능

***

#### 주의사항

* 한글 파일 `.hwp`, PDF 등은 지원되지 않음
* 잘못된 형식의 파일 업로드 시 오류 발생
* 다수 문서가 포함된 `.docx` 파일은 각 섹션 단위로 분할되지 않음
* 메타데이터 필드명이 중복되거나 잘못 지정되면 후속 노드 오류 발생 가능
