# Ollama Embeddings

Ollama Embeddings 노드는 로컬에서 실행 중인 Ollama 서버를 통해 임베딩 모델을 호출하여 텍스트를 벡터로 변환하는 노드입니다. 인터넷 연결 없이 로컬 환경에서 임베딩 처리 가능하며, GPU 및 Thread 설정을 통해 성능을 유연하게 조정할 수 있습니다.

***

### 주요 기능

* Ollama 서버를 통해 로컬 임베딩 모델(`llama2` 등) 호출 가능
* 로컬 환경에서 벡터 생성 → 개인정보 유출 우려 없는 폐쇄망 처리 가능
* GPU 개수, Thread 수, MMAP 여부 등 성능 튜닝 파라미터 제공
* 오픈소스 모델 기반으로 빠르고 비용 없는 임베딩 처리 가능

<figure><img src="../../../.gitbook/assets/image (15).png" alt=""><figcaption><p>WindyFlo Ollama Embeddings</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (16).png" alt=""><figcaption><p>WindyFlo Ollama Embeddings Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목         | 설명                                                  | 필수 여부 |
| ---------- | --------------------------------------------------- | ----- |
| Base URL   | Ollama 서버의 API 주소 (예: `http://localhost:11434`)     | 필수    |
| Model Name | 사용할 로컬 임베딩 모델 이름 (예: `llama2`, `mxbai-embed-large`) | 필수    |

***

### 파라미터 (Parameters)

| 항목               | 설명                                    |
| ---------------- | ------------------------------------- |
| Number of GPU    | 사용할 GPU 수 (예: `1`, `0` – CPU 전용)      |
| Number of Thread | 병렬 처리를 위한 Thread 수 (시스템 사양에 맞게 조정)    |
| Use MMap         | 모델을 Memory Map 방식으로 불러올지 여부 (기본값: ON) |

***

### 출력값 (Outputs)

| 출력 항목            | 설명                      |
| ---------------- | ----------------------- |
| OllamaEmbeddings | 입력 텍스트에 대한 임베딩 벡터 결과 배열 |

***

### 활용 예시

* 완전한 오프라인 환경에서 문서 임베딩을 생성하여 내부 검색 시스템 구축
* Llama2 또는 Mistral 기반 임베딩 모델을 로컬 서버에서 운영하며 RAG 파이프라인 구성
* GPU와 Thread 설정을 통해 경량화된 로컬 서버에서도 고속 처리 가능
* 데이터 유출 위험 없이 민감 정보 기반 AI 시스템 구축

***

### 사용 팁

* `Base URL`은 Ollama가 실행 중인 머신의 API 주소이며, 포트(`11434`)를 정확히 입력해야 합니다.
* `Model Name`은 Ollama에 사전 다운로드 및 로드된 모델 이름과 정확히 일치해야 합니다.
  * 예시: `llama2`, `mxbai-embed-large`, `nomic-embed-text` 등
* `Use MMap`을 활성화하면 모델 로딩 속도 및 메모리 사용 효율이 향상됩니다.
* Thread 수를 높이면 처리 속도는 빨라지나 시스템 자원을 많이 소모하므로 테스트 후 최적화하세요.

***

### 주의사항

* Ollama 서버가 실행 중이지 않거나 `Base URL`이 올바르지 않으면 호출이 실패합니다.
* 로컬에 해당 모델이 존재하지 않거나 미리 로드되어 있지 않으면 임베딩이 생성되지 않습니다.
* GPU 설정은 해당 머신의 사양과 호환되어야 하며, 없는 GPU를 설정할 경우 오류가 발생합니다.
* 로컬 서버 성능에 따라 처리 시간과 품질이 달라질 수 있으므로 초기 테스트가 필요합니다.
