# POST API Chain

**POST API Chain 노드**는 외부 API 문서를 기반으로 LLM이 자동으로 POST 요청의 URL과 요청 본문(payload)을 생성하고, 호출 결과를 해석하여 자연어 응답을 생성하는 **자동화된 POST 요청 체인 노드**입니다.

***

### 주요 기능

* API 문서를 분석해 LLM이 요청 URL과 body 데이터를 자동 생성
* 자동으로 POST 요청 수행 및 응답 해석
* 인증, 데이터 등록, 트리거형 API 호출 시 활용 가능
* 프롬프트 기반으로 유연하게 요청 포맷을 설정 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-09 165050.png" alt=""><figcaption><p>WindyFlo POST API Chain</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-09 165059.png" alt=""><figcaption><p>WindyFlo POST API Chain Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                    | 설명                                  | 필수 여부 |
| --------------------- | ----------------------------------- | ----- |
| **Language Model**    | 사용자 질문을 분석하고 POST 요청 구조를 생성할 LLM    | 필수    |
| **API Documentation** | OpenAPI 명세 또는 예제 기반 API 문서 (텍스트 형태) | 필수    |

***

### 파라미터 (Parameters)

| 항목                | 설명                                                       |
| ----------------- | -------------------------------------------------------- |
| **Headers**       | POST 요청 시 포함할 HTTP 헤더 (예: Authorization, Content-Type 등) |
| **URL Prompt**    | 사용자 질문에 기반해 호출할 URL과 JSON body를 생성하는 프롬프트                |
| **Answer Prompt** | POST 요청 결과를 해석해 사용자 질문에 대한 응답을 생성하는 프롬프트                 |

#### URL Prompt 예시

```
text복사편집You are given the below API Documentation: {api_docs}
Using this documentation, generate a JSON string with two keys: "url" and "data".
The value of "url" should be a string, which is the API url to call for the user’s request.
The value of "data" should be a JSON object that contains the correct request payload.
```

#### Answer Prompt 예시

```
text복사편집You are given the below API Documentation: {api_docs}
Using this documentation, generate a JSON string with two keys: "url" and "data".
The value of "url" should be a string, which is the API url to call for the user’s request.
The value of "data" should be a JSON object that contains the correct request payload.
```

***

### 출력값 (Outputs)

| 출력 항목            | 설명                             |
| ---------------- | ------------------------------ |
| **POSTApiChain** | POST 요청 결과와 해석된 자연어 응답이 포함된 객체 |

***

### 활용 예시

1. **회원가입 요청 자동화**
   * 사용자: "회원가입 요청 보내줘"
   * LLM이 `/register` 경로와 payload 자동 구성 → POST 요청 실행 → 성공 여부 응답
2. **Slack Webhook 자동 발송**
   * 사용자: "슬랙에 메시지 보내줘"
   * URL과 메시지 payload 자동 생성 → POST 요청으로 전송
3. **예약 시스템 연동**
   * 사용자: "5월 20일 오후 2시로 예약해줘"
   * 예약 API URL 및 JSON 본문 자동 생성 → 결과 응답 처리

***

### 사용 팁

* **API 문서에는 필수 파라미터, 요청 형식, 응답 예시가 명확히 포함되어야** LLM이 올바른 POST 요청을 구성할 수 있습니다.
* 프롬프트는 API 특성에 맞게 커스터마이징 가능합니다. (예: 특정 필드 강제 지정 등)
* 인증이 필요한 경우 Headers에 `Authorization` 등 헤더를 명시해야 합니다.

***

### 주의사항

* 이 노드는 반드시 **POST 메서드 전용**입니다. GET 요청은 별도의 GET API Chain 노드를 사용하세요.
* API 명세가 불완전하거나 요청 형식이 복잡한 경우, 응답이 예상과 다를 수 있습니다.
* Headers 필드는 JSON 구조로 구성하며, `Content-Type: application/json`과 같은 필드를 반드시 포함하는 것을 권장합니다.

***

POST API Chain은 WindyFlo에서 **양식 전송, 등록, 업데이트 요청 등의 시나리오에 유용하게 활용 가능한 자동 POST 호출 노드**입니다.\
API 문서만 있으면 사용자의 질의에 따라 유연하게 POST 구조를 자동화할 수 있습니다.
