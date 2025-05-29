# AWS ChatBedrock

AWS ChatBedrock 노드는 Amazon Bedrock을 통해 다양한 LLM(Chat Model)을 호출할 수 있는 인터페이스를 제공합니다. Bedrock에서 지원하는 모델을 선택하여, 프롬프트 입력 기반의 응답 생성을 수행할 수 있습니다. 특히 Anthropic Claude, AI21, Amazon Titan 등 여러 모델 중 선택적으로 사용할 수 있습니다.

#### 주요 기능

* AWS Bedrock 기반 LLM 호출을 지원합니다.
* Region과 Model을 선택하여 원하는 모델 환경을 설정할 수 있습니다.
* 이미지 업로드 사용 여부, 사용자 정의 모델 이름 등 추가 설정이 가능합니다.
* `Streaming`, `Temperature`, `Max Tokens to Sample` 등 주요 파라미터를 조정하여 응답 특성을 제어할 수 있습니다.
* Credential에 등록된 AWS 키를 통해 인증하며, us-east-1 리전을 기본으로 사용합니다.

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 095414.png" alt=""><figcaption><p>WindyFlo AWS ChatBedrock</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 095423.png" alt=""><figcaption><p>WindyFlo AWS ChatBedrock Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                  | 설명                                                | 필수 여부 |
| ------------------- | ------------------------------------------------- | ----- |
| AWS Credential      | AWS Bedrock에 접근할 수 있는 Credential에 등록된 자격 정보       | 필수    |
| Region              | 사용할 AWS 리전(e.g., us-east-1)                       | 필수    |
| Model Name          | 사용할 Bedrock 모델 이름(e.g., anthropic.claude-3-haiku) | 필수    |
| Custom Model Name   | 사용자 지정 모델 명칭(표시용)                                 | 선택    |
| Allow Image Uploads | 이미지 업로드 허용 여부                                     | 선택    |

***

#### 파라미터 (Parameters)

| 항목                   | 설명                                            |
| -------------------- | --------------------------------------------- |
| Streaming            | 응답을 스트리밍 방식으로 받을지 여부 (기본값: 활성화)               |
| Temperature          | 출력 다양성 제어 값. 0.0 \~ 1.0 사이 값 설정 가능 (기본값: 0.7) |
| Max Tokens to Sample | 출력 토큰 수 제한 (기본값: 200)                         |

***

#### 출력값 (Outputs)

| 출력 항목          | 설명                           |
| -------------- | ---------------------------- |
| AWSChatBedrock | AWS Bedrock을 통해 생성된 응답 결과 객체 |

***

#### 활용 예시

* 고객센터 챗봇에 Claude 모델을 연동하여, 고객 문의에 대해 자연스럽고 신뢰도 높은 응답을 제공
* 사내 임직원용 Q\&A 서비스에 Claude 3를 연결해, 정책 문서나 인사 정보를 자연어로 조회 가능하게 구성
* 전자상거래 플랫폼에서 사용자의 질문에 기반한 상품 추천 응답을 실시간으로 생성
* 교육 콘텐츠 플랫폼에서 학생의 질문을 실시간으로 이해하고, 관련 개념을 설명하는 학습 도우미 구현

***

#### 사용 팁

* Token 수 조절을 통해 비용과 응답 시간 최적화 가능
* Streaming을 활성화하면 대화형 UX에서 응답 지연을 줄일 수 있음
* Region, Model Name을 정확히 입력하지 않으면 오류 발생 가능

***

#### 주의사항

* AWS Bedrock 사용을 위해 사전 서비스 신청 및 권한 설정 필요
* 입력된 토큰 수 및 출력 토큰 수에 따라 요금이 발생
* 허용된 모델 외의 Model Name 입력 시 오류 발생
* AWS Credential에 등록된 키가 없을 경우 실행 불가
