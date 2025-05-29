# Simple Prompt Moderation

Simple Prompt Moderation 노드는 사전에 정의된 Deny List 기반으로 사용자 입력에 포함된 금지 표현을 탐지하여, 특정 조건을 만족할 경우 실행을 차단하는 간단한 프롬프트 검열 노드입니다. 외부 API 호출 없이 빠르고 경량화된 필터링을 제공합니다.

***

### 주요 기능

* Deny List 기반 키워드 매칭 필터링 수행
* 민감하거나 위험한 문구 포함 시 에러 메시지 출력
* 별도 API 호출 없이 빠르게 실행 가능
* 단순 입력 제어, LLM 보안성 강화, 프롬프트 삽입 공격 방지에 유용

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-19 175929.png" alt=""><figcaption><p>WindyFlo Simple Prompt Moderation</p></figcaption></figure>

### 입력값 (Inputs)

| 항목         | 설명                              | 필수 여부 |
| ---------- | ------------------------------- | ----- |
| Chat Model | 연결 대상 LLM 노드 (검열 대상이 되는 입력의 출처) | 선택    |

***

### 파라미터 (Parameters)

| 항목            | 설명                                                                                         |
| ------------- | ------------------------------------------------------------------------------------------ |
| Deny List     | 금지 키워드 또는 문구 리스트 (예: `ignore previous instructions`, `do not follow directions` 등)         |
| Error Message | 조건 위반 시 사용자에게 표시할 메시지 (예: `"Cannot Process! Input violates content moderation policies."`) |

***

### 출력값 (Outputs)

| 출력 항목      | 설명                   |
| ---------- | -------------------- |
| Moderation | 필터링 결과 객체 (허용 여부 포함) |

***

### 활용 예시

* 프롬프트 삽입(prompt injection)을 방지하기 위한 사전 차단
* 챗봇 서비스에서 LLM 명령어 오용을 막기 위한 방어 로직 구성
* 입력 제어를 통해 유해 발화나 설정 우회 시도를 차단
* Deny List를 커스터마이징하여 서비스 도메인별 금지 문구 설정

***

### 사용 팁

* Deny List는 쉼표 또는 줄바꿈 기준으로 다수의 금지 문구를 설정할 수 있습니다.
* 외부 API 호출이 없기 때문에 비용 부담 없이 고속 필터링이 가능합니다.
* Error Message는 사용자 친화적인 언어로 구성하면 UX를 해치지 않으면서 제어가 가능합니다.
* IfElseFunction 노드와 연계해 필터링 조건 충족 시 흐름 차단이 가능합니다.

***

### 주의사항

* 단순 문자열 매칭 기반이므로, 유사 표현 또는 회피 문구 탐지는 불완전할 수 있습니다.
* 복잡한 정책 필터링이나 카테고리 분류가 필요한 경우 OpenAI Moderation 노드와 병행 사용하는 것이 바람직합니다.
* Deny List의 길이가 길어지면 관리 및 디버깅이 어려워질 수 있습니다.
* 단독 사용은 가능하나, Chat Model과 연결된 구조에서 의미 있게 작동합니다.
