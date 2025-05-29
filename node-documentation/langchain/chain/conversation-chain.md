# Conversation Chain

**Conversation Chain 노드**는 기본적인 챗봇 응답을 구현하기 위한 가장 단순하고 직관적인 대화형 체인 노드입니다.\
대화 기록(Memory)을 유지하면서 지정한 시스템 프롬프트를 기반으로 LLM이 사용자 메시지에 응답합니다.

***

### 주요 기능

* LLM과의 **연속 대화 흐름 유지**
* **지정된 프롬프트와 메모리**를 바탕으로 맥락 기반 응답 생성
* 초보자에게 적합한 **기본형 챗봇 구현 노드**

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-09 170354.png" alt=""><figcaption><p>WindyFlo Conversation Chain</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-09 170406.png" alt=""><figcaption><p>WindyFlo Conversation Chain Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                       | 설명                                    | 필수 여부 |
| ------------------------ | ------------------------------------- | ----- |
| **Chat Model**           | 대화 응답을 생성할 언어 모델 (예: GPT-4, Claude 등) | 필수    |
| **Memory**               | 이전 대화 기록을 저장하고 참조하는 메모리 구성 요소         | 필수    |
| **Chat Prompt Template** | 대화의 스타일이나 맥락을 지정하는 시스템 프롬프트           | 선택    |
| **Input Moderation**     | 유해하거나 부적절한 입력을 필터링하는 기능               | 선택    |

***

### 파라미터 (Parameters)

| 항목                 | 설명                                              |
| ------------------ | ----------------------------------------------- |
| **System Message** | AI의 역할이나 응답 스타일을 지정하는 시스템 프롬프트로, 대화 전 맥락 제공에 사용 |

#### System Message 예시

```
text복사편집The following is a friendly conversation between a human and an AI.  
The AI is talkative and provides lots of specific details from its context.  
If the AI does not know the answer to a question, it truthfully says it does not know.
```

***

### 출력값 (Outputs)

| 출력 항목                 | 설명                     |
| --------------------- | ---------------------- |
| **ConversationChain** | LLM의 응답 메시지 (기억 기반 포함) |

***

### 활용 예시

1. **FAQ 응답 챗봇**
   * 단순한 문답 형태의 고객상담 챗봇에 활용
   * 메모리를 통해 대화 흐름을 유지하면서 반복 질문 방지
2. **퍼스널 챗봇**
   * 프롬프트를 통해 캐릭터 성격이나 톤 설정 가능
   * 지속적인 대화 맥락 유지 기능으로 인간적인 상호작용 제공

***

### 사용 팁

* System Message를 창의적으로 구성하면, 챗봇의 성격(예: 무뚝뚝한 상담원, 상냥한 조교 등)을 쉽게 조절할 수 있습니다.
* Memory는 `BufferMemory`, `SummaryMemory`, `TokenBufferMemory` 등 목적에 따라 선택 가능합니다.
* 이 노드는 Tool 사용 없이 순수 대화 기능에 집중하고자 할 때 유용합니다.

***

### 주의사항

* Tool 실행, 검색 기능 등은 이 노드만으로는 불가능하며, Agent 계열 노드와 조합이 필요합니다.
* 메모리를 설정하지 않으면 매 대화마다 독립적인 응답이 생성되어 맥락 유지가 불가능합니다.
* System Message가 명확하지 않을 경우, AI의 응답 품질이 낮아질 수 있습니다.

***

Conversation Chain은 WindyFlo에서 **기본 챗봇 인터페이스를 빠르게 구현하고 테스트할 수 있는 가장 단순한 대화 체인 노드**입니다.\
빠른 프로토타입 제작이나 실험적 대화 흐름 테스트에 적합합니다.
