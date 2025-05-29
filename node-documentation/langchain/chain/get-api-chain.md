# GET API Chain

**ET API Chain 노드**는 사용자 질문에 따라 외부 API 문서를 기반으로 적절한 URL을 생성하고 호출한 뒤, 해당 응답을 해석하여 자연어 답변을 생성하는 **자동 API 질의 응답 체인 노드**입니다.

***

### 주요 기능

* API 문서를 기반으로 **LLM이 자동으로 URL을 구성**
* 구성된 URL로 GET 요청을 수행하고 **응답 결과 해석**
* 사용자 질문에 대해 **API 기반의 실시간 답변 제공 가능**
* API 명세가 자주 변경되는 서비스에서도 유연하게 대응 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-09 163514.png" alt=""><figcaption><p>WindyFlo GET API Chain</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-09 163527.png" alt=""><figcaption><p>WindyFlo GET API Chain Parameters</p></figcaption></figure>

### 파라미터 (Parameters)

| 항목                | 설명                                            |
| ----------------- | --------------------------------------------- |
| **Headers**       | 요청 시 포함할 HTTP 헤더 (예: 인증 토큰, 콘텐츠 타입 등)         |
| **URL Prompt**    | 주어진 API 문서를 기반으로 호출할 URL을 생성하는 프롬프트. 아래 예시 참고 |
| **Answer Prompt** | 호출 결과를 바탕으로 사용자 질문에 답변을 생성하는 프롬프트. 아래 예시 참고   |

#### URL Prompt 예시

```
You are given the below API Documentation: {api_docs}
Using this documentation, generate the full API url to call for answering the user question.
You should build the API url in order to get a response that is as short as possible.
```

***

#### Answer Prompt 예시

```
Given this {api_response} response for {api_url}, use the given response to answer this {question}
```

### 출력값 (Outputs)

| 출력 항목           | 설명                            |
| --------------- | ----------------------------- |
| **GETApiChain** | API 호출 결과와 해석된 사용자 응답이 포함된 객체 |

***

### 활용 예시

1. **실시간 날씨 확인 봇**
   * 사용자: "서울 날씨 알려줘"
   * API 문서 기반으로 `/weather?city=Seoul` 자동 구성
   * 응답 결과 → "현재 서울은 맑고 25도입니다."
2. **금융 데이터 조회 시스템**
   * 사용자: "오늘 테슬라 주가 알려줘"
   * URL 자동 생성 + 응답 해석 → 실시간 금융 봇 구현 가능

***

### 사용 팁

* API 문서 입력 시, **경로(URL), 파라미터, 응답 예시**를 함께 넣으면 더 정확한 URL이 생성됩니다.
* Prompt는 **서비스 목적에 따라 커스터마이징**하면 응답 품질이 크게 향상됩니다.

***

### 주의사항

* 이 노드는 **GET 방식 API 전용**입니다. POST, PUT 등은 별도 노드를 사용하세요.
* 보안이 필요한 API는 Headers에 인증 정보를 반드시 포함해야 합니다.
* LLM이 문서를 기반으로 URL을 생성하므로 **문서가 불명확하면 예외적 동작이 발생할 수 있습니다.**

***

GET API Chain은 WindyFlo에서 **외부 API 기반 자동 응답 시스템을 구현할 수 있는 핵심 노드**로, 실시간 정보 제공 서비스에 적합합니다.
