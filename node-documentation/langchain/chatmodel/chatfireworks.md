# ChatFireworks

ChatFireworks 노드는 Fireworks.ai 플랫폼에 배포된 다양한 오픈소스 기반 LLM(Llama, Mistral 등)을 호출할 수 있는 Chat Model 노드입니다. 경량화된 인프라에서 고성능 모델을 저비용으로 활용할 수 있어, 빠르고 효율적인 AI 응답 환경을 구축하는 데 적합합니다.

***

#### 주요 기능

* Fireworks.ai 플랫폼의 LLM 호출 기능 지원 (예: Llama, Mistral 등)
* 세부 모델 경로를 직접 입력하여 다양한 모델 활용 가능
* Temperature 조절로 응답 창의성 설정 가능
* Streaming 방식 지원으로 빠른 응답 체감 가능
* 합리적인 비용으로 GPT 대체 모델 운영 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 103309.png" alt=""><figcaption><p>WindyFlo ChatFireworks</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                 | 설명                                                         | 필수 여부 |
| ------------------ | ---------------------------------------------------------- | ----- |
| Connect Credential | Fireworks API Key를 Credential에 등록한 항목                      | 필수    |
| Model              | 호출할 모델의 경로 (예: accounts/fireworks/models/llama-v2-7b-chat) | 필수    |
| Temperature        | 창의성 조절 값 (0.0 \~ 1.0, 기본값: 0.9)                            | 선택    |
| Streaming          | 응답을 스트리밍으로 수신할지 여부 (기본값: true)                             | 선택    |

***

#### 출력값 (Outputs)

| 출력 항목         | 설명                          |
| ------------- | --------------------------- |
| ChatFireworks | Fireworks 모델의 응답 또는 스트리밍 객체 |

***

#### 활용 예시

* Llama 2 기반 모델을 활용한 저비용 챗봇 구축 (GPT 대비 비용 절감 가능)
* 개발자 툴 내에 내장되는 인라인 코드 도우미 기능 구현 시, 빠르고 경량화된 응답 제공
* 사내 업무 자동화 시스템에서 일정 수준의 자연어 응답 기능이 필요한 경우
* 학습용 플랫폼에서 학생 질문에 대해 LLM 기반 응답을 제공하되, 트래픽 비용 최소화가 필요한 환경

***

#### 사용 팁

* Model 필드에는 Fireworks 콘솔에서 제공하는 전체 경로를 정확히 입력해야 정상 작동합니다\
  (예: `accounts/fireworks/models/llama-v2-7b-chat`)
* Temperature를 0.6 이하로 낮추면 더 일관된 응답을 유도할 수 있음
* Fireworks.ai는 다양한 오픈소스 모델을 지원하므로 실험적 모델 사용에 적합함

***

#### 주의사항

* Fireworks API Key가 Credential에 등록되어 있어야 하며, 모델 접근 권한이 부여되어 있어야 합니다
* 모델 경로를 잘못 입력하면 오류가 발생하므로 콘솔에서 정확한 경로 확인 필요
* 일부 모델은 특정 토큰 제한 또는 응답 포맷 제약이 있으므로 문서 확인 필수
* 고빈도 호출 시 요금 청구 방식과 제한 조건을 사전에 파악하고 운영할 것
