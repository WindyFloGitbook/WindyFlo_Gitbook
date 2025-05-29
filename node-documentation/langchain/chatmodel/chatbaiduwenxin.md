# ChatBaiduWenxin

ChatBaiduWenxin 노드는 Baidu에서 제공하는 ERNIE Bot 계열 모델(예: ERNIE-Bot-turbo)을 호출하는 Chat Model 노드입니다. 중국 내 법률, 금융, 교육 등 산업별 언어 자원을 기반으로 최적화된 응답을 제공하며, 중화권 특화 서비스에 적합합니다.

***

#### 주요 기능

* Baidu ERNIE Bot 모델 호출 가능 (예: ERNIE-Bot-turbo)
* 중국어 이해 및 표현에 최적화된 응답 생성
* Temperature 설정으로 응답 다양성 제어 가능
* Streaming 방식으로 빠른 응답 수신 가능
* 중국 로컬 시장 대상 챗봇 및 분석 서비스에 활용 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 102708.png" alt=""><figcaption><p>WindyFlo ChatBaiduWenxin</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                 | 설명                                             | 필수 여부 |
| ------------------ | ---------------------------------------------- | ----- |
| Connect Credential | Baidu Cloud API Key를 포함한 Credential에 등록된 인증 정보 | 필수    |
| Model              | 사용할 ERNIE 모델 이름 (예: ERNIE-Bot-turbo)           | 필수    |
| Temperature        | 응답의 창의성 조절 값 (0.0 \~ 1.0, 기본값: 0.9)            | 선택    |
| Streaming          | 응답을 스트리밍 방식으로 수신할지 여부 (기본값: true)              | 선택    |

***

#### 출력값 (Outputs)

| 출력 항목           | 설명                         |
| --------------- | -------------------------- |
| ChatBaiduWenxin | ERNIE 모델 응답 텍스트 또는 스트리밍 객체 |

***

#### 활용 예시

* 중국 내 사용자 대상 고객센터 챗봇에 ERNIE Bot을 적용해 자연스러운 현지 언어 대응
* 중화권 교육 플랫폼에서 학생 질문에 대해 Baidu 모델을 통한 정답 및 개념 설명 제공
* 중국 산업용 기술 문서 기반 Q\&A 시스템 구축 시, Baidu Wenxin 기반의 정확한 정보 제공
* 한중 합작 서비스에서 중국어 전용 AI 응답 기능을 별도로 분리해 운영

***

#### 사용 팁

* Temperature 값을 0.6\~0.8로 설정하면 과도한 창의성 없이 안정적인 응답 생성 가능
* Baidu ERNIE Bot은 산업 특화 도메인에 대한 정밀 응답이 강점이므로 활용 도메인에 맞는 Prompt 구성 추천
* Baidu Cloud 내 콘솔에서 API 사용량 및 요청 속도 제한을 반드시 확인하고 적용

***

#### 주의사항

* Baidu Cloud API Key가 사전에 발급되어 있고, ERNIE 서비스 사용 권한이 설정되어 있어야 합니다
* 중국 외 지역에서는 API 호출 지연 또는 연결 실패 가능성이 존재하므로, 네트워크 상태에 주의가 필요합니다
