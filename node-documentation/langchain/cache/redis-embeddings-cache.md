# Redis Embeddings Cache

**Redis Embeddings Cache 노드**는 벡터 임베딩 결과를 Redis 서버에 저장하고, 이후 검색 및 재사용할 수 있도록 지원하는 **외부 벡터 캐시 노드**입니다. 이 노드는 임베딩을 직접 수행하지 않으며, OpenAI Embeddings와 같은 임베딩 생성 노드와 함께 사용하여 생성된 벡터를 Redis에 저장합니다.

***

### 주요 기능

* **임베딩 캐시 저장소**로 Redis 서버 사용
* &#x20;**Embeddings에서 생성된 벡터를 저장**
* **세션 간 유지되는 벡터 재사용 가능**
* **Retriever Tool, Vector Store와 함께 검색 파이프라인 구성 가능**

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-09 151149.png" alt=""><figcaption><p>Windyflo Redis Embeddings Cache</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-09 151155.png" alt=""><figcaption><p>Windyflo Redis Embeddings Cache Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                     | 설명                                          | 필수 여부 |
| ---------------------- | ------------------------------------------- | ----- |
| **Embeddings**         | 외부 임베딩 생성 노드(OpenAI Embeddings 등)의 출력값을 입력  | 필수    |
| **Connect Credential** | Redis 연결을 위한 자격 정보. Credential Manager에서 설정 | 필수    |

***

### 파라미터 (Parameters)

| 항목                    | 설명                                                 |
| --------------------- | -------------------------------------------------- |
| **Time to Live (ms)** | 캐시된 벡터의 유효 시간(ms 단위). 3600000 = 1시간 유지 등           |
| **Namespace**         | Redis 내에서 벡터 그룹을 구분하는 식별자. 예: `"support"`, `"faq"` |

***

### 출력값 (Outputs)

| 출력 항목                    | 설명                                         |
| ------------------------ | ------------------------------------------ |
| **RedisEmbeddingsCache** | 저장된 임베딩 벡터 객체. 이후 Vector Store에 입력으로 사용 가능 |

***

***

### 권장 사용 시나리오

* 세션 간 임베딩 데이터를 지속적으로 활용해야 하는 경우
* OpenAI Embeddings 등의 벡터를 Redis에 저장하고 검색 기반 Q\&A 구축 시
* Namespace를 활용해 다양한 문서 도메인을 분리 저장하고자 할 때

***

### 주의사항

* 이 노드는 임베딩을 **직접 생성하지 않으며**, 반드시 **임베딩 생성 노드의 결과를 입력으로 받아야 합니다**.
* Retriever Tool이나 Vector Store 노드와 함께 사용해야 **실제 검색 기능이 완성**됩니다.
* Redis 서버는 사전 구축 및 연결 정보(Credential) 설정이 필요합니다.
