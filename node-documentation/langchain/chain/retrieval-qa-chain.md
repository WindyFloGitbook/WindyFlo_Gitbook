# Retrieval QA Chain

**Retrieval QA Chain** 노드는 사용자 질문에 대해 벡터스토어 기반 문서를 검색하고, 해당 결과를 바탕으로 언어 모델이 응답을 생성하는 질의응답용 체인입니다.\
RAG(Retrieval-Augmented Generation) 방식의 가장 기본 구조로, 단일 벡터 리트리버와 언어 모델로 간결하게 구성됩니다.

***

### 주요 기능

* 사용자 질문을 기반으로 문서 벡터스토어에서 관련 정보를 검색
* 검색된 문서를 컨텍스트로 사용하여 언어 모델이 답변 생성
* 간단한 RAG 구현 시 가장 기본적인 구성

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-09 174047.png" alt=""><figcaption><p>WindyFlo Retrieval QA Chain</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                         | 설명                                                         | 필수 여부 |
| -------------------------- | ---------------------------------------------------------- | ----- |
| **Language Model**         | 검색된 컨텍스트를 바탕으로 응답을 생성할 LLM (예: GPT, Claude 등)              | 필수    |
| **Vector Store Retriever** | 질문과 관련된 문서를 검색하는 리트리버 (예: In-Memory Vector Store, Redis 등) | 필수    |
| **Input Moderation**       | 입력값에 대한 유해 콘텐츠 필터링 기능 (ON/OFF)                             | 선택    |

※ `Vector Store Retriever`는 `InMemory Vector Store`, `Redis Embeddings Cache` 등과 연결 가능

***

### 출력값 (Outputs)

| 항목                   | 설명                        |
| -------------------- | ------------------------- |
| **RetrievalQAChain** | 검색된 문서를 기반으로 생성된 응답 (텍스트) |

***

### 활용 예시

* **PDF 요약 RAG**\
  업로드한 문서에서 질문에 따라 내용을 검색하고 LLM이 요약 제공
* **사내 문서 기반 Q\&A**\
  임직원이 사내 정책 문서에서 답변을 자동으로 받을 수 있도록 구현
* **FAQ 대체 챗봇**\
  자주 묻는 질문에 대해 정적 답변 대신 실시간 정보 기반 응답 제공

***

### 사용 팁

* 검색 정확도를 높이려면 벡터스토어의 Top-K 값을 조절하거나 문서 chunking 전략을 조정하세요.
* 단순한 Q\&A를 넘어, `Chain Tool`과 연결해 후속 작업을 설정할 수 있습니다.
* LLM의 출력을 `Write File`로 저장하거나 이메일로 전송하는 흐름으로 확장 가능합니다.

***

### 주의사항

* 다중 리트리버 검색이 필요한 경우에는 `Multi Retrieval QA Chain` 노드를 사용해야 합니다.
* 컨텍스트로 제공된 문서 외의 질문에는 답변하지 않도록 프롬프트를 제어하는 것이 좋습니다.
* 벡터 리트리버가 올바르게 연결되지 않으면 응답이 비거나 오류가 발생할 수 있습니다.

***

**Retrieval QA Chain**은 WindyFlo에서 RAG를 가장 단순하고 빠르게 구현할 수 있는 기본 체인입니다.\
단일 문서 소스 기반 Q\&A를 구현하고자 할 때 가장 먼저 선택해야 할 노드입니다.
