# OpenAPI Chain

**OpenAPI Chain 노드**는 OpenAPI 명세(YAML)를 기반으로, 사용자의 질문에 맞는 API 경로를 자동으로 선택하고 응답을 해석해 답변을 생성하는 **API 기반 질의응답 자동화 노드**입니다.\
특히 구조화된 API 명세를 파일 또는 링크로 제공하면, LLM이 이를 분석하여 API 호출 흐름을 자동 구성합니다.

***

### 주요 기능

* OpenAPI 스펙 문서를 기반으로 LLM이 API 사용 흐름을 자동 구성
* 사용자 질문에 맞는 API 경로 및 파라미터를 자동 추론
* API 응답을 해석하여 자연어로 정리된 답변 생성
* **YAML 파일 또는 URL 입력** 모두 지원

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-09 164914.png" alt=""><figcaption><p>WindyFlo OpenAPI Chain</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-09 164920 (1).png" alt=""><figcaption><p>WindyFlo OpenAPI Chain Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                   | 설명                                                                    | 필수 여부 |
| -------------------- | --------------------------------------------------------------------- | ----- |
| **Chat Model**       | 사용자 질문을 해석하고 API 호출 구조를 생성할 LLM                                       | 필수    |
| **YAML Link**        | 외부에 호스팅된 OpenAPI YAML 명세 링크 (예: https://api.example.com/openapi.yaml) | 선택    |
| **YAML File**        | 로컬에서 직접 업로드하는 OpenAPI YAML 파일                                         | 선택    |
| **Input Moderation** | 콘텐츠 필터링 기능 활성화 여부                                                     | 선택    |

※ YAML Link와 YAML File 중 **하나 이상 필수**

***

### 파라미터 (Parameters)

| 항목          | 설명                                                                   |
| ----------- | -------------------------------------------------------------------- |
| **Headers** | API 호출 시 필요한 인증 토큰, Accept, Content-Type 등의 HTTP 헤더. JSON 형식으로 입력 가능 |

***

### 출력값 (Outputs)

| 출력 항목            | 설명                            |
| ---------------- | ----------------------------- |
| **OpenAPIChain** | API 호출 결과와 해석된 사용자 응답이 포함된 객체 |

***

### 활용 예시

1. **OpenAPI 기반 외부 서비스와 통합된 Q\&A 시스템**
   * 사용자가: "최근 주문 내역 보여줘"
   * LLM이 `/orders/recent` 경로와 파라미터 자동 선택
   * API 결과를 요약해 사용자에게 응답
2. **Swagger 기반 엔드포인트 자동 연결**
   * 복잡한 API 명세 없이도 YAML 파일 업로드로 자동 분석 및 연결

***

### 사용 팁

* YAML 파일은 **OpenAPI 3.0 이상 버전**을 권장합니다.
* 인증이 필요한 API는 반드시 **Headers에 토큰 또는 키**를 명시해야 합니다.
* 파일 내에 정의된 경로, 메서드, 응답 예시가 구체적일수록 정확한 응답을 생성할 수 있습니다.

***

### 주의사항

* **GET 외의 요청 방식**(POST, PUT 등)이 포함된 API일 경우, LLM이 정확한 파라미터 조합을 찾지 못할 수 있습니다.
* YAML 문서가 잘못된 경우 로딩이 실패할 수 있으므로 **사전 유효성 검사**를 권장합니다.
* 큰 API 명세 파일의 경우 LLM이 일부 정보만 활용할 수 있습니다. **요약된 명세**를 별도로 준비하면 성능이 향상됩니다.

***

OpenAPI Chain은 WindyFlo에서 **구조화된 API 명세 파일을 기반으로 실시간 API 호출 및 응답 해석 기능을 구현할 수 있는 강력한 노드**입니다.\
특히 YAML 기반으로 문서화된 API를 가진 외부 서비스와 통합할 때 유용하게 사용할 수 있습니다.
