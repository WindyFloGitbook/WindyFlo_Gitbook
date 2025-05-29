# Multi Retrieval QA Chain

**Multi Retrieval QA Chain** 노드는 하나 이상의 벡터스토어에서 정보를 검색하여, LLM이 종합적인 응답을 생성할 수 있도록 지원하는 QA 체인입니다.\
다중 문서 소스에서 정보를 병합해 답변할 수 있도록 설계되어, 다양한 출처 기반의 질의응답 시나리오에 적합합니다.

***

### 주요 기능

* 여러 개의 Vector Store Retriever로부터 정보를 통합 검색
* 질의에 따라 각기 다른 벡터스토어에서 필요한 문서를 추출
* LLM이 검색된 정보를 바탕으로 응답 생성
* 출처 반환 여부 설정 가능 (Return Source Documents)

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-09 173728.png" alt=""><figcaption><p>WindyFlo Multi Retrieval QA Chain</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                          | 설명                                                             | 필수 여부 |
| --------------------------- | -------------------------------------------------------------- | ----- |
| **Language Model**          | 질의에 응답할 언어 모델 (예: OpenAI Chat, Claude 등)                       | 필수    |
| **Vector Store Retriever**  | 검색에 사용할 하나 이상의 벡터스토어 리트리버 (예: In-Memory Vector Store, Redis 등) | 필수    |
| **Input Moderation**        | 유해한 입력값에 대한 필터링 여부 설정                                          | 선택    |
| **Return Source Documents** | 응답과 함께 참조된 원문 정보를 반환할지 여부 (ON/OFF 스위치)                         | 선택    |

※ Vector Store Retriever는  `Redis`, `InMemory Vector Store` 등과 연결 가능\
※ 복수 벡터 리트리버 사용 시 자동으로 병합된 결과 생성

***

### 출력값 (Outputs)

| 항목                        | 설명                                |
| ------------------------- | --------------------------------- |
| **MultiRetrievalQAChain** | 검색 결과를 기반으로 생성된 텍스트 응답 (질의 응답 결과) |

***

### 활용 예시

* **사내 문서 + 외부 정책문서 통합 질의응답**
  * HR 정책은 Google Drive 기반 벡터스토어, 업무 매뉴얼은 PDF 기반으로 분리되어 있을 때 동시에 검색
* **언어별 문서에서 답변 생성**
  * 한국어, 영어 문서 벡터스토어를 따로 구성해 언어 불문 전체 문서에서 검색
* **기술 문서 + FAQ 병렬 질의응답**
  * 고객 질문에 대해 기술 사양서와 FAQ를 동시에 참조해 종합 답변 생성

***

### 사용 팁

* 벡터스토어는 `In-Memory Vector Store`, `Redis` 등과 연결 가능
* 벡터 리트리버 출력이 여러 개일 경우 자동으로 병합되어 동작
* `Return Source Documents` 옵션을 활성화하면 응답의 근거 문서도 함께 출력됨

***

### 주의사항

* 벡터 리트리버 노드가 1개 이상 연결되어 있어야 체인이 정상 작동합니다.
* 벡터스토어 출력 형식이 호환되지 않으면 오류가 발생할 수 있습니다 (예: 비정형 Embedding 연결 시 주의).
* 검색된 문서의 순서나 우선순위는 LLM이 아닌 리트리버의 설정에 따라 달라질 수 있습니다.

***

**Multi Retrieval QA Chain**은 다양한 데이터 출처를 통합 검색하고 응답하는 고급 질의응답 체인으로,\
여러 문서 소스가 존재하는 프로젝트나 멀티도메인 질문에 유용하게 활용할 수 있습니다.
