# Zep Memory - Open Source

Zep Memory - Open Source 노드는 오픈소스 기반의 Zep 서버와 연동하여, 대화 히스토리를 저장 및 검색할 수 있는 고급 메모리 노드입니다. 대화 구조 내에서 사용자와 AI의 발화를 구분하고, LLM과의 연결을 위한 다양한 키 설정을 지원합니다.

***

### 주요 기능

* 오픈소스 Zep 서버와 연동하여 메모리 데이터 저장 및 검색
* 사용자와 AI의 발화 구분을 위한 프리픽스 설정 지원
* 최근 대화 `Size`만큼 유지하여 토큰 효율 최적화
* Input/Output Key 및 Memory Key 지정으로 유연한 LLM 연동 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-19 175054.png" alt=""><figcaption><p>WindyFlo Zep Memory - Open Source</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-19 175108.png" alt=""><figcaption><p>WindyFlo Zep Memory - Open Source Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                             | 필수 여부 |
| ------------------ | ---------------------------------------------- | ----- |
| Connect Credential | Zep 서버 인증 정보 (Credential에 등록 필요)               | 필수    |
| Base URL           | 연결할 Zep API 서버 주소 (예: `http://127.0.0.1:8000`) | 필수    |

***

### 파라미터 (Parameters)

| 항목           | 설명                                   |
| ------------ | ------------------------------------ |
| Session Id   | 세션 또는 사용자 고유 식별자                     |
| Size         | 유지할 최근 대화 턴 수 (예: 10)                |
| AI Prefix    | AI 발화에 붙는 접두어 (예: `ai`)              |
| Human Prefix | 사용자 발화에 붙는 접두어 (예: `human`)          |
| Memory Key   | LLM에서 사용할 히스토리 키 (예: `chat_history`) |
| Input Key    | 입력 메시지를 담을 키 이름 (예: `input`)         |
| Output Key   | 출력 메시지를 담을 키 이름 (예: `text`)          |

***

### 출력값 (Outputs)

| 출력 항목     | 설명                     |
| --------- | ---------------------- |
| ZepMemory | Zep 서버 기반 대화 메모리 객체 반환 |

***

### 활용 예시

* 로컬 또는 클라우드 환경에서 오픈소스 메모리 서버 기반 챗봇 구축
* LLM 응답 품질 향상을 위해 최근 발화만 유지하는 구조 구현
* 사용자와 AI의 발화를 명확히 구분해야 하는 구조화된 대화 시스템
* Input/Output 키 커스터마이징이 필요한 파이프라인 구성

***

### 사용 팁

* Zep 서버는 사전에 로컬 또는 클라우드에 배포되어 있어야 하며, Base URL은 해당 주소로 입력해야 합니다.
* AI Prefix와 Human Prefix는 LLM이 응답 형식을 구분할 수 있도록 설정하는 것이 좋습니다.
* Input/Output Key는 LLM 또는 Agent 노드 설정과 반드시 일치해야 정상 동작합니다.

***

### 주의사항

* Connect Credential 또는 Base URL이 누락되면 Zep 서버에 연결되지 않습니다.
* Size가 너무 작으면 맥락이 부족해지고, 너무 크면 응답 지연 및 토큰 초과 가능성이 있습니다.
* Zep 서버는 메모리, 스토리지 등 리소스를 자체적으로 관리하므로 서버 성능에 따라 결과가 달라질 수 있습니다.
* 단독 사용은 불가하며, 반드시 Agent 또는 LLM 노드와 연결해 사용해야 의미가 있습니다.
