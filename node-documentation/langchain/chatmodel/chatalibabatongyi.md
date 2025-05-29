# ChatAlibabaTongyi

ChatAlibabaTongyi 노드는 Alibaba Cloud에서 제공하는 Tongyi Qianwen (通义千问) 계열 모델을 호출하는 Chat Model 노드입니다. 중국 로컬 서비스나 중국어 특화 응답이 필요한 환경에서 유리하며, qwen-plus 모델을 기본으로 사용합니다.

***

#### 주요 기능

* Alibaba Cloud 기반 Tongyi 모델(qwen-plus) 호출 지원
* 중국어 및 중국 내 서비스 특화 대화형 응답 생성
* Streaming 응답 방식 제공
* Temperature 값 조절로 응답의 창의성 제어 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 101911.png" alt=""><figcaption><p>WindyFlo ChatAlibabaTongyi</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                 | 설명                                       | 필수 여부 |
| ------------------ | ---------------------------------------- | ----- |
| Connect Credential | Alibaba Cloud 인증 정보 (Credential에 등록된 항목) | 필수    |
| Model              | 사용할 모델 이름 (현재 고정값: qwen-plus)            | 필수    |
| Temperature        | 창의성 조절 값 (0.0 \~ 1.0, 기본값 예: 0.9)        | 선택    |
| Streaming          | 응답을 스트리밍 방식으로 수신할지 여부 (기본값: 활성화됨)        | 선택    |

***

#### 출력값 (Outputs)

| 출력 항목             | 설명                   |
| ----------------- | -------------------- |
| ChatAlibabaTongyi | 모델 응답 텍스트 또는 스트리밍 객체 |

***

#### 활용 예시

* 중국 로컬 전자상거래 플랫폼의 고객 응대 챗봇에 Tongyi 모델을 적용하여 중국어 자연어 처리 정밀도 향상
* 중화권 사용자 대상의 AI 기반 학습 서비스에서 질문 응답 시스템에 활용
* 중국 내 법률/금융 문서 기반 Q\&A 시스템에 활용하여 현지 언어 및 표현 맥락에 맞춘 정확한 응답 생성
* 한중 다국어 서비스를 제공하는 기업에서, 중국어 대화 기능만 Tongyi 모델로 분리 운영

***

#### 사용 팁

* qwen-plus는 중국어 처리에 특화된 모델로, 한국어나 영어보다는 중국어 데이터 기반에서 성능이 뛰어납니다.
* Temperature를 0.6\~0.8 수준으로 조절하면 응답 품질과 일관성 간 균형을 맞출 수 있습니다.

***

#### 주의사항

* Alibaba Cloud 내 API Key 발급 및 해당 모델(qwen-plus)에 대한 활성화가 필요합니다.
* 현재 모델 선택은 고정(qwen-plus) 상태이며, 변경이 불가능합니다.
* 중국 외 지역에서 호출 시 네트워크 지연 또는 연결 실패 가능성이 존재합니다.
