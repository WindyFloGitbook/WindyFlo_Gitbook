# API Loader

외부 API에서 데이터를 불러와 문서 형식(Document)으로 변환하는 로더 노드입니다. RESTful API를 활용해 다양한 JSON 데이터를 수집하고, 이후 텍스트 분할기와 함께 문서 파이프라인에 사용할 수 있습니다. 내부 문서화되지 않은 API도 자유롭게 호출할 수 있어 확장성이 뛰어납니다.

***

#### 주요 기능

* GET 또는 POST 방식으로 외부 API 호출 가능
* 응답 데이터를 Document 형식으로 변환
* Headers, Body, Metadata 등 세부 요청 구성 가능
* 응답 데이터 중 제외할 Metadata key를 지정해 정제된 문서 생성
* Text Splitter와 함께 사용 시 장문 응답 처리 용이

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 131839.png" alt=""><figcaption><p>WindyFlo API Loader</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 131911.png" alt=""><figcaption><p>WindyFlo API Loader Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목            | 설명                      | 필수 여부 |
| ------------- | ----------------------- | ----- |
| Text Splitter | 긴 텍스트 분할을 위한 노드 연결      | 선택    |
| Method        | API 호출 방식 (GET 또는 POST) | 필수    |
| URL           | API 엔드포인트 URL           | 필수    |

***

#### 파라미터 (Parameters)

| 항목                  | 설명                                                                   |
| ------------------- | -------------------------------------------------------------------- |
| Headers             | 요청 시 포함할 HTTP 헤더 항목들 (예: Authorization)                              |
| Body                | POST 방식 사용 시 전달할 데이터 객체                                              |
| Additional Metadata | 문서에 함께 포함할 추가 메타데이터 항목                                               |
| Omit Metadata Keys  | 응답 데이터 중 제외할 metadata 키 지정 (쉼표로 구분된 키 목록, 예: `key1, key2.nestedKey`) |

***

#### 출력값 (Outputs)

| 출력 항목    | 설명                                        |
| -------- | ----------------------------------------- |
| Document | pageContent와 metadata를 포함한 Document 객체 배열 |
| Text     | 모든 문서를 하나의 텍스트로 연결한 문자열 (선택 출력 형식)        |

***

#### 활용 예시

* Step 1. 사내 API 또는 외부 API로부터 JSON 데이터 수집
* Step 2. Headers와 Body 값을 설정하여 인증된 POST 요청 실행
* Step 3. 문서로 변환된 응답을 벡터 스토어에 저장하거나 QA 파이프라인에 활용
* 고객 리뷰 API, 기술문서 API, 뉴스 API 등을 문서로 처리 가능
* Custom Metadata 삽입으로 후속 검색/필터링 최적화
* URL만 바꿔도 다양한 API 연동 가능하여 반복 활용도 높음

***

#### 사용 팁

* Text Splitter를 함께 사용하면 API 응답이 장문일 경우에도 적절히 분할 가능
* 응답 구조가 복잡할 경우 `Omit Metadata Keys`를 활용하여 불필요한 필드 정리
* API 키가 필요한 경우 Headers에 `Authorization` 키 삽입 필요

***

#### 주의사항

* Method와 URL은 반드시 입력되어야 하며, 누락 시 실행되지 않음
* API 응답 형식이 문서 처리에 적합하지 않다면 후속 파싱이 필요
* 과도한 데이터 호출은 속도 저하 및 API 요금 과금 위험 존재
* Text Splitter 미연결 시 긴 텍스트가 잘리지 않고 그대로 전달됨
