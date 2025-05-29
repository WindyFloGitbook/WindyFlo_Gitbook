# Mem0

Mem0 노드는 MemGPT의 오픈소스 메모리 백엔드를 활용하여 고성능 검색 및 저장형 메모리를 제공합니다. 다양한 ID 기반 필터링 및 `Search Only` 기능을 통해 유연한 메모리 검색 및 호출이 가능합니다.

***

### 주요 기능

* MemGPT 기반 메모리 스토리지 및 검색 기능 제공
* `Search Only` 모드를 통해 과거 기록을 단순 검색으로만 활용 가능
* 다양한 범위의 식별자(ID)를 활용한 필터링 지원
* Memory Key, Input Key, Output Key 설정으로 LLM 연동 제어 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 164839.png" alt=""><figcaption><p>WindyFlo Mem0</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (85).png" alt=""><figcaption><p>WindyFlo Mem0 Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                           | 필수 여부 |
| ------------------ | -------------------------------------------- | ----- |
| Connect Credential | MemGPT API Key 또는 사용자 인증 정보 (Credential에 등록) | 필수    |
| User ID            | 사용자 고유 ID (예: `WindyFlo-default-user`)       | 필수    |
| Search Only        | 검색 전용 모드 설정 (활성화 시, 기록 저장 없이 검색만 수행)         | 선택    |
| Run ID             | 세션 실행 단위 식별자 (기록 필터링 용도)                     | 선택    |
| Agent ID           | 연결된 에이전트 식별자                                 | 선택    |
| App ID             | 호출한 애플리케이션 식별자                               | 선택    |
| Project ID         | 프로젝트 단위로 메모리 필터링 시 사용                        | 선택    |
| Organization ID    | 조직 단위 식별자                                    | 선택    |
| Memory Key         | LLM과 연동할 메모리 키 (예: `history`)                | 선택    |
| Input Key          | LLM에 입력으로 전달할 필드 키 (예: `input`)              | 선택    |
| Output Key         | LLM 응답을 저장할 키 지정 (예: `text`)                 | 선택    |

***

### 출력값 (Outputs)

| 출력 항목 | 설명                     |
| ----- | ---------------------- |
| Mem0  | 검색 또는 저장된 메모리 결과 객체 반환 |

***

### 활용 예시

* 다수의 사용자 기록을 MemGPT 기반으로 중앙 저장/검색하는 SaaS 챗봇 구현
* `Search Only` 모드로 유사 질문 검색 및 문맥 기반 유사도 매칭 수행
* LLM 호출 전후 히스토리를 프로젝트, 사용자, 세션 단위로 구조화하여 분석
* LLM 응답 품질 개선을 위한 기록 기반 컨텍스트 재활용

***

### 사용 팁

* `Search Only`를 활성화하면 기록 저장 없이 벡터 검색 기반으로 과거 내용 참조만 수행할 수 있어, 민감 정보 저장을 피할 수 있습니다.
* Input/Output Key 설정은 Agent 또는 LLM 노드의 Key 설정과 반드시 일치시켜야 정상 작동합니다.
* 프로젝트별 또는 조직 단위 분석이 필요할 경우, ID 필드를 일관되게 구성하는 것이 중요합니다.

***

### 주의사항

* Connect Credential 등록 없이 실행 시 인증 오류 발생
* User ID가 유일하지 않거나 불명확할 경우, 검색 범위가 잘못될 수 있음
* LLM 노드와 Input/Output Key가 불일치하면 응답 반영이 되지 않음
* MemGPT 자체 제한(요금, 속도, 저장 기간 등)을 사전에 확인해야 안정적인 운영 가능
