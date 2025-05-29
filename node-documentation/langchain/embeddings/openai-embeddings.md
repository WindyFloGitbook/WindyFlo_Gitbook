# OpenAI Embeddings

OpenAI Embeddings 노드는 OpenAI의 고성능 임베딩 모델(`text-embedding-3` 시리즈 및 `text-embedding-ada-002`)을 호출하여 텍스트를 벡터로 변환하는 노드입니다. 다양한 크기와 성능의 모델을 선택할 수 있으며, 검색, 유사도 비교, 분류, 클러스터링 등 다양한 AI 워크플로우에 활용할 수 있습니다.

***

### 주요 기능

* OpenAI가 제공하는 최신 임베딩 모델을 통해 고품질 벡터 생성
* `text-embedding-3-large`, `text-embedding-3-small`, `text-embedding-ada-002` 중 선택 가능
* 대량 입력을 처리하기 위한 Batch 설정, 응답 지연 제어, 차원 수 설정 등 다양한 파라미터 지원
* 줄바꿈 처리 옵션 등 데이터 정제 유연성 확보

<figure><img src="../../../.gitbook/assets/image (17).png" alt=""><figcaption><p>WindyFlo OpenAI Embeddings</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (18).png" alt=""><figcaption><p>WindyFlo OpenAI Embeddings Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                                                    | 필수 여부 |
| ------------------ | --------------------------------------------------------------------- | ----- |
| Connect Credential | OpenAI API 인증 정보 (Credential에 등록)                                     | 필수    |
| Model Name         | 사용할 임베딩 모델 이름 (예: `text-embedding-3-large`, `text-embedding-ada-002`) | 필수    |

***

### 파라미터 (Parameters)

| 항목              | 설명                                      |
| --------------- | --------------------------------------- |
| Strip New Lines | 개행 문자 제거 여부 (기본값: false)                |
| Batch Size      | 한 번에 처리할 텍스트 수 (예: 100)                 |
| Timeout         | 응답 대기 시간 제한 (ms 단위)                     |
| BasePath        | OpenAI API 커스텀 엔드포인트 (선택, 예: 프록시 서버 주소) |
| Dimensions      | 출력 임베딩 벡터 차원 수 (모델에 따라 지원 범위 상이)        |

***

### 출력값 (Outputs)

| 출력 항목            | 설명                      |
| ---------------- | ----------------------- |
| OpenAIEmbeddings | 입력 텍스트에 대한 임베딩 벡터 배열 결과 |

***

### 활용 예시

* RAG 파이프라인에서 사용자 질문과 문서 임베딩을 생성해 유사도 기반 검색 구현
* 제품 설명, 리뷰 데이터를 임베딩 후 클러스터링을 통한 인사이트 도출
* 다국어 텍스트 데이터를 임베딩 후 분류 모델의 입력 데이터로 활용
* 기존 검색 시스템에 벡터 필터 기능을 추가하여 정확도 향상

***

### 사용 팁

* `text-embedding-3-large`는 가장 높은 품질의 벡터를 생성하며, 성능이 중요한 분석이나 고정도 검색에 적합합니다.
* `text-embedding-ada-002`는 빠르고 저렴한 비용으로 실시간 임베딩 처리에 적합합니다.
* `Strip New Lines`를 활성화하면 줄바꿈을 제거해 일관된 벡터 생성이 가능하며, 특히 문장 단위 임베딩 시 유용합니다.
* `Dimensions` 파라미터는 `text-embedding-3` 시리즈에서만 사용 가능하며, 출력 차원 수를 조정하여 공간 최적화가 가능합니다.

***

### 주의사항

* `Model Name`은 반드시 OpenAI가 공식 지원하는 모델명만 입력해야 하며, 오타 또는 지원 종료된 모델은 호출 실패 원인이 됩니다.
* `Dimensions` 파라미터는 `text-embedding-3`에서만 사용 가능하며, `text-embedding-ada-002`에서는 무시됩니다.
* Batch Size가 너무 클 경우 OpenAI API 요청 크기 제한(토큰 기준)을 초과하여 실패할 수 있으므로 조정이 필요합니다.
* OpenAI API 사용량에 따라 요금이 발생하므로 트래픽에 따라 비용 계획을 수립해야 합니다.
