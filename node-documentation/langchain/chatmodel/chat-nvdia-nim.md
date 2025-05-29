# Chat Nvdia NIM

ChatNvdiaNIM 노드는 NVIDIA의 NIM(NVIDIA Inference Microservices) 플랫폼을 통해 Microsoft, Mistral, Meta 등 다양한 파트너사의 LLM을 호출하는 Chat Model 노드입니다. 고성능 추론 인프라 위에서 다수의 모델을 API 형태로 빠르게 활용할 수 있습니다.

***

#### 주요 기능

* NIM 플랫폼에 등록된 다양한 LLM 모델 호출 가능 (예: microsoft/phi-3-mini-4k-instruct)
* Temperature, Top-P 등 응답 생성 제어 옵션 지원
* Streaming 응답 지원
* NVIDIA API 기반으로 신뢰성 높은 추론 처리 가능
* Base Options를 통한 확장 설정 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 112057.png" alt=""><figcaption><p>WindyFlo ChatNvdiaNIM</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 112107.png" alt=""><figcaption><p>WindyFlo ChatNvdiaNIM Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                 | 설명                                                                                               | 필수 여부 |
| ------------------ | ------------------------------------------------------------------------------------------------ | ----- |
| Connect Credential | NVIDIA NGC API Key 또는 NIM 인증 키 (Credential에 등록된 값)                                               | 필수    |
| Model Name         | 호출할 모델 이름 (예: microsoft/phi-3-mini-4k-instruct 등 NIM 등록 모델)                                      | 필수    |
| Temperature        | 응답 창의성 조절 값 (0.0 \~ 1.0, 기본값: 0.9)                                                               | 선택    |
| Base Path          | NIM API Endpoint (예: [https://integrate.api.nvidia.com/v1](https://integrate.api.nvidia.com/v1)) | 필수    |

***

#### 파라미터 (Parameters)

| 항목                | 설명                                |
| ----------------- | --------------------------------- |
| Streaming         | 응답을 스트리밍 방식으로 받을지 여부 (기본값: true)  |
| Max Tokens        | 생성할 최대 응답 토큰 수                    |
| Top Probability   | Top-P 확률 기반 샘플링 값                 |
| Frequency Penalty | 중복 단어 억제 계수                       |
| Presence Penalty  | 새로운 주제 유도 계수                      |
| Timeout           | 응답 제한 시간 (ms)                     |
| Base Options      | 추가 설정 옵션 (JSON 형식으로 key-value 전달) |

***

#### 출력값 (Outputs)

| 출력 항목        | 설명                       |
| ------------ | ------------------------ |
| ChatNvdiaNIM | 선택한 모델로부터의 응답 또는 스트리밍 객체 |

***

#### 활용 예시

* NVIDIA 인프라 기반으로 안정성과 성능을 확보한 **엔터프라이즈 대화형 서비스** 개발
* **Microsoft Phi-3** 모델을 활용한 경량 고속 응답 시스템 구현
* Mistral, Meta 등 오픈 모델을 단일 플랫폼에서 통합 운영하는 멀티모델 챗봇 구성
* GPU 서버 없이도 고성능 LLM 추론 기능을 **API 형태**로 활용하고 싶은 스타트업/SMB 대상 서비스 구축

***

#### 사용 팁

* 모델 이름은 NIM에서 제공하는 **정확한 식별자**를 사용해야 하며 사전 확인 필수
* `Base Options` 필드는 JSON 형식으로 다양한 실험적 파라미터나 확장 설정 전달에 활용 가능
* Streaming 모드는 UX를 개선하는 데 효과적이며, 특히 프론트엔드 실시간 응답에 적합
* Top-P와 Temperature를 함께 조절하여 창의성과 일관성 사이 밸런스를 조정할 수 있음

***

#### 주의사항

* Connect Credential은 NVIDIA NGC 계정에서 생성된 유효한 키여야 하며, 권한이 부족할 경우 인증 오류 발생
* 지정된 Base Path가 정확하지 않으면 연결 실패 발생
* 사용 가능한 모델 목록은 NIM 플랫폼 계정 유형에 따라 제한될 수 있음
* Base Options 활용 시 JSON 구조 오류가 발생하지 않도록 주의 필요
