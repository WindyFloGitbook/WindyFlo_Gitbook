# GoogleGenerativeAI Embeddings

GoogleGenerativeAI Embeddings 노드는 Google Cloud Vertex AI 기반의 `embedding-001` 모델을 사용하여 텍스트를 벡터로 변환합니다. 검색, 분류, 유사도 분석, 군집화 등 다양한 목적에 따라 Task Type을 명확히 지정할 수 있으며, Google이 제공하는 고성능 임베딩 품질을 기반으로 다양한 파이프라인에서 활용됩니다.

***

### 주요 기능

* Google Generative AI의 `embedding-001` 모델을 사용하여 임베딩 벡터 생성
* 목적에 따라 Task Type 설정 가능: 검색, 분류, 유사도, 군집화 등
* Google Cloud 기반 인프라를 활용해 안정적이고 빠른 처리 가능
* 생성된 벡터는 검색, 추천, 분류 등 다양한 다운스트림 작업에 활용 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-13 170222.png" alt=""><figcaption><p>WindyFlo GoogleGenerativeAI Embeddings</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                       | 필수 여부 |
| ------------------ | ---------------------------------------- | ----- |
| Connect Credential | Google API 호출을 위한 인증 정보 (Credential에 등록) | 필수    |
| Model Name         | 사용할 임베딩 모델 이름 (현재는 `embedding-001`만 지원)  | 필수    |
| Task Type          | 임베딩 목적에 따라 처리 유형 선택                      | 필수    |

***

### 파라미터 (Parameters)

※ 별도 파라미터 항목은 없으며, 입력값만으로 설정됨

***

### 출력값 (Outputs)

| 출력 항목                        | 설명                      |
| ---------------------------- | ----------------------- |
| GoogleGenerativeAiEmbeddings | 입력 텍스트에 대한 임베딩 벡터 결과 배열 |

***

### 활용 예시

* 사용자 질문 및 문서에 대해 `RETRIEVAL_QUERY` / `RETRIEVAL_DOCUMENT`로 임베딩 설정하여 RAG 파이프라인 구성
* 유사도 판단이 필요한 추천 시스템에 `SEMANTIC_SIMILARITY` 방식으로 벡터 생성
* 카테고리 분류용 데이터를 `CLASSIFICATION` 타입으로 임베딩하여 ML 모델에 입력
* 고객 발화 데이터를 벡터화한 뒤 `CLUSTERING` 유형으로 군집 분석 수행

***

### 사용 팁

* **Task Type은 반드시 목적에 맞게 설정**해야 합니다. 아래 기준 참고:
  * `RETRIEVAL_QUERY`: 사용자 검색 쿼리용 벡터
  * `RETRIEVAL_DOCUMENT`: 문서 저장용 벡터
  * `SEMANTIC_SIMILARITY`: 유사도 분석용
  * `CLASSIFICATION`: 분류 목적 입력
  * `CLUSTERING`: 군집화 분석용
* `RETRIEVAL_QUERY`와 `RETRIEVAL_DOCUMENT`는 반드시 짝으로 설정해야 검색 성능이 극대화됩니다.
* `TASK_TYPE_UNSPECIFIED`은 테스트 외에는 권장되지 않으며, 명확한 목적을 지정하는 것이 성능상 유리합니다.
* Google Cloud 프로젝트 및 API Key 설정이 완료되어 있어야 정상 호출됩니다.

***

### 주의사항

* `Connect Credential`에 등록된 인증 정보가 정확하지 않으면 호출이 실패합니다.
* Task Type을 설정하지 않거나 목적에 맞지 않게 설정할 경우, 결과 벡터의 품질이 저하되거나 의도한 작업이 어려워질 수 있습니다.
* 현재는 `embedding-001` 모델만 지원되며, 다른 모델 이름 입력 시 오류가 발생합니다.
* Google API 호출 시 사용량에 따라 과금이 발생할 수 있으므로 사전 모니터링이 필요합니다.
