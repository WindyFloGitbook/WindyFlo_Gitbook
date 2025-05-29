# LocalAI Embeddings

LocalAI Embeddings 노드는 사용자의 자체 서버(LocalAI 인스턴스)에 배포된 임베딩 모델을 호출하여 텍스트를 벡터로 변환하는 노드입니다. 외부 API 의존 없이 로컬 환경에서 임베딩 처리를 할 수 있어 보안 및 비용 측면에서 유리합니다.

***

### 주요 기능

* LocalAI 서버에 배포된 임베딩 모델을 호출하여 로컬 임베딩 처리
* 외부 API 없이 내부 네트워크 또는 오프라인 환경에서 운영 가능
* Base Path 및 Model Name을 자유롭게 지정해 유연한 설정 가능
* 보안이 중요한 환경 또는 비용 최소화를 원하는 프로젝트에 적합

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-13 173104.png" alt=""><figcaption><p>WindyFlo LocalAI Embeddings</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                                          | 필수 여부 |
| ------------------ | ----------------------------------------------------------- | ----- |
| Connect Credential | LocalAI 서버 인증 정보 (Credential에 등록)                           | 필수    |
| Base Path          | LocalAI 서버의 API Endpoint 주소 (예: `http://localhost:8080/v1`) | 필수    |
| Model Name         | 사용할 임베딩 모델 이름 (예: `text-embedding-ada-002`)                 | 필수    |

***

### 파라미터 (Parameters)

※ 별도 고급 설정 파라미터 없음

***

### 출력값 (Outputs)

| 출력 항목             | 설명                      |
| ----------------- | ----------------------- |
| LocalAIEmbeddings | 입력 텍스트에 대한 임베딩 벡터 결과 배열 |

***

### 활용 예시

* 인터넷 연결 없이도 자체 서버(LocalAI)를 통해 텍스트 임베딩 수행
* 사내 서버에 구축한 OpenAI 호환 모델을 활용하여 벡터 DB 연계
* 비용 절감이 중요한 프로젝트에서 외부 API 호출 없이 임베딩 생성
* 의료, 금융 등 외부 데이터 전송이 제한된 환경에서 안전하게 벡터 생성

***

### 사용 팁

* `Base Path`는 정확한 포맷(`http://.../v1`)으로 입력해야 하며, LocalAI 서버와 연결되어 있어야 합니다.
* `Model Name`은 LocalAI에 사전 등록된 모델과 정확히 일치해야 정상 호출됩니다. 예: `text-embedding-ada-002`
* LocalAI는 OpenAI API 형식을 대부분 호환하므로 기존 GPT 임베딩 워크플로우를 그대로 적용할 수 있습니다.
* Docker 기반의 LocalAI를 사용할 경우, 포트 설정과 CORS 정책을 사전에 확인해두는 것이 좋습니다.

***

### 주의사항

* LocalAI 서버가 실행 중이지 않거나 연결 정보가 잘못된 경우 호출이 실패합니다.
* 모델이 LocalAI 내에 사전 로드되어 있어야 하며, 미등록 모델 호출 시 오류가 발생합니다.
* 외부 API보다 응답 속도는 빠르지만, 하드웨어 사양에 따라 성능이 크게 달라질 수 있습니다.
* GPU 없이 동작할 경우 처리 시간이 길어질 수 있으므로 벡터 생성 시 리소스 상태를 확인하세요.
