# ChatIBMWatsonx

ChatIBMWatsonx 노드는 IBM의 AI 플랫폼인 Watsonx에 배포된 LLM 모델을 호출하는 Chat Model 노드입니다. 특히 기업 환경에 적합한 보안과 컴플라이언스 기반에서 Mistral 등 다양한 오픈 모델을 안정적으로 운용할 수 있습니다.

***

#### 주요 기능

* IBM Watsonx 플랫폼에 등록된 모델 호출 가능 (예: mistralai/mistral-large)
* Temperature, Top-P, Penalty 등 다양한 생성 제어 파라미터 제공
* Streaming 모드를 통한 실시간 응답 가능
* 기업용 환경에 최적화된 IBM의 AI 인프라를 기반으로 운영

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 105320.png" alt=""><figcaption><p>WindyFlo ChatIBMWatsonx</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 105333.png" alt=""><figcaption><p>WindyFlo ChatIBMWatsonx Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                 | 설명                                                     | 필수 여부 |
| ------------------ | ------------------------------------------------------ | ----- |
| Connect Credential | IBM Cloud API Key 또는 Watsonx 인증 정보 (Credential에 등록된 값) | 필수    |
| Model              | 사용할 모델 경로 (예: mistralai/mistral-large)                 | 필수    |
| Temperature        | 창의성 조절 값 (0.0 \~ 1.0, 기본값: 0.9)                        | 선택    |

***

#### 파라미터 (Parameters)

| 항목                | 설명                                |
| ----------------- | --------------------------------- |
| Streaming         | 응답을 스트리밍 방식으로 수신할지 여부 (기본값: true) |
| Max Tokens        | 출력 최대 토큰 수                        |
| Frequency Penalty | 동일 단어 반복 억제 계수                    |
| Presence Penalty  | 새로운 주제 유도 계수                      |
| Top P             | 확률 기반 응답 다양성 제어 값 (예: 0.1 \~ 1.0) |
| N                 | 응답 후보 개수 (기본값: 1)                 |
| Log Probs         | 로그 확률값 반환 여부 (디버깅용)               |

***

#### 출력값 (Outputs)

| 출력 항목          | 설명                          |
| -------------- | --------------------------- |
| ChatIBMWatsonx | Watsonx 기반 모델 응답 또는 스트리밍 객체 |

***

#### 활용 예시

* **금융, 제조, 헬스케어 등 규제가 요구되는 산업 환경**에서 안전하게 LLM을 도입할 때
* IBM 클라우드 기반 데이터와 연계한 문서 생성, 보고서 요약, 회의록 정리 등에 LLM 활용
* 보안 및 신뢰성이 중요한 기업용 챗봇 또는 자동화 응답 시스템에 적용
* Mistral 모델 기반의 대화형 AI 서비스를 Watsonx 환경에서 안정적으로 테스트 및 운영

***

#### 사용 팁

* **Presence Penalty**와 **Frequency Penalty**를 함께 조정하면 응답 중복이나 새로운 주제 전환을 유도 가능
* **Top P**를 낮게 설정하면 더 집중된 응답을 얻을 수 있으나 다양성이 낮아질 수 있음
* **N**을 2 이상으로 설정하면 다양한 후보 응답을 비교하거나 A/B 테스트에 활용 가능

***

#### 주의사항

* Watsonx에 등록된 모델만 호출 가능하며, 사전에 배포된 모델 ID를 정확히 입력해야 합니다
* Credential에 등록된 인증 키가 올바르지 않으면 호출이 실패하거나 인증 오류가 발생할 수 있음
* 로그 확률(Log Probs)은 일반 응답에는 불필요하며 디버깅 또는 분석 목적일 때만 활성화 권장
* 토큰 사용량에 따라 비용이 발생하므로 Max Tokens 설정 시 예산을 고려해야 함
