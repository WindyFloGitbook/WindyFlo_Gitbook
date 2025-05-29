# Replicate

Replicate 노드는 Replicate 플랫폼의 사전 학습된 모델을 호출하여 텍스트 생성 작업을 수행할 수 있도록 지원합니다. 사용자는 원하는 모델과 파라미터를 지정하여 다양한 자연어 처리 작업에 활용할 수 있습니다.

***

### 주요 기능

* Replicate에 호스팅된 사전 학습 모델을 호출하여 텍스트 생성
* 모델 이름을 직접 지정하여 다양한 모델(LLaMA, StableLM 등) 사용 가능
* Temperature, Top-p 등 핵심 생성 파라미터 조정 가능
* 최대 토큰 수, 반복 패널티 등 세부 제어 지원
* Additional Inputs 항목을 통한 사용자 지정 인수 전달 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 134125.png" alt=""><figcaption><p>WindyFlo Replicate</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 134143.png" alt=""><figcaption><p>WindyFlo Replicate Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                           | 필수 여부 |
| ------------------ | -------------------------------------------- | ----- |
| Connect Credential | Replicate API Key를 Credential에 등록하여 연결       | 필수    |
| Model              | 호출할 모델 경로 (예: `a16z-infra/llama13b-v2-chat`) | 필수    |
| Temperature        | 창의성 조절 (0.0 \~ 1.0, 높을수록 다양성 증가)             | 선택    |

***

### 파라미터 (Parameters)

| 항목                 | 설명                                  |
| ------------------ | ----------------------------------- |
| Max Tokens         | 출력 최대 길이 (예: 512)                   |
| Top Probability    | Top-p 샘플링 값 (0.0 \~ 1.0, 예: 0.9)    |
| Repetition Penalty | 반복 억제 계수 (예: 1.1)                   |
| Additional Inputs  | 모델에 따라 필요한 추가 파라미터를 JSON 형식으로 전달 가능 |

***

### 출력값 (Outputs)

| 출력 항목     | 설명               |
| --------- | ---------------- |
| Replicate | 모델로부터 생성된 텍스트 결과 |

***

### 활용 예시

* LLaMA 기반 텍스트 생성 모델을 이용한 마케팅 문안 생성
* StableLM 또는 CodeGen 모델로 코드 요약 자동화
* 다양한 오픈소스 모델 성능 비교 및 벤치마킹 실험
* 생성 모델 파라미터 튜닝을 통한 챗봇 응답 품질 개선

***

### 사용 팁

* Temperature와 Top-p는 한 번에 하나만 조정하여 결과 차이를 비교하는 것이 좋습니다.
* Max Tokens를 짧게 설정하면 응답 속도가 빨라지지만 응답 품질은 낮아질 수 있습니다.
* Additional Inputs에 `"system_prompt"` 또는 `"instruction"`을 포함하여 프롬프트 커스터마이징이 가능합니다.

***

### 주의사항

* Connect Credential에 반드시 Replicate API 키를 등록해야 정상 작동합니다.
* 모델 경로는 Replicate 플랫폼 기준으로 정확히 입력해야 하며, 오탈자 시 호출 오류가 발생합니다.
* 유료 모델 사용 시 Replicate 측에서 요금이 부과될 수 있으므로 사용 전 확인이 필요합니다.
* 출력값이 많을 경우, 토큰 초과 또는 응답 지연이 발생할 수 있습니다.
