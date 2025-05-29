# VectorDB QA Chain

**VectorDB QA Chain** 노드는 사용자가 구성한 Vector Store에 기반하여 질문에 대한 응답을 생성하는 문서 기반 질의응답 체인입니다.\
간단한 구성으로 다양한 벡터스토어에 연결할 수 있으며, Language Model을 기반으로 검색된 문서를 요약하거나 해석한 응답을 생성합니다.

***

### 주요 기능

* 벡터스토어에 기반한 문서 검색 및 응답 생성
* 간결한 입력 구성으로 빠르게 QA 파이프라인 구성
* 다양한 Vector Store와 호환 가능

***

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-09 180645.png" alt=""><figcaption><p>WindyFlo VectorDB QA Chain</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목               | 설명                                        | 필수 여부 |
| ---------------- | ----------------------------------------- | ----- |
| Language Model   | 응답 생성을 위한 LLM (예: GPT-4, Claude 등)        | 필수    |
| Vector Store     | 검색 대상으로 사용할 벡터스토어 (예: Chroma, Pinecone 등) | 필수    |
| Input Moderation | 유해하거나 부적절한 입력을 필터링하는 기능                   | 선택    |

***

#### 파라미터 (Parameters)

※ 본 노드는 별도의 파라미터 없이 입력 항목만으로 동작합니다.\
필요한 설정은 Vector Store와 LLM 노드에서 각각 정의합니다.

***

#### 출력값 (Outputs)

| 출력 항목           | 설명                      |
| --------------- | ----------------------- |
| VectorDBQAChain | 질의응답 결과 텍스트 (LLM 응답 형식) |

***

### 활용 예시

* 내장형 문서 검색 + 요약 챗봇
* 특정 프로젝트 문서에 기반한 QA 서비스
* 제품 매뉴얼, 기술 문서 기반 고객 응대 자동화

***

### 사용 팁

* Vector Store는 `Chroma`, `Pinecone`, `Weaviate` 등 Vector Store 노드와 연결  가능합니다.
* LLM은 `ChatOpenAI`, `ChatAnthropic`, `ChatTogetherAI` 등과 연결 가능하며, 다양한 모델을 시험해 볼 수 있습니다.
* 간단한 QA 구성 시 `Retrieval QA Chain`보다 더 직접적인 제어가 가능할 수 있습니다.

***

### 주의사항

* Vector Store가 설정되지 않으면 질문에 대한 문맥 기반 응답이 생성되지 않습니다.
* 이 노드는 자체 Summarizer 기능을 내장하고 있지 않으며, 응답 생성 품질은 연결된 LLM에 따라 결정됩니다.
* 고도화된 문서 분기 응답이 필요한 경우 `Multi Retrieval QA Chain` 또는 `Conversational Retrieval QA Chain`을 고려하세요.
