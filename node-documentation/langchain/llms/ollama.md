# Ollama

Ollama 노드는 로컬 환경에 설치된 LLM(Large Language Model)을 API를 통해 실행할 수 있도록 지원하는 노드입니다. llama2, mistral, codellama 등 다양한 오픈소스 모델을 Docker 기반으로 실행하며, WindyFlo와 연동하여 개인화된 텍스트 생성 환경을 구축할 수 있습니다.

***

### 주요 기능

* 로컬 서버에서 구동 중인 LLM 모델 호출 (기본 포트: `11434`)
* `Temperature`, `Top-k`, `Top-p` 등 세부 샘플링 전략 제어 가능
* `Mirostat`, `Repeat Penalty`, `Context Window Size` 등 고급 생성 설정 지원
* GPU/Thread 자원 설정을 통해 로컬 성능에 최적화 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 133543.png" alt=""><figcaption><p>WindyFlo Ollama</p></figcaption></figure>

<div><figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 133606.png" alt=""><figcaption><p>WindyFlo Ollama Parameters</p></figcaption></figure> <figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 133623.png" alt=""><figcaption><p>WindyFlo Ollama Parameters</p></figcaption></figure></div>

### 입력값 (Inputs)

| 항목          | 설명                                             | 필수 여부 |
| ----------- | ---------------------------------------------- | ----- |
| Cache       | 동일 요청 결과를 저장할지 여부                              | 선택    |
| Base URL    | Ollama 서버의 접속 주소 (예: `http://localhost:11434`) | 필수    |
| Model Name  | 사용할 모델 이름 (`llama2`, `mistral`, `codellama` 등) | 필수    |
| Temperature | 생성 다양성 제어값 (기본값: 0.9)                          | 선택    |

***

### 파라미터 (Parameters)

| 항목                   | 설명                                  |
| -------------------- | ----------------------------------- |
| Top P                | Top-p(nucleus sampling) 설정값         |
| Top K                | Top-k 샘플링 설정값                       |
| Mirostat             | Mirostat 샘플링 활성화 여부 (`0` 또는 `1`)    |
| Mirostat ETA         | Mirostat 학습률 (일반적으로 0.1 권장)         |
| Mirostat TAU         | Mirostat 목표 surprisal 값 (예: 5.0)    |
| Context Window Size  | 컨텍스트 윈도우 최대 길이 설정                   |
| Number of GQA Groups | GQA 그룹 수 (모델 구조에 따라 설정)             |
| Number of GPU        | 할당할 GPU 수                           |
| Number of Thread     | 병렬 처리할 스레드 수                        |
| Repeat Last N        | 반복 억제 대상 토큰 수                       |
| Repeat Penalty       | 반복 문장 억제 강도                         |
| Stop Sequence        | 출력 종료를 유도할 문장 또는 토큰                 |
| Tail Free Sampling   | Tail Free Sampling 설정값 (0.0 \~ 1.0) |

***

### 출력값 (Outputs)

| 출력 항목  | 설명                     |
| ------ | ---------------------- |
| Ollama | Ollama에서 생성된 텍스트 응답 결과 |

***

### 활용 예시

* 비용 부담 없이 로컬에서 LLM 테스트 환경 구축 시
* OpenAI와 유사한 기능의 사설 텍스트 생성 파이프라인 구성
* 프라이빗 데이터를 기반으로 커스터마이징한 모델 운영
* 고성능 GPU 서버에서 `Mistral`, `LLaMA`, `Phi`, `Gemma` 등 비교 분석 목적

***

### 사용 팁

* Ollama를 처음 설치한 경우 `ollama run llama2` 명령어로 모델을 로드해두어야 API 호출이 가능합니다.
* `Base URL`은 기본적으로 `http://localhost:11434`이며, 외부 접근 시 방화벽 및 포트 포워딩 설정 필요
* `Mirostat`(1), `Mirostat ETA`, `Mirostat TAU`는 학습된 생성 분포 유지에 유용하지만, 잘못 설정하면 품질 저하 가능
* `Repeat Last N`, `Repeat Penalty`는 중복된 응답 방지를 위한 핵심 설정이므로 튜닝이 중요합니다.
* `Stop Sequence`를 활용해 챗봇 응답을 명확히 종료시킬 수 있습니다.

***

### 주의사항

* Ollama는 모델 다운로드 및 실행 시 사전 세팅이 필요하므로 로컬 환경 구성 여부를 확인해야 합니다.
* GPU 설정이 과도하거나 스레드 수가 부족할 경우 응답이 느리거나 실패할 수 있습니다.
* 일부 파라미터(`GQA groups`, `Mirostat`)는 사용하지 않으면 기본값으로 처리되나, 모델 특성에 따라 명확히 지정하는 것이 좋습니다.
* 로컬 메모리/디스크 사용량이 많으므로 서버 자원 상태를 지속적으로 확인해야 합니다.
