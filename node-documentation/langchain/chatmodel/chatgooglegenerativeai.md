# ChatGoogleGenerativeAI

ChatGoogleGenerativeAI 노드는 Google Cloud 기반의 Gemini 계열 모델(Google Generative AI)을 호출하는 Chat Model 노드입니다. 다중 모달 입력, 빠른 응답 속도, 고도화된 대화형 추론 기능을 바탕으로 다양한 비즈니스 환경에서 활용 가능합니다.

***

#### 주요 기능

* Google Gemini(Pro, 2.5 등) 계열 모델 호출 기능 제공
* Temperature 조절을 통한 응답 스타일 제어 가능
* 이미지 업로드 기능 지원 (선택적 활성화)
* Google Cloud 기반 인증 연동 구조로 보안성 및 확장성 확보
* 고도화된 멀티턴 대화 및 추론형 응답 처리에 적합

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 103425.png" alt=""><figcaption><p>WindyFlo ChatGoogleGenerativeAI</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                  | 설명                                                               | 필수 여부 |
| ------------------- | ---------------------------------------------------------------- | ----- |
| Connect Credential  | Google Cloud API Key 또는 서비스 계정 키(Credential에 등록된 값)              | 필수    |
| Model Name          | 사용할 Google Generative AI 모델 이름 (예: gemini-pro, gemini-1.5-pro 등) | 필수    |
| Temperature         | 응답 창의성 조절 값 (0.0 \~ 1.0, 기본값 예: 0.9)                             | 선택    |
| Allow Image Uploads | 이미지 업로드 허용 여부 (텍스트+이미지 입력이 필요한 경우 활성화)                           | 선택    |

***

#### 파라미터 (Parameters)

| 항목                                  | 설명                                                        |
| ----------------------------------- | --------------------------------------------------------- |
| Custom Model Name                   | Google Vertex AI에서 생성된 배포 ID (예: gemini-1.5-pro-exp-0801) |
| Streaming                           | 응답을 스트리밍 방식으로 받을지 여부 (기본값: true)                          |
| Max Output Tokens                   | 생성할 최대 응답 토큰 수                                            |
| Top Probability                     | Top-P (확률 기반 응답 다양성 조절)                                   |
| Top Next Highest Probability Tokens | Top-K와 유사한 역할의 후보 토큰 제한                                   |
| Harm Category                       | 유해 콘텐츠 범주 (예: Harassment, Violence 등)                     |
| Harm Block Threshold                | 해당 범주 차단 임계값 (예: Low, Medium, High 등)                     |

***

#### 출력값 (Outputs)

| 출력 항목                  | 설명                          |
| ---------------------- | --------------------------- |
| ChatGoogleGenerativeAI | Google Gemini 응답 또는 스트리밍 객체 |

***

#### 활용 예시

* 다중 입력(텍스트+이미지)에 기반한 고객 문의 응대 시스템 구현
* 기업 내부 문서 기반의 고도화된 검색형 Q\&A 챗봇 설계&#x20;
* 영상 콘텐츠 제작팀의 아이디어 브레인스토밍 및 스크립트 생성 보조
* 멀티턴 대화가 필요한 학습/튜터링 서비스에 Gemini 기반 대화형 AI 적용

***

#### 사용 팁

* Gemini 2 시리즈는 문맥 유지 능력이 강력하므로, 긴 대화 기반의 시나리오에 적합
* Temperature는 0.3\~0.7 사이에서 안정적인 비즈니스 응답을 생성하는 데 유리함
* Allow Image Uploads 옵션을 켜면 이미지 인식 기반 질문 처리가 가능하지만, 처리 시간이 증가할 수 있음

***

#### 주의사항

* Google Cloud 프로젝트에 Gemini API가 활성화되어 있어야 하며, 권한이 부여된 키를 Credential에 등록해야 함
* Model Name은 정확한 배포 모델명을 입력해야 하며, 미지원 모델명을 입력하면 오류 발생
* Gemini 2.5 계열은 응답 품질이 높은 대신 처리 비용 및 시간도 높을 수 있으므로 요금 정책 확인 필요
* 이미지 업로드를 사용할 경우, 입력 데이터 포맷과 크기에 대한 제한 사항을 반드시 확인할 것
