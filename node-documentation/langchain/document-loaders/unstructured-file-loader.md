# Unstructured File Loader

Unstructured File Loader 노드는 PDF, 이미지, DOCX 등 다양한 비정형 문서 파일을 업로드하고 Unstructured API를 통해 문서 텍스트를 추출하여 정형 데이터로 변환합니다. OCR, 페이지 분할, 텍스트 청킹 등 다양한 전처리 옵션을 제공하여 문서 분석 파이프라인의 전처리 단계에 적합합니다.

***

### 주요 기능

* PDF, 이미지, 워드 파일 등 다양한 비정형 문서 형식 처리
* Unstructured API와 연동하여 문서 내용 추출 및 구조화
* OCR 언어 설정, 청킹 전략 등 다양한 문서 처리 파라미터 제공
* 파일 내 메타데이터 필터링 및 추가 메타데이터 삽입 가능
* 결과를 문서 객체 배열(Document) 또는 텍스트(Text)로 출력 가능

<figure><img src="../../../.gitbook/assets/image (78).png" alt=""><figcaption><p>WindyFlo Unstructured File Loader</p></figcaption></figure>

<div><figure><img src="../../../.gitbook/assets/image (79).png" alt=""><figcaption><p>WindyFlo Unstructured File Loader Parameters</p></figcaption></figure> <figure><img src="../../../.gitbook/assets/image (80).png" alt=""><figcaption><p>WindyFlo Unstructured File Loader Parameters</p></figcaption></figure></div>

### 입력값 (Inputs)

| 항목                   | 설명                                             | 필수 여부 |
| -------------------- | ---------------------------------------------- | ----- |
| Connect Credential   | Unstructured API 사용을 위한 인증 정보 (Credential에 등록) | 필수    |
| Files Upload         | 업로드할 문서 파일 선택                                  | 필수    |
| Unstructured API URL | Unstructured 엔드포인트 URL                         | 필수    |

***

### 파라미터 (Parameters)

| 항목                     | 설명                                      |
| ---------------------- | --------------------------------------- |
| Strategy               | 문서 처리 전략 선택 (예: Auto, fast, hi\_res 등)  |
| Encoding               | 텍스트 인코딩 방식 (기본값: utf-8)                 |
| Skip Infer Table Types | 표 추론을 건너뛸 파일 형식 지정 (기본값: jpg, pdf, png) |
| Hi-Res Model Name      | 고해상도 모델 지정 시 사용 (옵션)                    |
| Chunking Strategy      | 문서 청킹 기준 설정 (예: By Title, By Element 등) |
| OCR Languages          | OCR 적용 시 언어 설정                          |
| Source ID Key          | 문서 소스 식별자 키 (기본값: source)               |
| Coordinates            | 각 청크에 위치 정보 포함 여부 (ON/OFF)              |
| Include Page Breaks    | 페이지 구분자 삽입 여부 (ON/OFF)                  |
| XML Keep Tags          | XML 태그 유지 여부 (ON/OFF)                   |
| Multi-Page Sections    | 여러 페이지를 하나의 섹션으로 병합 여부 (ON/OFF)         |
| Combine Under N Chars  | 지정한 글자 수 미만 청크 병합                       |
| New After N Chars      | 지정한 글자 수 초과 시 청크 분리                     |
| Max Characters         | 청크 최대 글자 수 (기본값: 500)                   |
| Additional Metadata    | key-value 형식으로 메타데이터 추가                 |
| Omit Metadata Keys     | 제거할 메타데이터 키 지정 (쉼표로 구분)                 |

***

### 출력값 (Outputs)

| 출력 항목    | 설명                                   |
| -------- | ------------------------------------ |
| Document | 각 청크별 메타데이터 및 내용이 포함된 문서 객체 배열       |
| Text     | 모든 청크의 pageContent를 하나의 문자열로 연결한 텍스트 |

***

### 활용 예시

* OCR 기반 문서(스캔본 PDF, 이미지 등)에서 텍스트를 추출하고 벡터화하기 전 전처리용으로 활용
* 다양한 문서 포맷을 통합하여 질의응답(RAG) 파이프라인의 소스로 구성
* 내부 보고서, 계약서 등을 자동 분할 및 메타데이터 필터링 후 LLM 입력으로 활용
* 청킹 전략을 조절하여 긴 문서를 요약하거나, 특정 기준(Title, Element)으로 문서 분리 가능

***

### 사용 팁

* **Chunking Strategy**를 상황에 따라 조정하세요. 긴 문서는 `By Element`, 구조화된 문서는 `By Title`이 효과적입니다.
* `Additional Metadata` 항목을 통해 문서 출처, 작성자 등의 정보를 추가할 수 있습니다.
* OCR이 필요한 경우 `OCR Languages` 설정을 통해 정확도를 높일 수 있습니다.
* 불필요한 메타데이터는 `Omit Metadata Keys`에 명시하여 정제된 출력 확보 가능

***

### 주의사항

* `Unstructured API URL`에 올바른 API 엔드포인트를 입력해야 정상 작동합니다.
* OCR, 청킹 등 고급 기능을 사용할수록 처리 속도가 느려질 수 있습니다.
* 입력 파일 용량이 크거나 OCR 설정이 활성화된 경우 API 사용량이 증가하므로 주의하세요.
* 출력 타입을 `Document`로 설정하지 않으면 일부 후속 노드에서 처리되지 않을 수 있습니다.
