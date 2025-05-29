# Json Lines File

Json Lines File 노드는 `.jsonl` 형식의 파일을 업로드하여 각 줄별 JSON 객체를 문서 객체(Document)로 변환합니다. 로그, 크롤링 결과, 사용자 이벤트 기록 등 대용량 스트리밍 데이터를 AI 파이프라인에서 활용하기 적합합니다.

***

### 주요 기능

* `.jsonl` 형식의 파일에서 각 줄을 독립적인 문서 객체로 추출
* 지정한 키에 해당하는 값만 pageContent로 사용 가능
* 각 JSON 객체 내 값을 메타데이터로 삽입하거나 제외 설정 가능
* Text Splitter 연계를 통해 대용량 데이터 자동 분할 가능

<figure><img src="../../../.gitbook/assets/image (29).png" alt=""><figcaption><p>WindyFlo Json Lines File</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (30).png" alt=""><figcaption><p>WindyFlo Json Lines File Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                    | 필수 여부 |
| ------------------ | ------------------------------------- | ----- |
| Jsonlines File     | 업로드할 JSONL 파일 (.jsonl)                | 필수    |
| Pointer Extraction | pageContent로 사용할 키 또는 경로 (예: content) | 필수    |
| Text Splitter      | 추출된 텍스트를 분할하는 데 사용할 Text Splitter 노드  | 선택    |

***

### 파라미터 (Parameters)

| 항목                  | 설명                                     |
| ------------------- | -------------------------------------- |
| Additional Metadata | 문서에 부여할 추가 메타데이터 (정적 JSON 또는 경로 매핑 가능) |
| Omit Metadata Keys  | 결과 문서에서 제거할 메타데이터 키 목록 (예: id, time 등) |

***

### 출력값 (Outputs)

| 출력 항목    | 설명                                |
| -------- | --------------------------------- |
| Document | pageContent와 메타데이터를 포함한 문서 객체 리스트 |
| Text     | 모든 pageContent를 하나의 문자열로 병합한 텍스트  |

***

### 활용 예시

* 고객 행동 로그(JSONL) 데이터를 AI 요약 및 이상 탐지 파이프라인에 연결
* 뉴스 기사, 리뷰 등의 크롤링 결과를 분할 로딩하여 RAG 시스템 구축
* API 로그 파일을 사내 지식베이스에 통합하고 자연어 질의 응답 구현

***

### 사용 팁

* Pointer Extraction에는 추출할 키 이름만 입력 (예: `content`)
* Additional Metadata는 JSON 경로 매핑 형식도 가능 (예: `{ "source": "/source" }`)
* JSONL은 줄 단위로 파싱되므로, 데이터가 많을수록 메모리 사용량 증가에 유의

***

### 주의사항

* 잘못된 포맷의 `.jsonl` 파일은 중단 없이 오류 발생 가능하므로 사전 유효성 검토 필수
* Pointer Extraction 항목이 존재하지 않는 경우, 해당 줄은 건너뜀
* JSONL 구조 상, 중첩된 필드가 많을 경우 메타데이터 매핑에 주의 필요
