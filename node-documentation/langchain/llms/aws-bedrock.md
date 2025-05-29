# AWS Bedrock

AWS Bedrock 노드는 Amazon Bedrock 플랫폼에서 제공하는 다양한 LLM 모델을 호출할 수 있는 범용 LLM 노드입니다. Anthropic Claude, AI21, Amazon Titan, Meta Llama 등 여러 벤더의 모델을 단일 인터페이스로 통합하여 사용할 수 있습니다.

***

### 주요 기능

* AWS Bedrock에 배포된 다양한 LLM 모델 호출 가능
* `Region`, `Model Name`, `Temperature` 등 주요 파라미터 설정 지원
* 캐시 기능을 통해 동일 요청 반복 시 성능 최적화
* Amazon 관리형 인프라 기반으로 신뢰성 높은 API 호출 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 103708.png" alt=""><figcaption><p>WindyFlo AWS Bedrock</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 103714 (1).png" alt=""><figcaption><p>WindyFlo AWS Bedrock Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                | 설명                                       | 필수 여부 |
| ----------------- | ---------------------------------------- | ----- |
| Cache             | 동일 요청에 대해 응답 캐시 사용 여부 (ON/OFF)           | 선택    |
| AWS Credential    | AWS Bedrock 호출용 인증 정보 (Credential에 등록)   | 필수    |
| Region            | 사용 중인 AWS Bedrock 리전 (예: `us-east-1`)    | 필수    |
| Model Name        | 사용할 LLM 모델 이름 (예: `anthropic.claude-v2`) | 필수    |
| Custom Model Name | 별도로 정의한 사용자 모델명 (선택)                     | 선택    |

***

### 파라미터 (Parameters)

| 항목                   | 설명                                    |
| -------------------- | ------------------------------------- |
| Temperature          | 출력 텍스트의 창의성 정도 (0.0 \~ 1.0, 기본값: 0.7) |
| Max Tokens to Sample | 생성할 최대 토큰 수 (예: 200)                  |

***

### 출력값 (Outputs)

| 출력 항목      | 설명                                       |
| ---------- | ---------------------------------------- |
| AWSBedrock | Bedrock LLM 응답 결과 (텍스트 또는 JSON 형식 포함 가능) |

***

### 활용 예시

* Claude 기반 대화형 QA 시스템 구성 (예: `anthropic.claude-v2`)
* Amazon Titan 모델을 활용한 텍스트 생성 및 자동화 응답 처리
* 동일 워크플로우 내에서 다양한 모델을 비교 테스트하는 멀티 LLM 설정
* 사내 시스템과 AWS 기반 API 연동하여 LLM 응답 처리 자동화 구축

***

### 사용 팁

* `Model Name`에는 Bedrock에서 지원하는 정확한 모델명(벤더.모델명)을 입력해야 합니다.
  * 예: `anthropic.claude-v2`, `amazon.titan-text-express-v1`, `meta.llama2-13b-chat-v1`
* `Temperature`는 높을수록 창의적인 응답이 나오며, 낮을수록 일관된 응답이 생성됩니다.
* 응답이 너무 짧을 경우 `Max Tokens to Sample` 값을 늘려서 출력 범위를 확장하세요.
* 다양한 모델을 실험해보기 위해 `Custom Model Name`을 사용하면 워크플로우 관리가 쉬워집니다.

***

### 주의사항

* AWS Bedrock은 기본적으로 유료 API이며, 모델별 요금 단가가 상이하므로 사전 확인이 필요합니다.
* `Model Name`을 잘못 입력하면 "Model not found" 오류가 발생합니다. 공식 문서에서 정확한 명칭을 확인하세요.
* 일부 모델은 특정 리전에서만 사용 가능하므로 `Region` 선택 시 제약사항을 고려해야 합니다.
* `Max Tokens to Sample` 값이 너무 크면 요금이 과다 발생하거나 응답이 지연될 수 있으니 적절히 설정해야 합니다.
