# Pdf File

Pdf File 노드는 업로드된 PDF 파일을 텍스트로 추출하여 문서 객체(Document)로 변환합니다. 보고서, 논문, 계약서 등 PDF 기반 정보를 AI 파이프라인에서 바로 활용할 수 있도록 지원합니다.

***

### 주요 기능

* PDF 파일 내 텍스트를 자동 추출하여 문서 객체로 변환
* 파일 전체 또는 페이지 단위로 문서를 나눠 처리 가능
* 메타데이터 삽입 및 불필요한 키 필터링 기능 제공
* Text Splitter와 연계해 긴 텍스트를 자동 분할 가능

<figure><img src="../../../.gitbook/assets/image (37).png" alt=""><figcaption><p>WindyFlo Pdf File</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (38).png" alt=""><figcaption><p>WindyFlo Pdf File Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목            | 설명                                                      | 필수 여부 |
| ------------- | ------------------------------------------------------- | ----- |
| Pdf File      | 업로드할 PDF 문서 파일 (.pdf)                                   | 필수    |
| Usage         | 추출 방식 선택: One document per page / One document per file | 필수    |
| Text Splitter | 추출된 텍스트를 분할하는 데 사용할 Text Splitter 노드                    | 선택    |

***

### 파라미터 (Parameters)

| 항목                  | 설명                                 |
| ------------------- | ---------------------------------- |
| Use Legacy Build    | 구버전 텍스트 추출 방식 사용 여부 (기본값: Off)     |
| Additional Metadata | 수동으로 삽입할 메타데이터 (예: source, type 등) |
| Omit Metadata Keys  | 결과에서 제외할 메타데이터 키 목록 (쉼표 구분 입력)     |

***

### 출력값 (Outputs)

| 출력 항목    | 설명                               |
| -------- | -------------------------------- |
| Document | 추출된 텍스트와 메타데이터를 포함한 문서 객체 리스트    |
| Text     | 전체 pageContent를 하나의 문자열로 병합한 텍스트 |

***

### 활용 예시

* 사내 정책 문서, 매뉴얼 PDF를 벡터 DB에 저장하여 질의 응답 기반 검색 구현
* 컨퍼런스 발표자료를 페이지 단위로 나누어 요약 및 분류 처리
* 외부기관 보고서나 백서를 분석하고 추론 기반 답변에 활용

***

### 사용 팁

* `Usage`를 “One document per page”로 설정하면 페이지별 분할 가능해 분석 유연성 증가
* OCR 기반 PDF는 Legacy Build 활성화 시 더 안정적인 추출 가능성 있음
* `Text Splitter`를 연결하면 페이지 단위보다 더 세밀한 텍스트 단위로 분할 가능

***

### 주의사항

* 스캔 기반 PDF(이미지)는 텍스트 추출이 불완전하거나 불가능할 수 있음
* 텍스트 양이 많을수록 처리 시간이 늘어나며, 성능 최적화를 위해 분할 사용 권장
* 텍스트 포맷이 무너지거나 줄바꿈 오류가 생길 수 있으므로 후처리 고려 필요
