# ChatXAI

ChatXAI 노드는 X(Twitter)의 자체 언어 모델인 **Grok**을 호출할 수 있는 Chat Model 노드입니다. SNS 기반 데이터에 특화된 답변 성향과 빠른 트렌드 반응력을 바탕으로, 실시간 정보 대응이 중요한 챗봇이나 분석 워크플로우에 활용됩니다.

***

#### 주요 기능

* X(Twitter)의 Grok LLM을 API 형태로 호출 가능
* 실시간 응답이 가능한 Streaming 지원
* Temperature, Max Tokens 등 주요 생성 옵션 설정 가능
* 트렌드, 짧은 질의, SNS 톤에 특화된 응답 제공

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 131312.png" alt=""><figcaption><p>WindyFlo ChatXAI</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 131321.png" alt=""><figcaption><p>WindyFlo ChatXAI Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                 | 설명                                        | 필수 여부 |
| ------------------ | ----------------------------------------- | ----- |
| Connect Credential | X API 토큰 또는 Grok 인증 키 (Credential에 등록된 값) | 필수    |
| Model              | 사용할 Grok 모델 명칭 (예: grok-beta)             | 필수    |
| Temperature        | 응답 다양성 조절 값 (0.0 \~ 1.0, 기본값: 0.9)        | 선택    |

***

#### 파라미터 (Parameters)

| 항목         | 설명                               |
| ---------- | -------------------------------- |
| Streaming  | 응답을 스트리밍 방식으로 출력 (기본값: true)     |
| Max Tokens | 최대 생성 토큰 수 (두 개 필드 존재, 추후 정리 필요) |

***

#### 출력값 (Outputs)

| 출력 항목   | 설명                           |
| ------- | ---------------------------- |
| ChatXAI | Grok 모델로부터 반환된 응답 또는 스트리밍 객체 |

***

#### 활용 예시

* **SNS 자동화 봇**에서 최신 트렌드 대응형 답변 생성
* 실시간 이슈를 반영한 **감성 분석** 파이프라인 구성
* 기업 SNS 채널의 고객 응대용 **SNS 어조 챗봇** 개발
* 뉴스/트렌드 기반 콘텐츠 초안 자동 생성 및 편집

***

#### 사용 팁

* Grok 모델은 일반적인 LLM보다 **짧고 임팩트 있는 응답**에 특화되어 있음
* Temperature를 높이면 더 재치 있는 스타일의 문장이 생성됨
* 동일한 Max Tokens 항목이 2개 존재하므로 값 입력 시 혼동 주의

***

#### 주의사항

* Grok은 현재 베타 모델이므로 응답 일관성, 품질이 다소 유동적일 수 있음
* 트렌드 기반 데이터셋 특성상 **사실 기반 질문에는 부정확한 응답**이 생성될 수 있음
* X API 인증 키 정책은 수시로 변경되므로 유효성 사전 확인 필요
* Max Tokens 항목이 두 개로 중복되어 있어, UI 업데이트 전까지 설정 시점 주의 요망
