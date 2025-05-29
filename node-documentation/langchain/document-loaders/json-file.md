# Json File

Json File 노드는 업로드된 JSON 파일에서 지정된 키의 데이터를 추출하여 문서 객체(Document)로 변환합니다. API 응답 로그, 사용자 행동 데이터, 크롤링 결과 등 구조화된 데이터를 벡터화하거나 검색 기반 시스템에 활용할 수 있습니다.

***

#### 주요 기능

* 업로드된 JSON 파일에서 특정 키의 값을 추출하여 텍스트로 변환
* 구조화된 데이터의 특정 필드만 선택적으로 가공
* pageContent 외 메타데이터 지정 가능
* Text Splitter와 연계해 텍스트 자동 분할 처리 가능

<figure><img src="../../../.gitbook/assets/image (60).png" alt=""><figcaption><p>WindyFlo Json File</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (61).png" alt=""><figcaption><p>WindyFlo Json File Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                  | 설명                                   | 필수 여부 |
| ------------------- | ------------------------------------ | ----- |
| Json File           | 업로드할 JSON 파일 (.json)                 | 필수    |
| Pointers Extraction | 추출할 키 또는 경로 (예: body, data.text 등)   | 선택    |
| Text Splitter       | 추출된 텍스트를 분할하는 데 사용할 Text Splitter 노드 | 선택    |

***

#### 파라미터 (Parameters)

| 항목                  | 설명                                            |
| ------------------- | --------------------------------------------- |
| Additional Metadata | 문서에 부여할 추가 메타데이터 (JSON 또는 경로 매핑 형식 사용 가능)     |
| Omit Metadata Keys  | 결과 문서에서 제거할 메타데이터 키 목록 (예: `id`, `timestamp`) |

***

#### 출력값 (Outputs)

| 출력 항목    | 설명                                |
| -------- | --------------------------------- |
| Document | pageContent와 메타데이터를 포함한 문서 객체 리스트 |
| Text     | 모든 pageContent를 하나의 문자열로 병합한 텍스트  |

***

#### 활용 예시

* 사용자 피드백 JSON 데이터를 요약하여 인사이트 추출용 파이프라인 구축
* 외부 API 응답 로그에서 특정 필드(body, result 등)만 추출하여 RAG에 활용
* 뉴스, 블로그 등 크롤링 데이터를 벡터 DB로 변환하여 검색 응답 품질 향상

***

#### 사용 팁

* `Pointers Extraction`에는 추출할 JSON 경로를 쉼표로 구분해 입력 가능 (예: body, data.text)
* `Additional Metadata`에 JSON 경로를 지정하면 원본 값이 메타데이터로 자동 포함됨 (예: `{ "url": "/url" }`)
* JSON 배열 내 객체가 많을수록 분할 및 로딩 시간이 증가하므로 필요한 필드만 추출하는 것이 효율적임

***

#### 주의사항

* 비정형 JSON 구조 또는 중첩이 많은 경우, 정확한 경로 지정을 하지 않으면 빈 출력 발생
* 페이지 크기 제한이 있는 경우, Text Splitter 노드를 반드시 연결하여 분할 처리 권장
* JSON 파일의 인코딩 오류 또는 문법 오류가 있을 경우 로딩에 실패할 수 있음
