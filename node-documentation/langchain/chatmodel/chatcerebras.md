# ChatCerebras

ChatCerebras 노드는 Cerebras Systems에서 제공하는 Llama 계열 모델을 호출하는 Chat Model 노드입니다. 대규모 연산 최적화와 고속 응답을 강점으로 하며, 클라우드 기반의 경량·고속 추론용 LLM 서비스를 빠르게 연결할 수 있습니다.

***

#### 주요 기능

* Cerebras의 Llama 기반 모델(llama3.1-8b 등) 호출 가능
* Top-P, Penalty 등 다양한 파라미터를 통한 응답 제어 지원
* Streaming 응답 수신 가능
* BasePath, Timeout 등 고급 설정으로 세밀한 API 제어 가능
* 비용 효율성과 응답 속도에 최적화된 클라우드 LLM 호출 구조

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 102950.png" alt=""><figcaption><p>WindyFlo ChatCerebras</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 103006.png" alt=""><figcaption><p>WindyFlo ChatCerebras Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                 | 설명                                          | 필수 여부 |
| ------------------ | ------------------------------------------- | ----- |
| Connect Credential | Cerebras API Key를 포함한 Credential에 등록된 인증 정보 | 필수    |
| Model Name         | 사용할 모델 이름 (예: llama3.1-8b)                  | 필수    |
| Temperature        | 창의성 조절 값 (0.0 \~ 1.0, 기본값: 0.9)             | 선택    |

***

#### 파라미터 (Parameters)

| 항목                | 설명                                          |
| ----------------- | ------------------------------------------- |
| Streaming         | 응답을 스트리밍으로 받을지 여부 (기본값: true)               |
| Max Tokens        | 출력 최대 토큰 수 제한                               |
| Top Probability   | Top-P 확률 샘플링 값                              |
| Frequency Penalty | 동일 단어 반복 억제 계수 (-2.0 \~ 2.0)                |
| Presence Penalty  | 새로운 주제 유도 계수 (-2.0 \~ 2.0)                  |
| Timeout           | 요청 제한 시간(ms)                                |
| BasePath          | API 호출 경로 (기본값: https://api.cerebras.ai/v1) |
| BaseOptions       | 추가 API 옵션 (JSON 형태)                         |

***

#### 출력값 (Outputs)

| 출력 항목        | 설명                         |
| ------------ | -------------------------- |
| ChatCerebras | Cerebras 모델의 응답 또는 스트리밍 객체 |

***

#### 활용 예시

* 빠른 추론 속도가 필요한 서비스형 API 기반 응답 시스템 구축 (예: 실시간 요약, 답변 생성 등)
* Llama 계열 모델을 활용한 비용 효율형 챗봇 시스템 구축 (OpenAI 대비 저비용 운영 가능)
* 응답 제어 설정이 중요한 사용자 맞춤형 인터랙션 시스템에 적용 (예: 상담, 콘텐츠 추천)
* 사내 보안망 외부에서 API 연동 기반으로 LLM 성능 테스트를 진행하고 싶은 경우

***

#### 사용 팁

* Llama 모델 기반이므로 대규모 모델(gpt-4 등)에 비해 속도가 빠르고 비용이 낮음
* Streaming 활성화 시 응답 체감 속도 향상 가능
* Top-P, Frequency Penalty 등을 함께 조절하면 반복 또는 과도한 응답을 방지할 수 있음

***

#### 주의사항

* Cerebras API 사용을 위해 별도 키 발급 및 사용 권한이 필요합니다
* 모델 이름은 제공된 형식(예: llama3.1-8b)을 그대로 입력해야 하며 변경 불가
* API Timeout, BasePath 등 설정이 잘못될 경우 호출 실패 가능성이 있으므로 반드시 검토할 것
* 고빈도 호출 시 요금 정책과 제한 조건을 사전 확인해야 함
