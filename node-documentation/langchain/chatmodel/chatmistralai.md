# ChatMistralAI

ChatMistralAI 노드는 Mistral.ai에서 제공하는 LLM(mistral-tiny, mistral-small 등)을 호출하는 Chat Model 노드입니다. 경량 모델 기반의 빠른 응답과 유연한 API 설정을 통해 빠른 테스트와 고성능 워크플로우 구성에 적합합니다.

***

#### 주요 기능

* Mistral.ai가 제공하는 오픈 모델(mistral-tiny 등) 호출 가능
* Top-P, Max Tokens, Safe Mode 등 응답 제어 파라미터 지원
* Streaming 모드 지원으로 실시간 응답 가능
* Endpoint Override 기능으로 엔터프라이즈 환경에 유연하게 적용 가능
* 고성능 대비 비용 효율적인 API 사용 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 111442.png" alt=""><figcaption><p>WindyFlo ChatMistralAI</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 111451.png" alt=""><figcaption><p>WindyFlo ChatMistralAI Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                 | 설명                                                         | 필수 여부 |
| ------------------ | ---------------------------------------------------------- | ----- |
| Connect Credential | Mistral API Key (Credential에 등록된 값)                        | 필수    |
| Model Name         | 사용할 모델명 (예: mistral-tiny, mistral-small, mistral-medium 등) | 필수    |
| Temperature        | 창의성 조절 값 (0.0 \~ 1.0, 기본값: 0.9)                            | 선택    |

***

#### 파라미터 (Parameters)

| 항목                | 설명                                 |
| ----------------- | ---------------------------------- |
| Streaming         | 응답을 스트리밍 방식으로 받을지 여부 (기본값: true)   |
| Max Output Tokens | 출력 최대 토큰 수                         |
| Top Probability   | Top-P 확률 기반 샘플링 값                  |
| Random Seed       | 응답 생성의 랜덤성 제어 시드값                  |
| Safe Mode         | 민감 콘텐츠 차단 여부 (활성 시 필터링 적용됨)        |
| Override Endpoint | 기본 API 주소를 대체할 사용자 정의 Endpoint URL |

***

#### 출력값 (Outputs)

| 출력 항목         | 설명                        |
| ------------- | ------------------------- |
| ChatMistralAI | Mistral 모델의 응답 또는 스트리밍 객체 |

***

#### 활용 예시

* 빠른 응답성과 낮은 지연시간이 필요한 챗봇 시스템에 Mistral 모델 활용 (예: 고객 상담 자동화)
* 다수 사용자 대상 콘텐츠 생성 기능(카피라이팅, 요약 등)에서 응답 속도와 비용을 최적화할 때
* 모델 Endpoint를 엔터프라이즈 프록시로 오버라이딩하여 내부망 운영 환경에 맞춰 사용
* GPT 대체 목적의 저비용 고성능 LLM 적용이 필요한 스타트업 SaaS 서비스

***

#### 사용 팁

* **Safe Mode** 활성화 시 일부 응답이 누락될 수 있으므로 필요할 때만 사용하는 것을 권장
* Top Probability 값을 낮게 설정하면 더 일관된 응답 생성이 가능
* **Random Seed**는 테스트 환경에서 재현 가능한 결과를 원할 때 유용함
* **Override Endpoint**는 프록시 서버 또는 지역별 리전 라우팅용으로 활용 가능

***

#### 주의사항

* 모델 이름은 정확히 입력해야 하며, `mistral-tiny` 등 Mistral이 제공하는 모델만 지원됩니다
* Mistral API Key가 Credential에 정확히 등록되어 있어야 하며, 인증 오류 시 연결이 차단됩니다
* Safe Mode와 Endpoint Override는 테스트 후 실제 환경에 맞게 조정해야 함
* Max Output Tokens 및 Streaming 동시 설정 시 출력량 제한에 주의 필요
