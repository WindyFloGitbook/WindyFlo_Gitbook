# TogetherAI

TogetherAI 노드는 Together 플랫폼의 다양한 오픈소스 LLM 모델을 호출하여 텍스트 생성, 요약, 질의응답 등 생성형 AI 작업을 수행할 수 있도록 합니다. 세부 파라미터를 조정하여 생성 품질과 스타일을 세밀하게 제어할 수 있습니다.

***

### 주요 기능

* Together API 기반 다양한 LLM(OpenChat, LLaMA, Mistral 등) 호출 지원
* Top-k, Top-p, Temperature 등 샘플링 제어 파라미터 제공
* Streaming 기능을 통해 실시간 출력 스트리밍 처리 가능
* Stop Sequence 설정으로 출력 종료 조건 제어 가능
* Additional Parameters를 통한 세부 옵션 전달 가능

<div><figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 134631.png" alt=""><figcaption><p>WindyFlo TogetherAI</p></figcaption></figure> <figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 134638.png" alt=""><figcaption><p>WindyFlo TogetherAI Parameters</p></figcaption></figure></div>

### 입력값 (Inputs)

| 항목                 | 설명                                                                | 필수 여부 |
| ------------------ | ----------------------------------------------------------------- | ----- |
| Connect Credential | Together API Key를 Credential에 등록하여 연결                             | 필수    |
| Model Name         | 호출할 Together 모델의 정확한 이름 (예: `mistralai/Mistral-7B-Instruct-v0.1`) | 필수    |
| Top K              | 상위 K개 토큰 중에서 선택 (예: 50)                                           | 선택    |
| Top P              | 누적 확률 기반 샘플링 값 (0.0 \~ 1.0, 예: 0.7)                               | 선택    |
| Temperature        | 출력 다양성 제어 (0.0 \~ 1.0, 예: 0.7)                                    | 필수    |
| Repeat Penalty     | 반복 억제 계수 (기본값: 1)                                                 | 필수    |
| Streaming          | 출력 결과를 실시간 스트리밍할지 여부 (기본값: false)                                 | 필수    |

***

### 파라미터 (Parameters)

| 항목                    | 설명                                            |
| --------------------- | --------------------------------------------- |
| Max Tokens            | 최대 출력 토큰 수 설정 (예: 512)                        |
| Stop Sequence         | 생성 중단 조건으로 사용하는 문자열 목록 (예: `"AI assistant:"`) |
| Additional Parameters | JSON 형식으로 전달하는 기타 세부 설정값                      |

***

### 출력값 (Outputs)

| 출력 항목      | 설명                          |
| ---------- | --------------------------- |
| TogetherAI | Together 플랫폼으로부터 생성된 텍스트 결과 |

***

### 활용 예시

* OpenChat 또는 Mistral 계열 모델을 활용한 비즈니스 이메일 자동 생성
* LLaMA 기반 모델로 기술문서 요약 자동화
* Streaming 옵션을 사용한 실시간 챗봇 응답 처리
* 다양한 모델 성능 비교를 위한 다중 설정 실험

***

### 사용 팁

* 모델명은 TogetherAI 공식 모델 명세에 따라 정확히 입력해야 합니다.
* Top-k와 Top-p는 동시에 조절하지 말고, 한 가지 방식만 우선 적용해보는 것이 효과적입니다.
* Stop Sequence를 적절히 설정하면 불필요한 출력 길이를 줄일 수 있습니다.
* Additional Parameters에 system prompt, user id 등 모델 특화 입력을 전달할 수 있습니다.

***

### 주의사항

* Connect Credential에 Together API Key를 미리 등록하지 않으면 호출이 불가능합니다.
* 모델 호출 실패는 대부분 Model Name 오탈자 또는 Credential 미등록 문제로 발생합니다.
* 일부 모델은 Streaming 기능을 지원하지 않을 수 있으므로 사전 테스트 필요합니다.
* 요금 정책은 Together 플랫폼 기준에 따르며, 사용량에 따라 과금될 수 있습니다.
