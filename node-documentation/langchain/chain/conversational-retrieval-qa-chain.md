# Conversational Retrieval QA Chain

**Conversational Retrieval QA Chain 노드**는 이전 대화 맥락을 유지하면서, 벡터 검색 기반 문서로부터 관련 정보를 찾아 **정확하고 자연스러운 질의응답**을 생성하는 노드입니다.\
질문이 애매하거나 맥락에 의존하는 경우에도, 이전 대화 내용을 바탕으로 질문을 재구성하고 문서 기반으로 답변합니다.

***

### 주요 기능

* 대화 흐름 속에서 **불완전한 질문을 명확한 단일 질문으로 재작성**
* 벡터 검색(Retriever)을 통해 관련 문서 컨텍스트 자동 검색
* 검색된 문서 내용을 기반으로 **정확하고 자연스러운 답변 생성**
* 과거 대화와 질문의 연계를 고려한 QA에 최적화

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-09 170545.png" alt=""><figcaption><p>WindyFlo Conversational Retrieval QA Chain</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-09 170559.png" alt=""><figcaption><p>WindyFlo Conversational Retrieval QA Chain Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                          | 설명                                    | 필수 여부 |
| --------------------------- | ------------------------------------- | ----- |
| **Chat Model**              | 문장 생성 및 재작성에 사용할 언어 모델                | 필수    |
| **Vector Store Retriever**  | 문서 기반 검색 기능. 유사한 문서를 벡터 기반으로 찾아 제공    | 필수    |
| **Memory**                  | 이전 대화를 저장하고 이어받는 구성 요소                | 선택    |
| **Input Moderation**        | 유해 콘텐츠 필터링 기능                         | 선택    |
| **Return Source Documents** | 응답에 참조된 문서 원문을 함께 반환할지 여부 (기본값: 비활성화) | 선택    |

***

### 파라미터 (Parameters)

| 항목                  | 설명                                         |
| ------------------- | ------------------------------------------ |
| **Rephrase Prompt** | 이전 대화 맥락을 기반으로 불완전한 질문을 단독 질문으로 재작성하는 프롬프트 |
| **Response Prompt** | 검색된 문서를 기반으로 최종 응답을 생성하는 프롬프트              |

#### Rephrase Prompt 예시

```
text복사편집Given the following conversation and a follow up question, rephrase the follow up question to be a standalone question.

Chat History:
{chat_history}
Question:
{question}
```

#### Response Prompt 예시

```
text복사편집I want you to act as a document that I am having a conversation with.  
Your name is "AI Assistant." Using the provided context, answer the user’s question to the best of your ability using the resources provided.  
If there is nothing in the context relevant to the question at hand, just say "Hmm, I’m not sure" and stop after that. Refuse to answer any question not about the info.
```

***

### 출력값 (Outputs)

| 출력 항목                              | 설명                      |
| ---------------------------------- | ----------------------- |
| **ConversationalRetrievalQAChain** | 질문 재작성 및 검색 결과 기반 응답 객체 |

***

### 활용 예시

1. **문서 기반 상담 챗봇**
   * 과거 대화에서 "그건 어디에 있어?" 같은 질문에도 정확한 문서를 검색하여 답변
2. **사내 데이터 Q\&A 시스템**
   * 정책 문서, 인사 매뉴얼 등에서 관련 내용을 자동 검색하여 응답 생성
3. **RAG 기반 대화형 어시스턴트**
   * 검색된 컨텍스트에 따라 정확한 정보 제공 및 출처 반환 가능

***

### 사용 팁

* 벡터 스토어는 `In-Memory`, `Redis`, `Weaviate` 등 다양한 유형과 연결 가능
* Memory 설정 시 follow-up 질문을 더 자연스럽게 처리 가능
* `Return Source Documents`를 활성화하면 **출처 투명성 확보**에 유리함

***

### 주의사항

* `Rephrase Prompt`에는 `{chat_history}`와 `{question}` 변수가 반드시 포함되어야 합니다.
* `Response Prompt`에는 `{context}` 변수가 반드시 포함되어야 하며, 이를 누락하면 정상 응답이 불가합니다.
* 문서 벡터화 품질이 낮을 경우 정확한 답변을 얻기 어렵습니다.

***

Conversational Retrieval QA Chain은 WindyFlo에서 **RAG(Retrieval-Augmented Generation) 기반 질의응답을 구현할 수 있는 핵심 노드**입니다.\
문서 검색과 대화의 연결이 중요한 챗봇 서비스에 최적화된 구성입니다.
