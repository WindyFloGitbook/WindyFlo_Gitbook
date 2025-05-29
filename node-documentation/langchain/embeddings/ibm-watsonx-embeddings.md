# IBM Watsonx Embeddings

IBM Watsonx Embeddings 노드는 IBM의 Watsonx.ai 플랫폼에서 제공하는 고성능 임베딩 모델(`ibm/slate-30m-english-rtrvr`)을 통해 텍스트 데이터를 벡터로 변환하는 노드입니다. Watsonx의 인프라를 활용하여 안정적으로 벡터 임베딩을 생성할 수 있으며, IBM 생태계 내 보안이 중요한 엔터프라이즈 환경에서 주로 활용됩니다.

***

### 주요 기능

* IBM Watsonx.ai에서 제공하는 사전 학습 임베딩 모델을 통해 텍스트 벡터 생성
* Token 수 제한, 재시도 횟수, 동시 처리 수 등 세부 동작 제어 가능
* 기업 보안 환경에 최적화된 IBM 플랫폼 기반 벡터 처리
* 생성된 임베딩은 검색, 유사도 분석, 분류 등 다양한 AI 워크플로우에 활용 가능

<figure><img src="../../../.gitbook/assets/image (10).png" alt=""><figcaption><p>WindyFlo IBM Watsonx Embeddings</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (11).png" alt=""><figcaption><p>WindyFlo IBM Watsonx Embeddings Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                                       | 필수 여부 |
| ------------------ | -------------------------------------------------------- | ----- |
| Connect Credential | IBM Watsonx API 인증 정보 (Credential에 등록)                   | 필수    |
| Model Name         | 사용할 Watsonx 임베딩 모델 이름 (예: `ibm/slate-30m-english-rtrvr`) | 필수    |

***

### 파라미터 (Parameters)

| 항목                    | 설명                        |
| --------------------- | ------------------------- |
| Truncate Input Tokens | 입력 토큰 수 제한 (초과 시 잘라냄)     |
| Max Retries           | API 호출 실패 시 재시도 횟수 (예: 3) |
| Max Concurrency       | 병렬 요청 허용 수 (예: 5)         |

***

### 출력값 (Outputs)

| 출력 항목             | 설명                      |
| ----------------- | ----------------------- |
| WatsonxEmbeddings | 입력 텍스트에 대한 임베딩 벡터 배열 결과 |

***

### 활용 예시

* 보안이 중요한 기업 내부 시스템에서 문서 검색용 벡터 생성
* Watsonx 기반 데이터 분석 파이프라인에 벡터 입력 데이터 제공
* Watson NLP, Knowledge Studio 등 IBM 생태계와 통합한 RAG 파이프라인 구성
* Token 수 제한이 있는 긴 문서 텍스트를 설정 범위 내에서 처리해 벡터로 변환

***

### 사용 팁

* `Model Name`은 IBM에서 사전 배포한 모델명 그대로 입력해야 하며, 일반적으로 `ibm/slate-30m-english-rtrvr`를 사용합니다.
* `Truncate Input Tokens`는 입력 길이를 제한하여 과도한 토큰 수로 인한 오류를 방지할 수 있습니다.
* `Max Retries`는 네트워크 이슈나 일시적 오류 대응을 위한 재시도 횟수이며, 기본값은 3\~5가 권장됩니다.
* `Max Concurrency`를 조절하여 동시에 처리할 요청 수를 제한하면 안정성과 처리량을 균형 있게 조정할 수 있습니다.

***

### 주의사항

* IBM Watsonx API를 사용하기 위해서는 IBM Cloud 내 서비스 활성화 및 Credential 등록이 반드시 필요합니다.
* Token 수 초과, Credential 누락, 모델명 오입력 시 호출이 실패합니다.
* 모델은 현재 `slate` 계열의 영어 모델만 제공되므로, 다국어 지원은 제한적일 수 있습니다.
* 사용량에 따라 IBM Cloud 플랫폼 과금이 발생하므로 API 호출량을 사전에 조절해야 합니다.
