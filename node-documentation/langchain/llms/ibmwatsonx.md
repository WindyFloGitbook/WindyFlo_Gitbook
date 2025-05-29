# IBMWatsonx

IBMWatsonx 노드는 IBM의 Watsonx.ai 플랫폼에서 제공하는 LLM 모델(`granite-13b-instruct-v2` 등)을 활용하여 텍스트 생성 기능을 수행합니다. 기업용 환경에 최적화된 Watsonx의 보안성과 신뢰성을 바탕으로 다양한 업무 시나리오에 적용할 수 있습니다.

***

### 주요 기능

* IBM Watsonx에서 배포된 사내용 LLM(`granite` 시리즈 등)을 API를 통해 호출
* `greedy`, `sampling` 등 다양한 디코딩 전략 선택 가능
* `Temperature`, `Top-p`, `Top-k`, `Repeat Penalty` 등 세부 생성 전략 제어
* Streaming 모드를 통해 실시간 응답 처리 지원

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 133233.png" alt=""><figcaption><p>WindyFlo IBMWatsonx</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 133256.png" alt=""><figcaption><p>WindyFlo IBMWatsonx Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                          | 필수 여부 |
| ------------------ | ------------------------------------------- | ----- |
| Cache              | 동일 요청 결과 캐시 여부 설정                           | 선택    |
| Connect Credential | IBM Watsonx 인증 정보 (Credential에 등록)          | 필수    |
| Model              | 사용할 모델 ID (`ibm/granite-13b-instruct-v2` 등) | 필수    |
| Streaming          | 스트리밍 응답 사용 여부 (on/off)                      | 필수    |

***

### 파라미터 (Parameters)

| 항목                    | 설명                                |
| --------------------- | --------------------------------- |
| Decoding Method       | 응답 생성 방식 (`greedy`, `sampling` 등) |
| Top K                 | 샘플링 시 고려할 최대 토큰 수 (기본값: 50)       |
| Top P                 | Top-p(nucleus) 샘플링 확률 (기본값: 0.7)  |
| Temperature           | 생성 응답 다양성 조절값 (기본값: 0.7)          |
| Repeat Penalty        | 반복 문장 억제 강도 (기본값: 1.0)            |
| Max New Tokens        | 최대 생성 토큰 수 (기본값: 100)             |
| Min New Tokens        | 최소 생성 토큰 수 (기본값: 1)               |
| Stop Sequence         | 응답 종료를 유도할 토큰 또는 문장               |
| Include Stop Sequence | 결과에 Stop Sequence 포함 여부           |
| Random Seed           | 생성 결과 고정 시 사용할 시드 값               |

***

### 출력값 (Outputs)

| 출력 항목      | 설명                       |
| ---------- | ------------------------ |
| IBMWatsonx | Watsonx로부터 생성된 텍스트 응답 결과 |

***

### 활용 예시

* 내부 데이터 기반 고객 응대용 Watsonx 기반 AI 비서 구축
* IBM 기반 시스템과 통합되는 기업용 RAG 파이프라인 설계
* 민감한 데이터가 포함된 생성 업무에 보안이 중요한 경우 활용
* 다양한 디코딩 전략 비교를 통한 텍스트 품질 실험

***

### 사용 팁

* `greedy` 방식은 가장 확률이 높은 응답을 반환하므로 일관성이 높고 빠르지만, 창의성은 낮습니다.
* `Top P`, `Top K`, `Temperature` 값을 조합하면 다양한 표현을 유도할 수 있습니다. 예: Top P = 0.9, Temperature = 0.8
* `Stop Sequence` 설정을 통해 챗봇 응답을 명확하게 종료시킬 수 있습니다.
* `Streaming`을 활성화하면 긴 응답이 필요한 응용 시 실시간으로 출력을 받아볼 수 있습니다.

***

### 주의사항

* IBM Cloud 내에서 Watsonx 프로젝트 및 모델 배포가 사전에 완료되어 있어야 합니다.
* 인증 정보가 정확하지 않으면 호출이 실패하며, 에러 메시지가 반환됩니다.
* 모델 ID는 정확한 경로 (`ibm/granite-13b-instruct-v2` 등)를 입력해야 정상 작동합니다.
* 토큰 제한 및 요금은 IBM Watsonx 정책에 따라 달라지며, 과도한 생성 요청 시 제한될 수 있습니다.
