# Cohere Embeddings

Cohere Embeddings 노드는 Cohere에서 제공하는 고성능 임베딩 모델을 사용하여 텍스트 데이터를 벡터로 변환합니다. 사용 목적에 따라 임베딩 방식(Type)을 설정할 수 있어 검색, 분류, 군집화 등 다양한 AI 파이프라인에 적합합니다.

***

### 주요 기능

* Cohere의 `embed-english` 또는 `embed-multilingual` 시리즈를 사용하여 텍스트 임베딩
* `search`, `classification`, `clustering` 목적에 따라 벡터 표현 최적화 가능
* 다양한 용도별 타입(`search_query`, `search_document`, `classification`, `clustering`) 설정 지원
* RAG 파이프라인, 분류 모델, 데이터 분석 등에서 활용 가능

<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption><p>WindyFlo Cohere Embeddings</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                             | 필수 여부 |
| ------------------ | ---------------------------------------------- | ----- |
| Connect Credential | Cohere API 호출을 위한 인증 정보 (Credential에 등록)       | 필수    |
| Model Name         | 사용할 임베딩 모델 이름 (예: embed-english-v2.0)          | 필수    |
| Type               | 임베딩 목적에 따른 처리 방식 설정 (search, classification 등) | 필수    |

***

### 파라미터 (Parameters)

※ 이 노드는 별도 파라미터 항목 없이 기본 입력값만으로 설정됨

***

### 출력값 (Outputs)

| 출력 항목            | 설명                   |
| ---------------- | -------------------- |
| CohereEmbeddings | 입력 텍스트에 대한 임베딩 벡터 배열 |

***

### 활용 예시

* 검색 기반 RAG 시스템에서 사용자 질문(`search_query`)과 문서(`search_document`)에 대한 임베딩 벡터 생성
* 제품 리뷰, 사용자 발언 등 텍스트 데이터를 벡터화하여 분류 모델에 입력 (`classification`)
* 문서 또는 문장 단위 데이터를 클러스터링 분석용 벡터로 변환 (`clustering`)
* 벡터 DB(Faiss, Pinecone 등)에 삽입하기 위한 표준화된 텍스트 임베딩 생성

***

### 사용 팁

* **Type 설정은 필수**입니다. 각 용도에 맞지 않는 Type을 사용할 경우 결과 벡터의 품질이 저하됩니다.
  * `search_document`: 문서 저장용
  * `search_query`: 검색용 사용자 질문
  * `classification`: 분류 모델 입력
  * `clustering`: K-means 등 군집화 입력
* `search_document`와 `search_query`는 반드시 **짝으로 구성**되어야 검색 정확도가 최적화됩니다.
* `embed-multilingual` 모델은 다국어 지원이 필요할 경우 선택하는 것이 적합합니다.
* 모델 버전(v2.0 등)은 차원 수 및 품질에 영향을 줄 수 있으므로 테스트 후 채택하세요.

***

### 주의사항

* Cohere API 키가 유효하지 않거나 쿼터가 초과되면 오류가 발생합니다.
* `Type` 항목을 설정하지 않으면 임베딩이 생성되지 않거나 목적과 맞지 않는 벡터가 생성될 수 있습니다.
* 모델 이름은 정확하게 입력해야 하며, 지원되지 않는 버전 입력 시 실패합니다.
* 입력 텍스트 길이에 따라 처리 시간과 비용이 달라질 수 있습니다.
