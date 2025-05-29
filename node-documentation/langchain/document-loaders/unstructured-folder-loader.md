# Unstructured Folder Loader

Unstructured Folder Loader 노드는 폴더 단위로 비정형 문서 파일을 일괄 처리하여 Unstructured API를 통해 내용을 추출하고 구조화된 형태로 반환합니다. 문서 대량 업로드가 필요한 경우에 적합하며, OCR, 청킹 전략 등 다양한 파라미터 설정을 통해 문서 분석 전처리 작업을 효율화할 수 있습니다.

***

### 주요 기능

* 지정한 폴더 내 모든 문서를 일괄 업로드하여 처리
* Unstructured API와 연동된 자동 문서 분석 및 추출 기능 제공
* OCR 언어, 청킹 기준, 고해상도 모델 설정 등 다양한 옵션 제공
* 결과물을 JSON 기반의 문서 배열 혹은 연결된 텍스트로 출력
* 대량 문서 처리에 적합한 유연한 파라미터 구성 지원

<figure><img src="../../../.gitbook/assets/image (81).png" alt=""><figcaption><p>WindyFlo Unstructured Folder Loader</p></figcaption></figure>

<div><figure><img src="../../../.gitbook/assets/image (82).png" alt=""><figcaption><p>WindyFlo Unstructured Folder Loader Parameters</p></figcaption></figure> <figure><img src="../../../.gitbook/assets/image (83).png" alt=""><figcaption><p>WindyFlo Unstructured Folder Loader Parameters</p></figcaption></figure></div>

### 입력값 (Inputs)

| 항목                   | 설명                                             | 필수 여부 |
| -------------------- | ---------------------------------------------- | ----- |
| Connect Credential   | Unstructured API 사용을 위한 인증 정보 (Credential에 등록) | 필수    |
| Folder Path          | 처리할 문서들이 위치한 폴더 경로                             | 필수    |
| Unstructured API URL | Unstructured 엔드포인트 URL                         | 필수    |

***

### 파라미터 (Parameters)

| 항목                     | 설명                                      |
| ---------------------- | --------------------------------------- |
| Strategy               | 문서 처리 전략 선택 (예: Auto, fast, hi\_res 등)  |
| Encoding               | 텍스트 인코딩 방식 (기본값: utf-8)                 |
| Skip Infer Table Types | 표 추론을 제외할 파일 유형 설정 (예: jpg, pdf, png)   |
| Hi-Res Model Name      | 고해상도 모델 이름 지정 (예: detectron2\_onnx)     |
| Chunking Strategy      | 문서 청킹 기준 설정 (예: By Title, By Element 등) |
| OCR Languages          | OCR 적용 시 사용 언어                          |
| Source ID Key          | 문서 식별용 메타데이터 키 (기본값: source)            |
| Coordinates            | 문서 청크 위치 정보 포함 여부 (ON/OFF)              |
| Include Page Breaks    | 페이지 구분 삽입 여부 (ON/OFF)                   |
| XML Keep Tags          | XML 태그 유지 여부 (ON/OFF)                   |
| Multi-Page Sections    | 여러 페이지 병합 여부 (ON/OFF)                   |
| Combine Under N Chars  | 지정 글자 수 미만의 청크 병합 기준                    |
| New After N Chars      | 지정 글자 수 초과 시 청크 분리 기준                   |
| Max Characters         | 청크 최대 글자 수 (기본값: 500)                   |
| Additional Metadata    | key-value 형식의 추가 메타데이터 삽입               |
| Omit Metadata Keys     | 제거할 메타데이터 키 목록 설정 (쉼표 구분)               |

***

### 출력값 (Outputs)

| 출력 항목    | 설명                                   |
| -------- | ------------------------------------ |
| Document | 각 문서 및 청크의 메타데이터와 내용을 포함한 객체 배열      |
| Text     | 모든 문서의 pageContent를 하나의 문자열로 연결한 텍스트 |

***

### 활용 예시

* 사내 문서 저장소 폴더 전체를 AI 검색 시스템 학습 데이터로 구성할 때
* 계약서, 보고서 등 구조가 유사한 문서를 폴더 단위로 청킹하여 요약·질의응답 파이프라인에 활용
* OCR 기능을 활용해 스캔된 이미지 기반 문서를 분석하고 정형화된 문서로 변환
* 문서별 추가 메타데이터를 삽입해 검색 가능성과 필터링 기능을 강화

***

### 사용 팁

* 폴더 경로에 유효한 파일만 포함되도록 사전 정리하는 것이 권장됩니다.
* `Hi-Res Model Name`은 이미지 처리 정밀도를 높이기 위한 옵션으로, OCR 기반 문서에 유용합니다.
* 다국어 문서의 경우 `OCR Languages`를 복수로 설정하면 인식률이 향상됩니다.
* `Omit Metadata Keys`로 불필요한 시스템 메타데이터를 제거하여 출력 문서의 간결성을 확보할 수 있습니다.

***

### 주의사항

* `Folder Path`에 포함된 모든 파일이 일괄 처리되므로, 불필요한 파일은 사전에 제외해야 합니다.
* OCR 활성화 시 처리 시간이 길어지고 API 사용량이 증가할 수 있습니다.
* Unstructured API URL이 정확하지 않거나 Credential이 누락될 경우 로딩 실패가 발생합니다.
* 출력 타입을 `Document`로 설정하지 않으면 후속 문서 처리 노드와 연결이 어려울 수 있습니다.
