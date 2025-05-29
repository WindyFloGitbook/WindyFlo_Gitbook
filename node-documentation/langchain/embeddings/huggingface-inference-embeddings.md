# HuggingFace Inference Embeddings

HuggingFace Inference Embeddings 노드는 Hugging Face Inference API 또는 AWS SageMaker Endpoint를 통해 Sentence Transformers 기반 모델을 호출하여 텍스트 임베딩 벡터를 생성하는 노드입니다. 사전 학습된 다양한 오픈소스 임베딩 모델을 활용할 수 있어 유연하고 강력한 임베딩 구축이 가능합니다.

***

### 주요 기능

* Hugging Face에서 제공하는 Sentence Transformers 계열 임베딩 모델 호출
* 사용자 정의 Endpoint를 활용해 자체 배포 모델에도 연결 가능
* RAG, 유사도 분석, 분류, 클러스터링 등 다양한 파이프라인에 활용 가능한 벡터 생성
* 높은 확장성과 오픈소스 기반 유연성 확보

<figure><img src="../../../.gitbook/assets/image (9).png" alt=""><figcaption><p>WindyFlo HuggingFace Inference Embeddings</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                                                                | 필수 여부 |
| ------------------ | --------------------------------------------------------------------------------- | ----- |
| Connect Credential | Hugging Face Inference API 또는 AWS Endpoint 호출용 인증 정보 (Credential에 등록)             | 필수    |
| Model              | 사용할 임베딩 모델의 이름 (예: `sentence-transformers/distilbert-base-nli-stsb-mean-tokens`)  | 필수    |
| Endpoint           | Inference API 또는 SageMaker 배포 엔드포인트 주소 (예: `https://xyz.eu-west-1.aws.endpoints`) | 필수    |

***

### 파라미터 (Parameters)

※ 이 노드는 별도 파라미터 항목 없음

***

### 출력값 (Outputs)

| 출력 항목                          | 설명                      |
| ------------------------------ | ----------------------- |
| HuggingFaceInferenceEmbeddings | 입력 텍스트에 대한 임베딩 벡터 배열 결과 |

***

### 활용 예시

* Hugging Face에서 제공하는 다양한 공개 임베딩 모델을 활용해 유사도 기반 검색 시스템 구성
* 사내에 배포된 AWS SageMaker 기반 임베딩 모델을 Endpoint로 지정하여 호출
* 기존 OpenAI, Cohere 등과 비교하여 성능 또는 비용 면에서 최적화된 대안으로 사용
* 벡터 DB(Faiss, Pinecone 등)와 함께 연계하여 문서 검색, 유사도 분석, 추천 시스템 구축

***

### 사용 팁

* `Model` 필드는 Hugging Face Hub에 등록된 모델 이름을 정확히 입력해야 하며, 예: `sentence-transformers/all-MiniLM-L6-v2`
* `Endpoint` 필드는 Hugging Face Inference Endpoint 또는 SageMaker 엔드포인트로 사용 가능하며, 접두사(`https://`)까지 포함해야 합니다.
* Hugging Face의 Inference Endpoint를 사용하는 경우, **유료 구독 플랜**이 필요할 수 있으니 사전에 확인하세요.
* 다양한 언어를 지원하는 모델을 선택하면 다국어 문서 처리에 유리합니다.

***

### 주의사항

* `Connect Credential`에 등록된 인증 정보가 없거나 잘못된 경우 API 호출이 실패합니다.
* Model 이름과 Endpoint 주소가 일치하지 않거나 형식이 잘못되면 임베딩 생성이 되지 않습니다.
* 호출 대상이 Hugging Face가 아닌 SageMaker일 경우, IAM 권한 및 네트워크 설정을 별도로 구성해야 할 수 있습니다.
* Inference Endpoint 사용량에 따라 비용이 발생하며, 실시간 처리 시에는 응답 속도 확인이 필요합니다.
