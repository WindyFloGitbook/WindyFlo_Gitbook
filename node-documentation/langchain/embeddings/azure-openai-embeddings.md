# Azure OpenAI Embeddings

Azure OpenAI Embeddings 노드는 Azure를 통해 배포된 OpenAI 모델을 이용하여 텍스트 데이터를 벡터 임베딩으로 변환합니다. 이 임베딩 벡터는 검색, 분류, 추천 등 다양한 AI 파이프라인에서 활용될 수 있으며, OpenAI의 강력한 언어 표현력과 Azure의 인프라 안정성을 함께 제공합니다.

***

### 주요 기능

* Azure에 배포된 OpenAI 임베딩 모델을 통해 텍스트를 벡터로 변환
* Batch 단위로 여러 입력을 한 번에 처리하여 효율적인 임베딩 수행
* API 요청 시간 제한, 경로 설정 등 Azure 환경에 최적화된 파라미터 제공
* 결과 벡터는 다양한 Vector Store 또는 분석 파이프라인에 활용 가능

<figure><img src="../../../.gitbook/assets/image (5).png" alt=""><figcaption><p>WindyFlo Azure OpenAI Embeddings</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption><p>WindyFlo Azure OpenAI Embeddings Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                              | 필수 여부 |
| ------------------ | ----------------------------------------------- | ----- |
| Connect Credential | Azure OpenAI API 호출에 필요한 인증 정보 (Credential에 등록) | 필수    |

***

### 파라미터 (Parameters)

| 항목          | 설명                                              |
| ----------- | ----------------------------------------------- |
| Batch Size  | 한 번에 처리할 텍스트 수 (기본값: 100)                       |
| Timeout     | API 호출 제한 시간 (ms 단위, 설정 시 요청 시간 초과 방지)          |
| BasePath    | Azure OpenAI 서비스의 커스텀 엔드포인트 경로 (필요 시 입력)        |
| BaseOptions | 추가로 전달할 key-value 형식의 옵션 (예: headers, params 등) |

***

### 출력값 (Outputs)

| 출력 항목                 | 설명                      |
| --------------------- | ----------------------- |
| AzureOpenAIEmbeddings | 입력 텍스트에 대한 벡터 임베딩 결과 배열 |

***

### 활용 예시

* Azure 환경에서 운영 중인 문서 기반 RAG 파이프라인에 벡터 생성용으로 활용
* 기업 내부 보안 요건에 따라 Azure에서 직접 관리하는 모델을 통한 임베딩 수행
* 입력 데이터를 벡터화하여 Pinecone, Weaviate 등 외부 Vector Store와 연계
* 검색 유사도, 카테고리 분류 등 벡터 기반 ML 모델의 입력값 생성에 사용

***

### 사용 팁

* `Batch Size`를 높이면 처리량은 증가하지만, 응답 크기 초과로 실패할 수 있으므로 테스트 후 최적값 설정이 필요합니다.
* Azure에서 **BasePath**는 모델 배포 경로와 정확히 일치해야 하며, 설정 누락 시 오류가 발생합니다.
* `BaseOptions`를 통해 요청에 커스텀 헤더 또는 파라미터를 추가하면 인증 또는 로깅을 유연하게 처리할 수 있습니다.
* `Timeout`을 설정해 장시간 지연에 대비하거나 Azure API가 일시적으로 응답이 느릴 경우를 안정적으로 제어할 수 있습니다.

***

### 주의사항

* Azure OpenAI 서비스는 **사용자 계정에 등록된 모델 배포 이름 및 리전**과 정확히 일치해야 정상 호출됩니다.
* 임베딩 모델이 아닌 일반 Chat 모델로 구성된 Azure 리소스를 연결할 경우 오류가 발생합니다.
* `Connect Credential` 등록 시 Key 이름, 엔드포인트, 리전 정보가 정확히 입력되어야 합니다.
* 사용량이 많을 경우 Azure API 호출 요금이 과금될 수 있으므로 트래픽 제어 및 사용량 모니터링이 필요합니다.
