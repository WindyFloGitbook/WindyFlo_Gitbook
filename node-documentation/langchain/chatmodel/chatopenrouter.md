# ChatOpenRouter

ChatOpenRouter 노드는 OpenRouter 플랫폼을 통해 다양한 LLM 제공자의 모델(OpenAI, Anthropic, Mistral 등)을 API 하나로 호출할 수 있는 Chat Model 노드입니다. **멀티모델 전략**, **비용 최적화**, **성능 실험**을 동시에 수행할 수 있어 유연한 파이프라인 설계에 적합합니다.

***

#### 주요 기능

* OpenRouter API를 통해 다양한 LLM 공급자의 모델(gpt-3.5, mistral, claude 등) 통합 호출
* 하나의 API 키로 다양한 모델 실험 가능
* Streaming 응답 및 생성 파라미터 설정 가능
* BasePath 수정 및 Proxy 설정을 통한 유연한 환경 구성
* OpenAI 호환 인터페이스 유지

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 131012.png" alt=""><figcaption><p>WindyFlo ChatOpenRouter</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 131022 (1).png" alt=""><figcaption><p>WindyFlo ChatOpenRouter Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                 | 설명                                                             | 필수 여부 |
| ------------------ | -------------------------------------------------------------- | ----- |
| Connect Credential | OpenRouter API Key (Credential에 등록된 값)                         | 필수    |
| Model Name         | 사용할 모델 이름 (예: openai/gpt-3.5-turbo, mistralai/mistral-small 등) | 필수    |
| Temperature        | 응답 창의성 조절 값 (0.0 \~ 1.0, 기본값: 0.9)                             | 선택    |

***

#### 파라미터 (Parameters)

| 항목                | 설명                                                    |
| ----------------- | ----------------------------------------------------- |
| Streaming         | 실시간 응답 스트리밍 (기본값: true)                               |
| Max Tokens        | 생성할 최대 응답 토큰 수                                        |
| Top Probability   | Top-P 기반 확률 샘플링 값                                     |
| Frequency Penalty | 반복 단어 빈도 억제 계수                                        |
| Presence Penalty  | 새로운 주제 등장 유도 계수                                       |
| Timeout           | API 응답 제한 시간(ms)                                      |
| BasePath          | OpenRouter API 경로 (기본값: https://openrouter.ai/api/v1) |
| BaseOptions       | 추가 옵션(JSON 형태 입력)                                     |

***

#### 출력값 (Outputs)

| 출력 항목          | 설명                           |
| -------------- | ---------------------------- |
| ChatOpenRouter | 지정한 LLM 모델로부터의 응답 또는 스트리밍 객체 |

***

#### 활용 예시

* **OpenAI와 Anthropic 모델을 번갈아 테스트**하면서 비용과 품질 비교 실험
* 사용량 급증 시 OpenRouter를 통해 **차단 우회 및 분산 처리**
* 특정 국가에서 차단된 API 대신 OpenRouter 경유로 **모델 연결 유지**
* 가격 대비 성능이 우수한 오픈 모델(Mistral 등)을 파이프라인에 통합

***

#### 사용 팁

* Model Name은 `공급자명/모델명` 형식으로 정확히 입력해야 정상 작동 (예: openai/gpt-3.5-turbo)
* OpenRouter는 다수의 모델을 하나의 API 키로 호출 가능하므로 테스트 자동화에 적합
* Streaming 기능 활성화 시 응답 체감 속도가 개선됨
* BaseOptions 항목에 JSON 형태의 세부 설정을 적용할 수 있음

***

#### 주의사항

* Model Name은 OpenRouter에 등록된 모델 ID 그대로 입력해야 하며, 오타 시 응답 실패
* OpenRouter는 별도 요금 정책을 사용하므로 OpenAI 등과 과금 방식이 다를 수 있음
* 일부 모델은 이미지 입력, 함수 호출 등의 기능을 지원하지 않을 수 있음
* 기업 방화벽 환경에서는 BasePath 및 Proxy 설정 필요
