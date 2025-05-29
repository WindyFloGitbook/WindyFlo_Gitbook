# Azure OpenAI

Azure OpenAI 노드는 Microsoft Azure 계정을 통해 OpenAI의 텍스트 생성 모델(`text-davinci-003` 등)을 호출할 수 있는 LLM 노드입니다. OpenAI의 기능을 Azure 인프라와 통합해 보안, 확장성, 규정 준수 요건을 만족하면서도 동일한 모델 성능을 제공합니다.

***

### 주요 기능

* Azure 계정으로 OpenAI의 `text-davinci` 모델 계열 사용 가능
* `Temperature`, `Top Probability`, `Frequency Penalty` 등 세부 생성 제어 파라미터 제공
* 캐시 및 Timeout 설정을 통해 안정적인 운영 가능
* Microsoft Azure 정책에 따른 보안성 및 서비스 레벨 보장

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 103858.png" alt=""><figcaption><p>WindyFlo Azure OpenAI</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 103906.png" alt=""><figcaption><p>WindyFlo Azure OpenAI Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                         | 필수 여부 |
| ------------------ | ------------------------------------------ | ----- |
| Cache              | 동일 입력에 대한 응답 캐시 사용 여부                      | 선택    |
| Connect Credential | Azure OpenAI 호출용 인증 정보 (Credential에 등록)    | 필수    |
| Model Name         | 사용할 모델 이름 (예: `text-davinci-003`)          | 필수    |
| Temperature        | 생성 텍스트의 창의성 조절 (기본값: 0.7, 권장 범위: 0 \~ 1.0) | 선택    |

***

### 파라미터 (Parameters)

| 항목                | 설명                                                                            |
| ----------------- | ----------------------------------------------------------------------------- |
| Max Tokens        | 최대 생성 토큰 수 (예: 256, 512 등)                                                    |
| Top Probability   | Top-p 샘플링 확률 값 (예: 0.95)                                                      |
| Best Of           | 여러 응답 중 최선 결과 선택 (예: 3)                                                       |
| Frequency Penalty | 반복 단어 억제 정도 (-2.0 \~ 2.0)                                                     |
| Presence Penalty  | 새로운 주제 유도 정도 (-2.0 \~ 2.0)                                                    |
| Timeout           | API 응답 제한 시간 (ms 단위)                                                          |
| BasePath          | Azure에서 제공하는 API Endpoint 경로 (예: `https://{resource-name}.openai.azure.com/`) |

***

### 출력값 (Outputs)

| 출력 항목       | 설명                                 |
| ----------- | ---------------------------------- |
| AzureOpenAI | LLM 응답 텍스트 또는 JSON 객체 (프롬프트 결과 포함) |

***

### 활용 예시

* 보안이 중요한 금융·공공기관 환경에서 GPT 모델을 활용한 자동 응답 시스템 구축
* Microsoft 기반 내부 시스템과 연동되는 LLM 기능 내재화
* 다양한 프롬프트 세팅을 통해 템플릿 기반 요약, 재작성, 분석 자동화
* OpenAI 대비 더 강력한 SLA 및 액세스 제어가 필요한 엔터프라이즈 환경 적용

***

### 사용 팁

* `BasePath`는 Azure 리소스 배포 시 자동 생성된 Endpoint 경로를 정확히 입력해야 정상 호출됩니다.
* `Temperature`는 0.2\~0.4로 설정하면 더 일관된 응답, 0.8 이상이면 더 창의적인 응답을 유도할 수 있습니다.
* `Top Probability`와 `Temperature`는 동시에 사용하지 않는 것을 권장하며, 하나만 조정해 실험하는 것이 좋습니다.
* `Best Of`는 비용이 증가하므로 품질 개선이 필요한 고정 작업에서만 활용하세요.

***

### 주의사항

* `Model Name`은 Azure에서 사전 배포된 모델만 지원되므로, OpenAI 공식 명칭과 다를 수 있습니다.
* Credential 등록 시 Azure OpenAI 리소스의 이름, 키, 배포된 모델 ID를 모두 정확히 입력해야 합니다.
* 요청당 `Max Tokens`가 클수록 비용 및 지연이 증가하므로 목적에 맞게 적정 수준 설정이 필요합니다.
* API 응답 오류가 발생하는 경우, Azure Resource Quota 또는 요청 속도 제한 정책을 점검해야 합니다.
