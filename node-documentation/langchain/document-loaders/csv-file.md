# Csv File

CSV 파일 데이터를 업로드하고, 각 행(row)을 문서(Document) 형식으로 변환하는 로더 노드입니다. 전체 파일 또는 특정 컬럼만 추출하여 다양한 텍스트 기반 파이프라인에 활용할 수 있습니다.

***

#### 주요 기능

* 업로드된 CSV 파일을 각 행 단위로 Document 객체로 변환
* 특정 컬럼만 추출하여 텍스트 콘텐츠로 처리 가능
* Text Splitter 연결로 긴 텍스트 처리 가능
* 사용자 정의 메타데이터 추가 및 특정 키 제외 가능
* 파일 기반 FAQ, 보고서, 피드백, 분석 데이터 입력에 활용

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 133654.png" alt=""><figcaption><p>WindyFlo Csv File</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 133709.png" alt=""><figcaption><p>WindyFlo Csv File Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                       | 설명                            | 필수 여부 |
| ------------------------ | ----------------------------- | ----- |
| Text Splitter            | 긴 텍스트 분할 처리용 노드 연결            | 선택    |
| Csv File                 | 업로드할 CSV 파일 (로컬 업로드)          | 필수    |
| Single Column Extraction | 추출할 특정 컬럼명 (입력 시 해당 컬럼 값만 사용) | 선택    |

***

#### 파라미터 (Parameters)

| 항목                  | 설명                                        |
| ------------------- | ----------------------------------------- |
| Additional Metadata | 각 문서에 추가할 사용자 정의 메타데이터 항목                 |
| Omit Metadata Keys  | 제외할 metadata 키 목록 (예: `index, timestamp`) |

***

#### 출력값 (Outputs)

| 출력 항목    | 설명                                            |
| -------- | --------------------------------------------- |
| Document | 각 CSV 행을 pageContent + metadata로 구성한 문서 객체 배열 |
| Text     | 전체 행의 내용을 텍스트로 병합한 문자열 (선택 출력 형식)             |

***

#### 활용 예시

* 고객 피드백 CSV를 불러와 요약 및 감성 분석에 활용
* 세일즈 리드 목록에서 이름/내용만 추출해 이메일 자동화에 활용
* 설문 데이터 중 특정 질문 답변만 추출하여 Q\&A 생성
* 텍스트 중심의 내부 데이터셋을 LLM 학습 입력으로 활용
* 예: “content” 컬럼만 추출해 리뷰 분류 모델 입력에 활용
* 전체 행을 그대로 Document로 처리해 DB 기반 검색에 연동 가능
* 챗봇 응답 튜닝을 위한 답변 데이터 정리용

***

#### 사용 팁

* 컬럼명이 정확히 일치해야 Single Column Extraction이 정상 동작
* Text Splitter를 연결하면 각 행이 장문인 경우도 적절히 처리 가능
* `Omit Metadata Keys`를 설정하면 불필요한 컬럼 제거 가능
* CSV 파일 구조가 일정할수록 문서 처리 효율이 높아짐

***

#### 주의사항

* 빈 컬럼명 또는 비정형 구조의 CSV는 처리 오류 발생 가능
* 업로드된 파일은 노드 실행 시마다 다시 처리되므로 과도한 용량은 주의
* 컬럼명이 한글 또는 특수문자일 경우 일부 기능에 제한 발생 가능
* Single Column Extraction 입력 시 해당 컬럼이 존재하지 않으면 빈 문서 생성됨
