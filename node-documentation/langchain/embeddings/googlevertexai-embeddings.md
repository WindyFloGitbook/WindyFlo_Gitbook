# GoogleVertexAI Embeddings

GoogleVertexAI Embeddings 노드는 Google Cloud Vertex AI의 `textembedding-gecko` 모델을 사용하여 텍스트 데이터를 벡터로 변환합니다. 사전 설정된 Task 없이 단순한 텍스트 임베딩을 빠르게 생성할 수 있으며, 벡터 검색, 분류, 유사도 분석 등에 폭넓게 활용됩니다.

***

### 주요 기능

* Google Vertex AI에서 제공하는 `textembedding-gecko@001` 모델 기반 임베딩 생성
* 별도 Task Type 설정 없이 단순 벡터 생성 목적에 적합
* 입력 텍스트를 벡터로 변환하여 RAG, 유사도 분석, 추천 시스템 등에서 활용 가능
* Vertex AI 기반의 안정적인 인프라 제공 및 빠른 응답 속도 보장

<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption><p>WindyFlo GoogleVertexAI Embeddings</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                                       | 필수 여부 |
| ------------------ | -------------------------------------------------------- | ----- |
| Connect Credential | Google Vertex AI API 호출용 인증 정보 (Credential에 등록)          | 필수    |
| Model Name         | 사용할 Vertex AI 임베딩 모델 이름 (예: `textembedding-gecko@001` 등) | 필수    |

***

### 파라미터 (Parameters)

※ 별도 파라미터 항목 없음

***

### 출력값 (Outputs)

| 출력 항목                    | 설명                      |
| ------------------------ | ----------------------- |
| GoogleVertexAIEmbeddings | 입력 텍스트에 대한 임베딩 벡터 배열 결과 |

***

### 활용 예시

* 대량 텍스트 데이터를 벡터로 변환 후 Pinecone, Faiss 등 벡터 DB에 저장
* Vertex AI 기반 AI 검색 시스템에서 사용자 쿼리와 문서 유사도 비교용 임베딩 생성
* Google Cloud 환경 내에서 유사도 기반 추천 또는 분류 모델 전처리 단계로 활용
* 미리 정의된 Task가 필요 없는 일반 텍스트 임베딩 처리

***

### 사용 팁

* **여러 Vertex AI 임베딩 모델 중 하나를 선택할 수 있으며**, 주로 사용되는 기본 모델은 `textembedding-gecko@001`입니다.
* 모델 선택 시 벡터 품질, 차원 수 등에 차이가 있을 수 있으므로 목적에 맞는 모델을 선택하세요.
* Task를 명시하지 않아도 되는 **단순 임베딩 처리**에 적합하며, Vertex AI 환경에서 빠르게 연동 가능합니다.
* 다양한 언어의 입력을 처리할 수 있지만, 영어 기반 문서에 최적화되어 있습니다.

***

### 주의사항

* `Connect Credential`에 등록된 인증 정보가 없거나 잘못된 경우 API 호출이 실패합니다.
* 현재 선택 가능한 모델 목록은 Google Vertex AI에서 주기적으로 업데이트될 수 있으므로 **모델 리스트를 정기적으로 확인**하는 것이 좋습니다.
* Google Cloud 사용량에 따라 API 호출 비용이 발생할 수 있으므로 주기적인 모니터링이 필요합니다.
* 다국어 입력 지원은 가능하지만 언어별 벡터 품질 차이가 존재할 수 있습니다.
