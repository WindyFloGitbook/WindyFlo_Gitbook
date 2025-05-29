# Vectara QA Chain

**Vectara QA Chain** 노드는 Vectara 벡터스토어와 연동하여, 사용자의 질문에 대해 요약 기반 응답을 생성하는 고급 QA 체인 노드입니다.\
Vectara가 제공하는 다양한 Summarizer 모델을 선택할 수 있으며, 응답 언어 및 결과 개수도 자유롭게 설정할 수 있습니다.

***

### 주요 기능

* Vectara 기반 문서 검색 및 요약 응답
* 다양한 GPT 기반 Summarizer 모델 선택 가능
* 응답 언어와 최대 요약 결과 개수 설정 기능

***

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-09 174531.png" alt=""><figcaption><p>WindyFlo Vectara QA Chain</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                     | 설명                             | 필수 여부 |
| ---------------------- | ------------------------------ | ----- |
| Vectara Store          | 검색 대상이 되는 Vectara 벡터스토어 구성 요소  | 필수    |
| Input Moderation       | 유해하거나 부적절한 입력을 필터링하는 기능        | 선택    |
| Summarizer Prompt Name | 요약에 사용할 Summarizer 모델 이름       | 필수    |
| Response Language      | 응답 언어 (예: English, Japanese 등) | 선택    |
| Max Summarized Results | 요약에 사용할 최대 문서 개수               | 필수    |

**Summarizer Prompt Name 선택 예시**

* `vectara-summary-ext-v1.2.0 (gpt-3.5-turbo)`
* `vectara-experimental-summary-ext-2023-small (gpt-3.5-turbo)`
* `vectara-summary-ext-v1.3.0 (gpt-4.0)`
* `vectara-experimental-summary-ext-2023-med (gpt-4.0)`

***

#### 파라미터 (Parameters)

| 항목                     | 설명                                             |
| ---------------------- | ---------------------------------------------- |
| Summarizer Prompt Name | Vectara에서 제공하는 GPT 기반 요약기 선택 (정확도 및 응답 품질에 영향) |
| Max Summarized Results | 응답에 포함할 최대 문서 개수 (기본값: 7)                      |
| Response Language      | 요약 응답 결과의 언어를 지정 (예: English)                  |

***

#### 출력값 (Outputs)

| 출력 항목          | 설명                        |
| -------------- | ------------------------- |
| VectaraQAChain | 요약된 응답 결과 텍스트 (LLM 응답 형식) |

***

### 활용 예시

* 방대한 문서 기반에서 신속한 요약 답변 제공
* 기업 FAQ 시스템에서 실시간 요약형 응답 제공
* Vectara 문서에 기반한 Q\&A 인터페이스 구현

***

### 사용 팁

* GPT-4 기반 Summarizer를 사용하면 정확도는 높지만, 속도는 느릴 수 있습니다.
* `Max Summarized Results` 값이 너무 높으면 응답이 장황해질 수 있습니다.
* Vectara Store 구성 시 적절한 필터링 조건을 함께 설정하면 더 정교한 검색 가능

***

### 주의사항

* Vectara QA Chain은 **Vectara Store**가 반드시 설정되어 있어야 작동합니다.
* Summarizer 모델 이름을 정확히 입력해야 에러 없이 응답이 생성됩니다.
* 해당 노드는 GPT 기반 Summarizer와만 연동되며, Vectara 사용자 계정이 필요할 수 있습니다.
* WindyFlo에서는 `Vectara QA Chain`을 다른 대화형 체인(`Conversation Chain`, `LLM Chain`)과 조합하여 응답 품질을 향상시킬 수 있습니다.
