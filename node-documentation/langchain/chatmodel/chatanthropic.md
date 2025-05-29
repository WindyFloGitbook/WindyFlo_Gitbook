# ChatAnthropic

ChatAnthropic 노드는 Anthropic의 Claude 계열 모델을 호출하는 Chat Model 노드입니다. 윤리적 설계와 맥락 이해 능력이 뛰어난 Claude 모델을 활용해 복잡한 사용자 질문에 대해 신뢰도 높은 응답을 생성할 수 있습니다.

***

#### 주요 기능

* Claude 1\~3 계열 모델 호출 가능 (예: claude-3-opus)
* 다양한 응답 제어 파라미터 지원 (Top-K, Top-P, Budget Tokens 등)
* Streaming 응답 수신 방식 제공
* 이미지 업로드 지원 (옵션 설정)
* Extended Thinking 기능으로 응답 품질 향상 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 102130.png" alt=""><figcaption><p>WindyFlo ChatAnthropic</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 102141.png" alt=""><figcaption><p>WindyFlo ChatAnthropic Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                  | 설명                                      | 필수 여부 |
| ------------------- | --------------------------------------- | ----- |
| Connect Credential  | Anthropic API 키 등 Credential에 등록된 인증 정보 | 필수    |
| Model Name          | 사용할 Claude 모델 이름 (예: claude-3-haiku)    | 필수    |
| Temperature         | 창의성 조절 값 (0.0 \~ 1.0, 기본값 예: 0.9)       | 선택    |
| Allow Image Uploads | 이미지 업로드 허용 여부                           | 선택    |

***

#### 파라미터 (Parameters)

| 항목                | 설명                                        |
| ----------------- | ----------------------------------------- |
| Streaming         | 응답을 스트리밍으로 받을지 여부 (기본값: true)             |
| Max Tokens        | 출력 최대 토큰 수                                |
| Top P             | 확률 기반 응답 다양성 제어 (0.0 \~ 1.0)              |
| Top K             | 상위 K개 토큰 중에서 샘플링 (예: 40)                  |
| Extended Thinking | 심층 사고 활성화 여부 (일반적으로 응답 품질 향상, 처리시간 증가 가능) |
| Budget Tokens     | 응답 생성에 사용할 최대 토큰 예산 (예: 1024)             |

***

#### 출력값 (Outputs)

| 출력 항목         | 설명                             |
| ------------- | ------------------------------ |
| ChatAnthropic | Claude 모델의 응답 결과 또는 스트리밍 응답 객체 |

***

#### 활용 예시

* 윤리성 검토가 필요한 챗봇 서비스에서 Claude 모델을 활용하여 민감한 질문에 신중하고 균형 잡힌 응답 생성
* 고도화된 문서 요약 기능이 필요한 기업에서 보고서 요약 자동화에 Claude 모델 적용
* 대화형 교육 플랫폼에서 학생의 주관식 질문에 논리적이고 이해 중심의 답변을 제공
* 법률 자문, 윤리 상담 등 분야에서 보다 인간적인 판단 기반의 응답이 필요한 서비스에 Claude 도입

***

#### 사용 팁

* **Extended Thinking** 옵션을 활성화하면 문맥 이해와 판단력이 더 필요한 질문에 대해 더 깊이 있는 답변을 생성할 수 있음
* **Budget Tokens** 값을 줄이면 응답 속도가 빨라지고 비용 절감 가능, 늘리면 응답 품질 향상
* Top-K, Top-P, Temperature 세 값을 함께 조절해 다양한 스타일의 응답 실험 가능

***

#### 주의사항

* Model Name은 Anthropic에서 발급받은 정확한 모델 ID를 사용해야 함
* Extended Thinking을 켜면 처리 시간이 증가하며, 비용이 더 많이 소모될 수 있음
* Budget Tokens가 너무 낮으면 응답이 중단되거나 불완전하게 출력될 수 있음
* Claude 3 계열은 고성능이지만 요금이 높으므로 사용 시 요금 정책을 반드시 확인할 것
