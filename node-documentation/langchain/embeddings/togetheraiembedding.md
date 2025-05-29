# TogetherAIEmbedding

TogetherAIEmbedding 노드는 Together.ai 플랫폼에서 제공하는 사전 학습 임베딩 모델을 호출하여 텍스트 데이터를 벡터로 변환하는 노드입니다. 다양한 오픈소스 Sentence Transformers 모델을 API로 편리하게 사용할 수 있어 빠르게 RAG, 검색, 분류 기반 워크플로우를 구성할 수 있습니다.

***

### 주요 기능

* Together.ai API를 통해 고성능 임베딩 벡터 생성
* `sentence-transformers/msmarco-bert-base-dot-v5` 등 다양한 오픈소스 임베딩 모델 지원
* 캐시 설정을 통해 동일 요청에 대한 반복 처리 비용 절감 가능
* 검색 최적화된 임베딩 모델로 벡터 검색 정확도 개선

<figure><img src="../../../.gitbook/assets/image (19).png" alt=""><figcaption><p>WindyFlo TogetherAIEmbedding</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                                                  | 필수 여부 |
| ------------------ | ------------------------------------------------------------------- | ----- |
| Cache              | 캐시를 사용할지 여부 설정                                                      | 선택    |
| Connect Credential | Together.ai API 인증 정보 (Credential에 등록)                              | 필수    |
| Model Name         | 사용할 임베딩 모델 이름 (예: `sentence-transformers/msmarco-bert-base-dot-v5`) | 필수    |

***

### 파라미터 (Parameters)

※ 별도 고급 파라미터는 없음

***

### 출력값 (Outputs)

| 출력 항목               | 설명                      |
| ------------------- | ----------------------- |
| TogetherAIEmbedding | 입력 텍스트에 대한 임베딩 벡터 결과 배열 |

***

### 활용 예시

* 고정된 사내 문서에 대해 `msmarco` 기반 임베딩으로 RAG 검색 정확도 개선
* 유사도 기반 추천 시스템에서 빠르고 정확한 문장 벡터 생성
* 오픈소스 임베딩 모델을 API 호출 형태로 간편하게 활용
* 캐시 노드연결결을 통해 동일 질의가 반복되는 상황에서 성능과 비용 최적화

***

### 사용 팁

* 기본 모델로 자주 활용되는 `sentence-transformers/msmarco-bert-base-dot-v5`는 검색에 최적화된 구조입니다.
* 캐시 노드를 연결하면 동일한 입력에 대한 재요청 시 API 비용을 줄이고 응답 속도를 향상시킬 수 있습니다.
* Together.ai는 OpenAI보다 저렴한 가격과 오픈모델 기반 구성이 가능하므로 비용 효율적인 벡터 생성이 가능합니다.
* 모델 이름은 Together.ai가 지원하는 모델 목록 중 정확한 이름으로 입력해야 합니다.

***

### 주의사항

* `Connect Credential` 누락 시 호출이 실패하며, 인증 오류가 발생합니다.
* 모델 이름은 Together.ai가 사전 배포한 모델명과 정확히 일치해야 하며, 오타 또는 미지원 모델은 오류 원인이 됩니다.
* 캐시 설정은 임베딩 정확도에 영향을 주지 않지만, 메모리 사용량이 증가할 수 있으므로 사용 환경에 맞게 조정하세요.
* Together.ai API 사용량에 따라 요금이 발생하며, 사전에 사용량 예측이 필요합니다.
