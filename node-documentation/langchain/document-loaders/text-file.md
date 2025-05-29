# Text File

Text File 노드는 `.txt` 형식의 파일을 업로드하여 텍스트 데이터를 Document 객체로 변환합니다. 사내 로그, 인터뷰 원문, 문서 초안 등 다양한 텍스트 기반 리소스를 간편하게 AI 파이프라인에 활용할 수 있습니다.

***

### 주요 기능

* 업로드한 `.txt` 파일을 Document 객체로 변환
* Text Splitter와 함께 사용하여 chunk 단위 분할 가능
* 문서에 사용자 지정 메타데이터 추가 가능
* 필요한 경우 메타데이터 필드 제거 기능 제공

<figure><img src="../../../.gitbook/assets/image (76).png" alt=""><figcaption><p>WindyFlo Text File</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (77).png" alt=""><figcaption><p>WindyFlo Text File Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목            | 설명                           | 필수 여부 |
| ------------- | ---------------------------- | ----- |
| Txt File      | 불러올 `.txt` 파일 (UTF-8 인코딩 권장) | 필수    |
| Text Splitter | 텍스트 분할 기준 설정                 | 선택    |

***

### 파라미터 (Parameters)

| 항목                  | 설명                             |
| ------------------- | ------------------------------ |
| Additional Metadata | 변환된 문서에 부여할 사용자 지정 메타데이터       |
| Omit Metadata Keys  | 문서에 포함하지 않을 메타데이터 키 지정 (쉼표 구분) |

***

### 출력값 (Outputs)

| 출력 항목    | 설명                                               |
| -------- | ------------------------------------------------ |
| Document | 텍스트가 포함된 Document 객체 배열 (metadata + pageContent) |
| Text     | 모든 pageContent를 하나로 합친 텍스트 문자열                   |

***

### 활용 예시

* 고객 응대 로그를 AI 요약 파이프라인에 투입
* 인터뷰 초안(txt)을 LLM 기반 정제 파이프라인에 입력
* 프로젝트 회의 기록(txt)을 기반으로 회의록 자동 생성

***

### 사용 팁

* 여러 페이지 또는 긴 텍스트는 Text Splitter 노드와 함께 사용하면 성능 최적화에 유리
* Additional Metadata에 작성일자, 업로드자 등의 정보를 부여하면 관리가 편리
* 분석 대상이 명확한 경우 Omit Metadata Keys로 불필요한 항목 제거 가능

***

### 주의사항

* `.txt` 외 파일 형식은 허용되지 않으며 인코딩 문제 발생 시 텍스트가 깨질 수 있음
* 대용량 텍스트 입력 시 처리 속도 저하 및 chunk 제한에 주의 필요
* 입력 파일 내 민감정보 포함 여부를 사전에 점검 필요
