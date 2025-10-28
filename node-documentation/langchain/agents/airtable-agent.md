# Airtable Agent

**Airtable Agent 노드**는 WindyFlo에서 Airtable에 저장된 데이터를 질의하고, 그 결과를 자연어로 받아볼 수 있도록 설계된 에이전트입니다. 복잡한 인터페이스 없이, 단순한 질문으로 필요한 정보를 대화형으로 얻을 수 있으며, 다양한 자동화 시나리오에서 유용하게 활용됩니다.

예를 들어, 다음과 같은 질문을 처리할 수 있습니다:

* “내 프로젝트 트래커 테이블에서 아직 완료되지 않은 작업이 몇 개인가요?”
* “CRM에 등록된 고객들의 연락처를 알려줘.”
* “지난주에 추가된 모든 레코드의 요약을 알려줘.”

Airtable Agent는 단순히 데이터를 불러오는 수준을 넘어, **LLM을 통해 데이터를 이해하고 요약**해주기 때문에 비 개발자도 직관적으로 데이터를 활용할 수 있습니다.

<figure><img src="../../../.gitbook/assets/image (67).png" alt=""><figcaption><p>WindyFlo Airtable Agent</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                        | 설명                                                                                                                               | 필수 여부 |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | ----- |
| **Language Model**        | ChatModel 연결 (예: GPT, Claude 등). 질의 분석 및 응답 생성에 사용됩니다.                                                                           | 필수    |
| **Input Moderation**      | 부적절한 질문을 자동 필터링할지 여부.                                                                                                            | 선택    |
| **Connect Credential**    | Airtable 연결용 API 키 등 인증 정보.                                                                                                      | 필수    |
| **Base ID**               | <p>Airtable Base의 고유 ID.<br>예시 URL: <code>https://airtable.com/app11RobdGoX0YNsC/...</code> → <code>app11RobdGoX0YNsC</code></p> | 필수    |
| **Table ID**              | <p>Airtable Table의 고유 ID.<br>예시 URL: <code>.../tblJdmvbrgizbYlCO/...</code> → <code>tblJdmvbrgizbYlCO</code></p>                 | 필수    |
| **Additional Parameters** | JSON 형식의 세부 설정값.                                                                                                                 | 선택    |
| **Return All**            | 테이블의 모든 레코드를 가져올지 여부.                                                                                                            | 선택    |
| **Limit**                 | 최대 조회 수 (기본값: 100). Return All이 꺼져 있을 때만 적용됩니다.                                                                                  | 선택    |

### 활용 예시

| 사용 시나리오    | 예시                      |
| ---------- | ----------------------- |
| **업무 자동화** | "오늘 마감인 작업만 보여줘"        |
| **CRM 질의** | "서울에 거주 중인 고객 리스트를 보여줘" |
| **데이터 요약** | "지난주에 추가된 항목들 요약해줘"     |
