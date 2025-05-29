# ChatGoogleVertexAI

ChatGoogleVertexAI 노드는 Google Cloud의 Vertex AI 플랫폼을 통해 Gemini 모델을 호출할 수 있는 Chat Model 노드입니다. 모델 배포와 권한 제어가 통합된 Vertex AI 환경에서 고성능 대화형 LLM을 안정적으로 운영할 수 있습니다.

***

#### 주요 기능

* Google Vertex AI를 통해 Gemini 계열 모델 호출 (예: gemini-1.5-pro)
* Custom Model Name 지정으로 세분화된 모델 제어 가능
* Streaming 응답 방식 및 고급 응답 제어 파라미터 지원
* Temperature, Top-P 설정 등 응답 품질 튜닝 기능 포함
* 이미지 업로드 입력도 선택적으로 허용 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 103609.png" alt=""><figcaption><p>WindyFlo ChatGoogleVertexAI</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 103619.png" alt=""><figcaption><p>WindyFlo ChatGoogleVertexAI Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                  | 설명                                                  | 필수 여부 |
| ------------------- | --------------------------------------------------- | ----- |
| Connect Credential  | Vertex AI에 연결된 서비스 계정 키 또는 API Key (Credential에 등록) | 필수    |
| Model Name          | 사용할 Vertex AI Gemini 모델명 (예: gemini-1.5-pro)        | 필수    |
| Temperature         | 창의성 조절 값 (0.0 \~ 1.0, 기본값: 0.9)                     | 선택    |
| Allow Image Uploads | 이미지 입력 허용 여부                                        | 선택    |

***

#### 파라미터 (Parameters)

| 항목                                  | 설명                                                 |
| ----------------------------------- | -------------------------------------------------- |
| Custom Model Name                   | Vertex AI에 배포된 모델 식별자 (예: gemini-1.5-pro-exp-0801) |
| Streaming                           | 스트리밍 방식 응답 수신 여부 (기본값: true)                       |
| Max Output Tokens                   | 출력 최대 토큰 수                                         |
| Top Probability                     | Top-P 확률 샘플링 값                                     |
| Top Next Highest Probability Tokens | 후보 토큰 수 제한 (예: Top-K 역할)                           |

***

#### 출력값 (Outputs)

| 출력 항목              | 설명                              |
| ------------------ | ------------------------------- |
| ChatGoogleVertexAI | Vertex AI를 통해 반환된 응답 또는 스트리밍 객체 |

***

#### 활용 예시

* 내부 Google Cloud 인프라 내에서 보안 통제된 환경에서 Gemini 모델을 안정적으로 운영
* 모델 버전 및 배포 단위 별 A/B 테스트를 통한 대화 응답 성능 최적화
* 클라우드 기반 업무 자동화 시스템에 Vertex AI 기반 언어 모델 내장
* 고도화된 사내 지식 검색형 챗봇에서 Vertex AI 기반 추론 응답 제공

***

#### 사용 팁

* **Custom Model Name**을 명확히 지정해야 정확한 배포 모델로 연결됩니다
* Streaming 응답을 활성화하면 사용자 응답 체감 속도가 크게 개선됩니다
* Top-P, Temperature 값을 함께 조절해 응답 일관성과 창의성의 균형을 조정할 수 있습니다

***

#### 주의사항

* Vertex AI 콘솔에서 모델이 실제 배포되어 있어야 하며, API 호출 권한이 있는 서비스 계정 키를 사용해야 합니다
* Model Name과 Custom Model Name의 불일치 시 오류 발생 가능
* Gemini 1.5 계열은 비용이 높고 응답 시간이 길 수 있으므로 사전 테스트 권장
* 토큰 수 제한과 네트워크 연결 상태에 따라 예외 상황이 발생할 수 있습니다
