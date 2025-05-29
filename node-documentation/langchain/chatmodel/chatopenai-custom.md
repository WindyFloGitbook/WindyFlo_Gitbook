# ChatOpenAI Custom

ChatOpenAI-Custom 노드는 OpenAI에서 **Fine-tune한 전용 모델**을 호출하는 Chat Model 노드입니다. 특정 업무 목적이나 도메인에 맞게 학습된 GPT-3.5 기반 커스텀 모델을 활용하여, **정확도 높은 특화 응답 생성**이 가능합니다.

***

#### 주요 기능

* OpenAI API를 통해 Fine-tuned GPT-3.5 모델 호출 지원
* 특정 문서, 서비스 문체, 업무 규칙에 맞춘 맞춤형 응답 제공
* 일반 ChatOpenAI와 동일한 파라미터 제어 기능 지원
* Streaming 모드 및 고급 샘플링 옵션 사용 가능
* BasePath를 통해 API 라우팅 유연성 확보

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 113001.png" alt=""><figcaption><p>WindyFlo ChatOpenAI Custom</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 113011.png" alt=""><figcaption><p>WindyFlo ChatOpenAI Custom Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                 | 설명                                                           | 필수 여부 |
| ------------------ | ------------------------------------------------------------ | ----- |
| Connect Credential | OpenAI API Key (Credential에 등록된 값)                           | 필수    |
| Model Name         | Fine-tuned 모델 ID (예: ft:gpt-3.5-turbo:org-id:custom\_suffix) | 필수    |
| Temperature        | 창의성 조절 값 (0.0 \~ 1.0, 기본값: 0.9)                              | 선택    |

***

#### 파라미터 (Parameters)

| 항목                | 설명                                  |
| ----------------- | ----------------------------------- |
| Streaming         | 스트리밍 응답 여부 (기본값: true)              |
| Max Tokens        | 생성할 최대 응답 토큰 수                      |
| Top Probability   | Top-P 기반 확률 샘플링 값                   |
| Frequency Penalty | 반복 단어 빈도 억제 계수                      |
| Presence Penalty  | 새로운 주제 등장 유도 계수                     |
| Timeout           | API 응답 제한 시간(ms)                    |
| BasePath          | OpenAI API 대체 경로 (프록시나 방화벽 우회 시 활용) |
| BaseOptions       | 추가 옵션(JSON 형태 입력)                   |

***

#### 출력값 (Outputs)

| 출력 항목             | 설명                              |
| ----------------- | ------------------------------- |
| ChatOpenAI-Custom | Fine-tuned 모델로부터의 응답 또는 스트리밍 객체 |

***

#### 활용 예시

* **고객지원 팀용 GPT**: 특정 브랜드 말투, 답변 정책을 학습시켜 통일된 상담 자동화
* **법률/회계/의료 등 특수 도메인 대응 봇**: 용어와 규칙 기반 응답 생성
* **사내 문서 FAQ 기반 응답**: RAG 없이도 높은 일관성 확보
* **서비스 설명 전용 GPT**: 기업 제품/서비스 설명 응답 전용 챗봇 구축

***

#### 사용 팁

* Model Name은 OpenAI의 Fine-tune 완료 후 부여되는 ID를 정확히 입력해야 함
* 일반 GPT보다 훈련된 데이터의 **응답 패턴을 잘 따르므로**, 지침 기반 사용에 적합
* Prompt 프레임은 훈련 당시의 템플릿과 유사하게 유지해야 성능 극대화 가능
* BaseOptions 필드로 응답 포맷이나 사용자 지정 조건을 추가할 수 있음

***

#### 주의사항

* Fine-tuned 모델은 GPT-3.5-turbo 기반으로만 가능 (GPT-4 Fine-tune 불가)
* 모델 호출 시 별도 요금이 적용되며, fine-tuning 비용과는 별개
* 훈련 데이터와 다른 유형의 질문에는 예상치 못한 응답이 생성될 수 있음
* API 호출량이 많을 경우 rate limit 이슈가 발생할 수 있음
