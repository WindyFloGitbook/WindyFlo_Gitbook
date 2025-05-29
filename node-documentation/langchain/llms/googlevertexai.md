# GoogleVertexAI

GoogleVertexAI 노드는 Google Cloud의 Vertex AI 플랫폼을 통해 텍스트 생성 모델(예: `text-bison`)을 호출할 수 있는 LLM 노드입니다. Google의 최신 PaLM 기반 모델을 활용하여 안전하고 고성능의 텍스트 생성이 가능합니다.

***

### 주요 기능

* Google Vertex AI의 `text-bison` 모델을 활용한 고품질 텍스트 생성
* `Temperature`, `Top Probability`, `max Output Tokens` 등 세부 파라미터 조정 가능
* 캐시 기능을 통해 반복 요청 비용 절감
* GCP 인증 기반의 보안된 API 연결 지원

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 112914.png" alt=""><figcaption><p>WindyFlo GoogleVertexAI</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 112932.png" alt=""><figcaption><p>WindyFlo GoogleVertexAI Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                   | 필수 여부 |
| ------------------ | ------------------------------------ | ----- |
| Cache              | 동일 요청 응답을 캐싱하여 재사용 여부 설정             | 선택    |
| Connect Credential | GCP 인증 정보 (Credential에 등록)           | 필수    |
| Model Name         | 사용할 모델 이름 (예: `text-bison`)          | 필수    |
| Temperature        | 생성 결과의 다양성 조절 (0.0 \~ 1.0, 기본값: 0.7) | 선택    |

***

### 파라미터 (Parameters)

| 항목                | 설명                              |
| ----------------- | ------------------------------- |
| max Output Tokens | 최대 생성 토큰 수 (예: 256, 1024 등)     |
| Top Probability   | Top-p 샘플링 확률 설정 (예: 0.9, 1.0 등) |

***

### 출력값 (Outputs)

| 출력 항목          | 설명                    |
| -------------- | --------------------- |
| GoogleVertexAI | 생성된 텍스트 또는 JSON 형식 결과 |

***

### 활용 예시

* Google Cloud 인프라 기반의 엔터프라이즈급 AI 텍스트 생성 시스템 구성
* 내부 데이터와 연결된 RAG 시스템에서 PaLM 계열 모델을 활용한 응답 생성
* SEO, 마케팅 문서 자동 생성과 같은 콘텐츠 제작 업무 자동화
* 응답 일관성과 안정성을 요구하는 고객 응대용 AI 도우미 구축

***

### 사용 팁

* `text-bison`은 Google PaLM 2 기반으로, 일반 지식 및 비즈니스 응답 품질이 뛰어나며 다양한 도메인에 적합합니다.
* `Temperature`는 낮게 설정할수록 정형화된 응답을, 높게 설정할수록 창의적인 출력을 유도합니다.
* `max Output Tokens`는 실제 사용 시 필요한 응답 길이에 맞춰 조정해야 합니다. 과도하게 설정하면 비용이 증가할 수 있습니다.
* GCP IAM 권한이 적절히 구성되지 않으면 Credential 오류가 발생할 수 있으므로 사전 설정 필요합니다.

***

### 주의사항

* GoogleVertexAI는 사전 GCP 프로젝트 등록 및 Vertex AI API 사용 설정이 필요합니다.
* 모델 호출 시 사용되는 리소스에 따라 요금이 청구되므로 호출 횟수 및 토큰 길이에 유의해야 합니다.
* `Top Probability`와 `Temperature`를 동시에 높게 설정하면 예측 불가능한 응답이 생성될 수 있으므로 테스트를 통해 최적값을 찾는 것이 좋습니다.
* Vertex AI는 지역 리전 설정에 따라 접근 가능한 모델이 제한될 수 있습니다 (`us-central1`, `us-east1` 등).
