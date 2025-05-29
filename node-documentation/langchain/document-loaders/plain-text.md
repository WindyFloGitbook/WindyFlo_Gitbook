# Plain Text

Plain Text 노드는 사용자가 입력한 순수 텍스트 데이터를 문서 객체(Document)로 변환합니다. 문서 파일 없이도 간단한 텍스트 콘텐츠를 직접 입력하여 RAG 또는 분석 파이프라인에 활용할 수 있습니다.

***

### 주요 기능

* 입력한 텍스트 문자열을 문서 객체로 변환
* 메타데이터 삽입 또는 제외 설정 가능
* Text Splitter 연계를 통해 긴 텍스트를 자동 분할 처리
* 외부 파일 없이 간단한 텍스트로 AI 기능 테스트에 활용 가능

<figure><img src="../../../.gitbook/assets/image (39).png" alt=""><figcaption><p>WindyFlo Plain Text</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (40).png" alt=""><figcaption><p>WindyFlo Plain Text Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목            | 설명                                  | 필수 여부 |
| ------------- | ----------------------------------- | ----- |
| Text          | 문서로 변환할 순수 텍스트 입력 값                 | 필수    |
| Text Splitter | 입력 텍스트를 분할하는 데 사용할 Text Splitter 노드 | 선택    |

***

### 파라미터 (Parameters)

| 항목                  | 설명                                               |
| ------------------- | ------------------------------------------------ |
| Additional Metadata | 문서에 삽입할 메타데이터 (예: { "source": "manual\_input" }) |
| Omit Metadata Keys  | 제거할 메타데이터 키 목록 (쉼표로 구분하여 입력)                     |

***

### 출력값 (Outputs)

| 출력 항목    | 설명                          |
| -------- | --------------------------- |
| Document | 입력한 텍스트를 기반으로 생성된 문서 객체 리스트 |
| Text     | 입력한 텍스트 문자열 그대로 반환된 값       |

***

### 활용 예시

* 시스템 구축 전 테스트용 텍스트를 빠르게 입력하여 AI 기능 점검
* 복사한 이메일, 회의록, 메모 등 비정형 텍스트를 바로 분석에 활용
* 고객 응대 예문, FAQ 등 간단한 문자열을 AI 응답 학습 데이터로 처리

***

### 사용 팁

* 텍스트 길이가 길 경우 Text Splitter를 연결해 chunk 단위로 분할 처리
* Additional Metadata를 활용하면 문서 출처, 분류 등 태깅 가능
* 텍스트 복사 시 줄바꿈 및 공백 오류가 생기지 않도록 미리 정리 권장

***

### 주의사항

* 입력 텍스트는 반드시 UTF-8 인코딩을 기준으로 처리됨
* HTML, 마크다운 등의 포맷은 일반 텍스트로 취급되므로 스타일 정보는 보존되지 않음
* 긴 텍스트를 단일 입력으로 넣을 경우 메모리 과부하 또는 처리 실패 가능성 있음
