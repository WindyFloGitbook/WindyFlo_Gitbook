# Azure ChatOpenAI

Azure ChatOpenAI 노드는 Microsoft Azure 인프라를 통해 OpenAI의 GPT 모델을 호출하는 Chat Model 노드입니다. 기업 보안 정책에 따라 OpenAI API 직접 사용이 제한된 환경에서도 GPT 기능을 안전하게 활용할 수 있습니다.

***

#### 주요 기능

* Azure OpenAI 서비스를 통해 GPT 계열 모델 호출 가능
* Temperature, Penalty 등 다양한 응답 제어 옵션 제공
* 이미지 업로드 허용 및 해상도 설정 가능
* Reasoning Effort 설정으로 응답 품질 수준 조정
* 기업 환경에 적합한 API 인증 및 Endpoint 구성 지원

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 101433.png" alt=""><figcaption><p>WindyFlo Azure ChatOpenAI</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 101453.png" alt=""><figcaption><p>WindyFlo Azure ChatOpenAI Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                  | 설명                                              | 필수 여부 |
| ------------------- | ----------------------------------------------- | ----- |
| Connect Credential  | Azure에 등록된 OpenAI 리소스 접근용 Credential에 등록된 값     | 필수    |
| Model Name          | 사용할 Azure OpenAI 모델명 (예: gpt-35-turbo, gpt-4 등) | 필수    |
| Temperature         | 창의성 조절 값 (0.0 \~ 1.0, 기본값 예: 0.9)               | 선택    |
| Allow Image Uploads | 이미지 업로드 허용 여부                                   | 선택    |

***

#### 파라미터 (Parameters)

| 항목                | 설명                                  |
| ----------------- | ----------------------------------- |
| Max Tokens        | 출력할 최대 토큰 수 제한                      |
| Streaming         | 응답을 스트리밍으로 수신할지 여부 (기본값: true)      |
| Top Probability   | Top-P 확률 샘플링 값 (예: 0.9)             |
| Frequency Penalty | 동일 단어 반복 감소 계수 (-2.0 \~ 2.0)        |
| Presence Penalty  | 새로운 주제 유도 계수 (-2.0 \~ 2.0)          |
| Timeout           | 응답 대기 시간 제한 (ms 단위)                 |
| BasePath          | 사용자 정의 Endpoint 주소                  |
| BaseOptions       | 추가 API 옵션 (JSON 객체 형태)              |
| Image Resolution  | 이미지 응답 해상도 설정 (Low / Medium / High) |
| Reasoning Effort  | 응답 논리 수준 설정 (Low / Medium / High)   |

***

#### 출력값 (Outputs)

| 출력 항목           | 설명                   |
| --------------- | -------------------- |
| AzureChatOpenAI | 모델 응답 텍스트 또는 스트리밍 객체 |

***

#### 활용 예시

* 금융기업 내부 시스템에서 민감한 데이터를 다루며, Azure 보안 인증을 통과한 GPT 모델로 상담 업무 자동화
* 교육기관 LMS 시스템에서 GPT-4 기반 학습 질문 응답 챗봇을 Azure 환경에 탑재하여 운영
* 대기업 고객센터에서 Azure OpenAI를 통해 영업 문서 요약 및 맞춤형 답변 생성 자동화
* 공공기관 내 보안망 환경에서도 사내 문서 기반 Q\&A 서비스를 안전하게 구현

***

#### 사용 팁

* **Image Resolution**을 "Low"로 설정하면 응답 속도가 빨라지고 비용이 절감됩니다.
* **Reasoning Effort**를 "High"로 설정 시 논리적인 응답이 가능하지만 응답 시간이 늘어날 수 있습니다.
* BasePath를 설정하면 Azure에서 커스텀 도메인/엔드포인트를 사용할 수 있습니다.

***

#### 주의사항

* Azure 리소스에 OpenAI 서비스가 사전에 설정되어 있어야 하며, API 키와 모델 배포 설정이 완료돼야 합니다.
* 모델 이름은 Azure에서 배포한 Deployment 이름과 일치해야 하며, 단순 모델명(gpt-4 등)이 아님에 주의해야 합니다.
* GPT-4 모델 사용 시 처리 지연이 발생할 수 있으며, 높은 Reasoning Effort와 함께 사용할 경우 더욱 증가합니다.
* 일부 설정값(예: Presence Penalty)이 과도하게 높으면 응답이 비정상적으로 동작할 수 있습니다.
