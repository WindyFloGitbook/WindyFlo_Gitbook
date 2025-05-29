# Buffer Window Memory

Buffer Window Memory 노드는 최근 대화 내용 일부만 메모리에 유지하는 윈도우 기반 메모리 구조입니다. 전체 히스토리를 저장하지 않고, 지정된 수 만큼의 메시지만 LLM에 전달함으로써 컨텍스트 초과를 방지하고 성능을 최적화할 수 있습니다.

***

### 주요 기능

* 가장 최근의 대화 기록만 유지하는 슬라이딩 윈도우 방식의 메모리
* `Size`를 통해 유지할 대화 턴 수를 지정하여 토큰 사용량 제어
* `Memory Key`를 통해 일관된 대화 히스토리 전달 가능
* Session ID 기반으로 사용자 간 메모리 분리 관리 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 140029.png" alt=""><figcaption><p>WindyFlo Buffer Window Memory</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 140038 (1).png" alt=""><figcaption><p>WindyFlo Buffer Window Memory Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목         | 설명                                     | 필수 여부 |
| ---------- | -------------------------------------- | ----- |
| Size       | 유지할 대화 기록 개수 (예: 4이면 최근 4개의 메시지만 유지)   | 필수    |
| Session Id | 사용자 또는 세션 구분 식별자                       | 선택    |
| Memory Key | LLM과 연동할 대화 히스토리 키 (예: `chat_history`) | 필수    |

***

### 출력값 (Outputs)

| 출력 항목              | 설명                        |
| ------------------ | ------------------------- |
| BufferWindowMemory | 윈도우 방식으로 구성된 대화 메모리 객체 반환 |

***

### 활용 예시

* 짧은 히스토리만 전달하고 싶은 FAQ 챗봇, 상담 봇 구현
* LLM 토큰 제한을 고려한 멀티턴 대화 최적화
* 다양한 사용자로부터 들어오는 요청을 Session ID로 구분하여 처리
* 이전 발화 일부만 유지하면서 흐름만 반영하는 캐주얼 챗봇 구축

***

### 사용 팁

* `Size`는 응답 품질과 비용(토큰 수)의 균형을 고려해 설정하는 것이 좋습니다.
* 동일한 `Session Id`를 활용하면 사용자별 대화를 개별 추적할 수 있습니다.
* 너무 작은 `Size` 설정은 이전 맥락 부족으로 응답 품질 저하를 유발할 수 있습니다.

***

### 주의사항

* Size가 너무 클 경우 일반 Buffer Memory와 차이가 없어지며, LLM 토큰 초과 가능성도 증가합니다.
* 히스토리 전체가 아닌 일부만 전달되므로, 이전 발화에 대한 완전한 맥락을 요구하는 Task에는 부적합할 수 있습니다.
* 단독 사용은 의미가 없으며, 반드시 Agent 노드 또는 LLM Chain과 연결해야 동작합니다.
