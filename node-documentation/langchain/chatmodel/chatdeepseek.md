# ChatDeepseek

ChatDeepseek 노드는 Deepseek사의 고성능 오픈소스 언어 모델을 사용하는 Chat Model 노드입니다. 코드 생성과 수학 연산에 강점을 가지며, 비교적 가벼운 세팅으로 안정적인 성능을 제공합니다.

***

#### 주요 기능

* Deepseek-chat 모델 호출을 통해 대화형 AI 기능 구현
* 코드 작성, 수식 계산, 추론 기반 응답에 적합
* Streaming 모드 지원으로 실시간 응답 제공 가능
* Temperature, Top P, Penalty 등 세부 파라미터 조정 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 131433.png" alt=""><figcaption><p>WindyFlo ChatDeepseek</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 131449.png" alt=""><figcaption><p>WindyFlo ChatDeepseek Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                 | 설명                                 | 필수 여부 |
| ------------------ | ---------------------------------- | ----- |
| Connect Credential | Deepseek API 키 (Credential에 등록된 값) | 필수    |
| Model Name         | 사용할 모델 이름 (예: deepseek-chat)       | 필수    |
| Temperature        | 응답 다양성 조절 값 (0.0 \~ 1.0, 기본값: 0.7) | 선택    |

***

#### 파라미터 (Parameters)

| 항목                | 설명                           |
| ----------------- | ---------------------------- |
| Streaming         | 응답을 스트리밍 방식으로 출력 (기본값: true) |
| Max Tokens        | 최대 생성 토큰 수 (예: 1024)         |
| Top Probability   | Top-p 샘플링 확률 상한값 (예: 0.9)    |
| Frequency Penalty | 같은 단어 반복 빈도에 따른 페널티 (예: 0.1) |
| Presence Penalty  | 새로운 주제 언급 유도 정도 (예: 0.1)     |
| Timeout           | 응답 대기 제한 시간 (ms 단위)          |
| Stop Sequence     | 응답 종료 기준 문자열 설정              |

***

#### 출력값 (Outputs)

| 출력 항목        | 설명                             |
| ------------ | ------------------------------ |
| chatDeepseek | 모델이 생성한 응답 또는 JSON 객체 형태 결과 반환 |

***

#### 활용 예시

* **프로그래밍 보조 봇**: 사용자의 코드 질문에 정확한 파이썬 예시 제공
* **수학 풀이 도우미**: 중등\~고등수학 수준의 서술형 풀이 자동화
* **기술 설명 챗봇**: 개발 문서나 기술 사양서의 자연어 요약
* **시나리오 기반 챗플로우**에 맞춘 응답 제어형 대화 구성

***

#### 사용 팁

* 수학 연산이 많은 시나리오에서는 **Top Probability** 값을 낮게 조절하면 더 정확한 결과 유도 가능
* 코드 응답이 필요한 경우, Stop Sequence에 `"""` 혹은 `AI:` 등을 지정하여 응답 구간을 제어 가능
* Temperature 값을 낮게 설정하면 **정확도 중심 응답**에 유리함

***

#### 주의사항

* Deepseek 모델은 한국어 성능이 상대적으로 낮을 수 있음 → 영어 기반 질문에 적합
* API 키는 유효 기간이 자주 변경될 수 있으므로 사전 확인 필요
* Timeout 설정이 없을 경우, 대규모 응답에서 지연 발생 가능
