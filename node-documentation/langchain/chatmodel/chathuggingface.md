# ChatHuggingFace

ChatHuggingFace 노드는 Hugging Face Inference API를 통해 다양한 오픈소스 대화형 모델(GPT, LLaMA 등)을 호출하는 Chat Model 노드입니다. API 키만으로 신속하게 외부 모델을 연결할 수 있어, 유연한 테스트와 비용 효율적인 서비스 설계가 가능합니다.

***

#### 주요 기능

* Hugging Face의 호스팅 모델(gpt 등)을 호출하여 응답 생성
* Endpoint와 API Key 기반으로 간단하게 모델 연결 가능
* Temperature, Top-K, Stop Sequence 등 다양한 생성 제어 옵션 제공
* 사용자 정의 Stop Sequence로 응답 종료 조건 설정 가능
* 저비용 테스트용 또는 실험적 오픈모델 적용에 적합

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 104507.png" alt=""><figcaption><p>WindyFlo ChatHuggingFace</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 104518.png" alt=""><figcaption><p>WindyFlo ChatHuggingFace Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                 | 설명                                          | 필수 여부 |
| ------------------ | ------------------------------------------- | ----- |
| Connect Credential | Hugging Face API Key (Credential에 등록된 값)    | 필수    |
| Model              | 사용할 모델명 (예: gpt2, mistralai/Mixtral-8x7B 등) | 필수    |
| Endpoint           | Inference Endpoint URL (자동 완성됨, 별도 입력 불필요)  | 선택    |

***

#### 파라미터 (Parameters)

| 항목                | 설명                                       |
| ----------------- | ---------------------------------------- |
| Temperature       | 응답 창의성 조절 값 (0.0 \~ 1.0)                 |
| Max Tokens        | 생성할 최대 토큰 수                              |
| Top Probability   | Top-P 샘플링 확률 값                           |
| Top K             | Top-K 샘플링 후보 수                           |
| Frequency Penalty | 중복 어휘 감소 계수                              |
| Stop Sequence     | 응답 종료 기준 문자열 또는 패턴 (예: “AI:”, “\nUser:”) |

***

#### 출력값 (Outputs)

| 출력 항목           | 설명                            |
| --------------- | ----------------------------- |
| ChatHuggingFace | Hugging Face 모델의 응답 또는 텍스트 결과 |

***

#### 활용 예시

* gpt2 또는 Mistral 계열 모델을 테스트 환경에서 빠르게 호출하여 응답 품질 검증
* Hugging Face에서만 제공되는 특화 모델 활용 (예: 의료, 법률 등 도메인 모델)
* 응답 제어 파라미터를 세밀하게 조정하여 콘텐츠 생성용 어시스턴트 프로토타입 구현
* 가격 부담 없는 실험적 챗봇 기능을 MVP 서비스에 탑재

***

#### 사용 팁

* **Stop Sequence**를 활용하면 모델이 불필요한 응답을 이어가지 않도록 제어할 수 있음
* **Top-K**와 **Top-P**를 동시에 설정하면 응답 다양성과 안정성을 균형 있게 유지 가능
* Hugging Face에 등록된 최신 모델명을 직접 입력하여 커스텀 실험 가능

***

#### 주의사항

* Hugging Face API Key는 유료 요금제에 따라 호출량 제한이 존재하며, 토큰당 과금에 주의해야 함
* 공개된 모델 중 일부는 응답 지연이 발생하거나 품질이 불안정할 수 있음
* Endpoint는 자동 생성되며 대부분의 경우 수정이 불필요하나, Private Model 호출 시 별도 설정 필요
* Stop Sequence를 설정하지 않으면 응답이 과도하게 길어질 수 있음
