# MistralAI Embeddings

MistralAI Embeddings 노드는 Mistral에서 제공하는 임베딩 모델(`mistral-embed`)을 사용하여 텍스트 데이터를 벡터로 변환하는 노드입니다. 고속 대용량 처리에 적합한 구조로 설계되어 있으며, 다양한 텍스트 기반 AI 파이프라인에서 사용할 수 있는 고성능 벡터를 제공합니다.

***

### 주요 기능

* Mistral의 최신 임베딩 모델을 사용하여 고품질 벡터 생성
* 최대 512건의 텍스트를 한 번에 처리 가능한 대규모 Batch 지원
* 개행 문자 제거 옵션, 사용자 지정 Endpoint 등 유연한 설정 가능
* 빠르고 안정적인 벡터 추출로 실시간 검색 및 추천 시스템에 적합

<figure><img src="../../../.gitbook/assets/image (13).png" alt=""><figcaption><p>WindyFlo MistralAI Embeddings</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (14).png" alt=""><figcaption><p>WindyFlo MistralAI Embeddings Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                 | 필수 여부 |
| ------------------ | ---------------------------------- | ----- |
| Connect Credential | Mistral API 인증 정보 (Credential에 등록) | 필수    |
| Model Name         | 사용할 임베딩 모델 이름 (`mistral-embed`)    | 필수    |

***

### 파라미터 (Parameters)

| 항목                | 설명                                              |
| ----------------- | ----------------------------------------------- |
| Batch Size        | 한 번에 처리할 텍스트 수 (기본값: 512)                       |
| Strip New Lines   | 줄바꿈 문자 제거 여부 (기본값: ON)                          |
| Override Endpoint | 기본 Mistral Endpoint 대신 사용할 사용자 지정 Endpoint (선택) |

***

### 출력값 (Outputs)

| 출력 항목               | 설명                      |
| ------------------- | ----------------------- |
| MistralAIEmbeddings | 입력 텍스트에 대한 임베딩 벡터 배열 결과 |

***

### 활용 예시

* RAG 파이프라인에서 검색용 문서 벡터 생성
* 유사한 뉴스 기사, 제품 설명 등을 분석하기 위한 임베딩 비교
* 대량 입력 텍스트를 고속으로 벡터화하여 벡터 DB 삽입
* 줄바꿈 제거를 통해 일관된 벡터 표현이 필요한 챗봇 입력 벡터 생성

***

### 사용 팁

* `Batch Size`는 최대 512까지 지원되며, 대용량 데이터 처리에 유리합니다. 너무 큰 값을 설정하면 요청 실패 가능성이 있으므로 환경에 맞게 조정하세요.
* `Strip New Lines`를 활성화하면 줄바꿈 문자가 벡터 결과에 영향을 주지 않도록 사전 정제됩니다. LLM 입력 시에도 이 설정이 유효할 수 있습니다.
* `Override Endpoint`를 사용하면 자체 프록시 서버나 커스텀 API Gateway를 통해 호출할 수 있어 보안과 라우팅 유연성이 확보됩니다.
* `Model Name`은 현재 `mistral-embed`로 고정되며, 추후 추가 모델이 생길 수 있습니다.

***

### 주의사항

* API Credential이 없거나 잘못된 경우 호출이 실패하며, 응답 메시지를 통해 오류 유형을 확인할 수 있습니다.
* `Override Endpoint`를 사용할 경우, CORS 정책, 인증 헤더 등을 별도로 설정해야 합니다.
* 줄바꿈 제거는 텍스트 의미를 일부 변경할 수 있으므로 상황에 따라 비활성화가 필요할 수 있습니다.
* 과도한 Batch Size 사용 시 처리 시간 지연 또는 API 제한에 도달할 수 있으므로 실환경 테스트가 권장됩니다.
