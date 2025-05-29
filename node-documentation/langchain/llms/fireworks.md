# Fireworks

Fireworks 노드는 Fireworks.ai 플랫폼을 통해 제공되는 다양한 오픈소스 LLM(예: LLaMA, Mistral 등)을 호출할 수 있는 노드입니다. Hugging Face 호환 API 기반으로 작동하며, 저비용 고성능 LLM을 API 형태로 활용할 수 있도록 지원합니다.

***

### 주요 기능

* Fireworks.ai 계정을 통해 다양한 오픈소스 LLM을 API 호출 방식으로 사용 가능
* `Model Name` 입력을 통해 LLaMA, Mistral 등 다양한 모델 지정
* Cache 기능으로 동일 프롬프트 요청 시 응답 시간 및 비용 최적화
* Hugging Face Inference API와 유사한 방식으로 간단한 통합 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 110441.png" alt=""><figcaption><p>WindyFlo Fireworks</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                                     | 필수 여부 |
| ------------------ | ------------------------------------------------------ | ----- |
| Cache              | 동일 요청 응답 캐시 여부                                         | 선택    |
| Connect Credential | Fireworks API Key (Credential에 등록)                     | 필수    |
| Model Name         | 사용할 모델 경로 (예: `accounts/fireworks/models/llama-v2-7b`) | 필수    |

***

### 파라미터 (Parameters)

※ 해당 노드는 추가 설정 없이 단순 API 호출 중심으로 구성되며, 별도 고급 파라미터 없음

***

### 출력값 (Outputs)

| 출력 항목     | 설명                    |
| --------- | --------------------- |
| Fireworks | LLM 응답 텍스트 또는 JSON 결과 |

***

### 활용 예시

* Meta LLaMA 기반 모델을 활용한 저비용 RAG 시스템 구축
* OpenAI 대비 저렴한 가격으로 유사 성능의 텍스트 생성 워크플로우 구성
* 프라이빗 LLM 실험 및 퍼포먼스 테스트 환경 구성
* Hugging Face Transformers 형식의 모델을 Fireworks 인프라에서 배포·실행하는 경우

***

### 사용 팁

* `Model Name`은 Fireworks에서 사전에 배포된 정확한 모델 경로를 입력해야 하며, 보통 Hugging Face 스타일 경로를 따릅니다.
  * 예: `accounts/fireworks/models/llama-v2-7b`, `accounts/fireworks/models/mistral-7b`
* 프롬프트 디자인은 일반적인 OpenAI 포맷과 유사하므로 쉽게 이전할 수 있습니다.
* 모델 성능과 응답 속도는 GPU 사용량과 모델 사이즈에 따라 차이가 나므로 사전 테스트가 중요합니다.
* Fireworks는 빠르게 모델을 교체하거나 최신 오픈모델을 실험할 때 특히 유리합니다.

***

### 주의사항

* `Connect Credential`이 정확히 등록되지 않으면 인증 실패로 인해 응답을 받을 수 없습니다.
* `Model Name` 경로가 잘못되거나 권한이 없는 경우 HTTP 오류가 반환되므로 Fireworks 계정에서 사전 확인 필요
* Fireworks API는 사용량 기반 과금이며, 대규모 요청 시 요금 주의가 필요합니다.
* 특정 모델은 유료 요금제에서만 사용 가능할 수 있으며, 리소스 제약도 존재할 수 있습니다.
