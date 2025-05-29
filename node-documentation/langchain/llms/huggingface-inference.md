# HuggingFace Inference

HuggingFace Inference 노드는 Hugging Face Hub에 등록된 다양한 텍스트 생성 모델(GPT2, BLOOM 등)을 API를 통해 실행할 수 있도록 지원하는 노드입니다. 커스텀 엔드포인트 설정을 통해 사내 호스팅 모델이나 Hugging Face Inference Endpoints와도 연결 가능합니다.

***

### 주요 기능

* Hugging Face Hub의 모델(gpt2, bloom 등)을 직접 호출해 텍스트 생성
* `Temperature`, `Top-p`, `Top-k`, `Max Tokens` 등 세부 생성 옵션 제공
* 커스텀 엔드포인트 설정을 통한 프라이빗 모델 배포 환경 연동 가능
* Cache 기능으로 반복 호출 시 응답 속도 및 비용 최적화

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 113212.png" alt=""><figcaption><p>WindyFlo HuggingFace Inference</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 113223.png" alt=""><figcaption><p>WindyFlo HuggingFace Inference Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                            | 필수 여부 |
| ------------------ | --------------------------------------------- | ----- |
| Cache              | 동일 요청에 대한 결과를 저장해 재사용할지 여부                    | 선택    |
| Connect Credential | Hugging Face API 토큰 (Credential에 등록)          | 필수    |
| Model              | 사용할 모델 이름 (예: `gpt2`, `bigscience/bloom`)     | 필수    |
| Endpoint           | Hugging Face Inference Endpoint 또는 사설 API URL | 선택    |

***

### 파라미터 (Parameters)

| 항목                | 설명                                     |
| ----------------- | -------------------------------------- |
| Temperature       | 생성 다양성 조절값 (0.0 \~ 1.0)                |
| Max Tokens        | 생성할 최대 토큰 수                            |
| Top Probability   | Top-p (nucleus sampling) 값 설정 (예: 0.9) |
| Top K             | Top-k 샘플링 설정값                          |
| Frequency Penalty | 반복 단어 억제 수치 (-2.0 \~ 2.0)              |

***

### 출력값 (Outputs)

| 출력 항목                | 설명                          |
| -------------------- | --------------------------- |
| HuggingFaceInference | 모델로부터 생성된 텍스트 결과 또는 JSON 응답 |

***

### 활용 예시

* 사내 인프라 또는 Hugging Face의 프라이빗 모델을 활용한 맞춤형 텍스트 생성 워크플로우 구축
* 오픈소스 LLM 기반 RAG 시스템 실험
* 비용을 고려해 OpenAI 대신 Hugging Face 모델로 실험 환경 구성
* 다양한 모델 설정을 통한 생성 품질 비교 및 평가

***

### 사용 팁

* `Model` 이름은 Hugging Face 모델 페이지의 정확한 경로를 입력해야 하며, 예: `bigscience/bloom`, `tiiuae/falcon-7b-instruct`
* `Endpoint`는 Hugging Face에서 생성한 Inference Endpoint URL 또는 로컬 프록시 서버 주소를 입력할 수 있습니다.
* `Top Probability`와 `Top K`는 함께 사용하는 경우 결과 다양성이 커질 수 있으나, 품질 저하 가능성도 있습니다.
* `Temperature`와 `Max Tokens` 조합을 적절히 조정하면 응답 품질과 비용을 동시에 관리할 수 있습니다.

***

### 주의사항

* 해당 노드는 입력된 모델 경로 또는 Endpoint가 잘못될 경우 오류를 반환하므로 사전 확인이 필수입니다.
* Hugging Face의 일부 모델은 인증 토큰이 없으면 호출이 제한될 수 있습니다.
* 생성된 응답 형식은 모델마다 다르므로 후처리 로직에서 주의가 필요합니다.
* 로컬 서버와 연동 시 API Timeout, 포맷 불일치 등에 대한 예외처리 필요
