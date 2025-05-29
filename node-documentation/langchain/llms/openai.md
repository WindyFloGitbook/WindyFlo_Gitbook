# OpenAI

OpenAI 노드는 OpenAI에서 제공하는 Instruct 기반 언어 모델을 API로 호출할 수 있는 노드입니다. GPT-3.5-turbo-instruct, text-davinci 계열 등의 모델을 지원하며, 다양한 생성 파라미터를 통해 출력 품질을 정교하게 제어할 수 있습니다.

***

### 주요 기능

* OpenAI의 Instruct 모델(gpt-3.5-turbo-instruct 등)을 통한 텍스트 생성 기능
* `Temperature`, `Top-p`, `Frequency Penalty` 등 다양한 생성 전략 설정 지원
* 배치 처리와 API 응답 제한 시간(timeout) 등 실무 설정 가능
* WindyFlo 내 다양한 LLM 기반 파이프라인과 연동 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 133920.png" alt=""><figcaption><p>WindyFlo OpenAI</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 133927 (1).png" alt=""><figcaption><p>WindyFlo OpenAI Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                      | 필수 여부 |
| ------------------ | --------------------------------------- | ----- |
| Cache              | 동일 요청 결과를 저장할지 여부                       | 선택    |
| Connect Credential | OpenAI API 키가 등록된 Credential            | 필수    |
| Model Name         | 사용할 모델 이름 (예: `gpt-3.5-turbo-instruct`) | 필수    |
| Temperature        | 생성의 다양성을 조절하는 파라미터 (0 \~ 1, 기본값: 0.7)   | 선택    |

***

### 파라미터 (Parameters)

| 항목                      | 설명                          |
| ----------------------- | --------------------------- |
| Max Tokens              | 출력 최대 토큰 수                  |
| Top Probability (Top-p) | Nucleus sampling 설정값        |
| Best Of                 | 여러 결과 중 가장 적합한 응답 선택        |
| Frequency Penalty       | 반복되는 단어를 줄이기 위한 패널티         |
| Presence Penalty        | 새로운 단어 사용을 유도하는 패널티         |
| Batch Size              | 한 번에 처리할 요청 묶음 크기           |
| Timeout                 | 요청 제한 시간 (ms)               |
| BasePath                | 프록시 서버를 사용하는 경우 지정하는 API 경로 |
| BaseOptions             | 고급 설정이 필요한 경우 JSON 형태로 지정   |

***

### 출력값 (Outputs)

| 출력 항목  | 설명                      |
| ------ | ----------------------- |
| OpenAI | OpenAI로부터 생성된 텍스트 응답 결과 |

***

### 활용 예시

* 특정 지침에 따라 응답을 생성하는 단답형 챗봇 개발 시
* GPT-4처럼 고비용 모델이 아닌 저렴한 instruct 모델로 기획 응답 구성 시
* 고객 응대 문구, 이메일 초안, 기사 요약 등 다양한 지시형 작업
* 프롬프트 기반 API 호출 자동화 파이프라인에 적합

***

### 사용 팁

* `gpt-3.5-turbo-instruct`는 명령형(prompt-to-text) 작업에 특화되어 있어, 일반 대화형 모델보다 정제된 결과를 요구하는 업무에 적합합니다.
* `Temperature`를 0.3 이하로 낮추면 보다 안정적이고 일관된 출력 확보가 가능합니다.
* `Best Of`를 사용할 경우 응답 속도가 느려질 수 있으므로 주의가 필요합니다.
* 내부 프록시나 방화벽 환경에서는 `BasePath`를 반드시 지정해야 API 호출이 성공합니다.

***

### 주의사항

* Instruct 모델은 ChatCompletion API가 아닌 Completion API를 기반으로 하므로, 채팅 기반 파이프라인에는 적합하지 않을 수 있습니다.
* `Best Of` 옵션을 높게 설정하면 요금이 증가할 수 있으므로 제한적으로 사용해야 합니다.
* `Batch Size`는 토큰 수와 조합하여 Rate Limit에 영향을 줄 수 있으므로 실사용 시 적절히 튜닝해야 합니다.
* `gpt-3.5-turbo-instruct`는 일반적인 `gpt-3.5-turbo`와 다르므로 프롬프트 포맷 차이에 유의해야 합니다.
