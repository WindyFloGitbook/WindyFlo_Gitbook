# LangFuse Prompt Template

LangFuse에 등록된 프롬프트 템플릿을 불러와 LLM 호출 시 일관되고 추적 가능한 프롬프트 관리가 가능하도록 구성하는 노드입니다. 프롬프트 버전 관리 및 A/B 테스트가 필요한 경우 유용하며, LangFuse 플랫폼과 연동해 템플릿 기반 프롬프트를 쉽게 호출할 수 있습니다.

***

### 주요 기능

* LangFuse에 저장된 프롬프트 템플릿을 노드를 통해 직접 불러와 사용할 수 있음
* Prompt Name만 입력하면 LangFuse 내 템플릿을 즉시 호출 가능
* 포맷 변수 값(`Format Prompt Values`)을 지정해 템플릿 내 변수를 동적으로 치환
* LangFuse의 버전 관리, 로깅, 성능 분석 기능과 통합 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-20 180931.png" alt=""><figcaption><p>WindyFlo LangFuse Prompt Template</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-20 180939 (1).png" alt=""><figcaption><p>WindyFlo LangFuse Prompt Template Values</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                   | 설명                                         | 필수 여부 |
| -------------------- | ------------------------------------------ | ----- |
| Langfuse Credential  | LangFuse API 인증을 위한 Credential에 등록된 항목 선택  | 필수    |
| Prompt Name          | LangFuse에 저장된 템플릿 이름. 정확히 일치해야 템플릿 불러오기 가능 | 필수    |
| Format Prompt Values | 프롬프트 내 사용되는 변수에 대한 실제 값 지정 (JSON 형식)       | 선택    |

***

### 출력값 (Outputs)

| 출력 항목          | 설명                                            |
| -------------- | --------------------------------------------- |
| PromptTemplate | LangFuse에서 불러온 프롬프트 템플릿 객체. 이후 LLM 노드에 연결해 사용 |

***

### 활용 예시

* 운영 환경에서 **프롬프트 버전별 테스트(A/B Test)** 를 진행할 때
* 마케팅/고객지원 등에서 **템플릿화된 프롬프트를 반복 호출**해야 할 때
* 프롬프트 변경 이력을 추적하고자 할 때 (LangFuse 로그 기반)
* **프롬프트 성능 모니터링 및 최적화**를 위해 LangFuse 연동 시

***

### 사용 팁

* `Prompt Name`은 LangFuse 내 정확한 템플릿 이름과 일치해야 하며, 오탈자 입력 시 불러오기에 실패할 수 있습니다.
* Format Prompt Values는 `{ "customer_name": "Alice" }` 형식으로 작성하여 템플릿 내 변수와 정확히 매칭되어야 합니다.
* LangFuse Credential은 사전 발급된 API Key를 WindyFlo의 Credential에 등록 후 사용해야 합니다.

***

### 주의사항

* LangFuse 플랫폼에 템플릿이 사전에 등록되어 있어야 정상 작동
* Prompt Name 불일치 또는 Credential 미설정 시 오류 발생
* LangFuse API 호출 실패 시 프롬프트 로딩에 실패할 수 있으며, 네트워크 상태에 따라 지연 가능성 있음
