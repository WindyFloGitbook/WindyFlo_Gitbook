# Prompt Template

사용자 지정 텍스트 기반 프롬프트를 템플릿 형태로 구성하는 노드입니다. 변수 삽입이 가능한 기본 프롬프트 구조를 정의할 수 있으며, LLM 호출 전 사용자 입력값을 포함한 프롬프트를 자동 완성하는 데 사용됩니다. LangChain Hub와 연동하여 미리 저장된 템플릿을 불러올 수도 있습니다.

***

### 주요 기능

* 사용자 입력을 변수로 포함할 수 있는 **템플릿 기반 프롬프트 구성**
* LangChain Hub에서 **사전 저장된 프롬프트**를 모델, 용도, 언어 기준으로 검색 및 로딩 가능
* `Format Prompt Values`를 통해 템플릿 내 변수 값을 동적으로 치환
* 간단한 프롬프트 구조를 손쉽게 관리 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-20 181104.png" alt=""><figcaption><p>WindyFlo Prompt Template</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-20 181112.png" alt=""><figcaption><p>WindyFlo Prompt Template Langchain Hub</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-20 181122 (1).png" alt=""><figcaption><p>WindyFlo Prompt Template Values</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                   | 설명                                                   | 필수 여부 |
| -------------------- | ---------------------------------------------------- | ----- |
| Template             | 프롬프트에 사용할 문자열 템플릿. 변수는 `{variable}` 형식으로 입력          | 필수    |
| Langchain Hub        | LangChain Hub에 저장된 템플릿을 모델, 용도, 언어 기준으로 검색하여 불러오기 가능 | 선택    |
| Format Prompt Values | 템플릿 내 사용된 변수에 대한 실제 값 지정 (JSON 형태)                   | 선택    |

***

### 출력값 (Outputs)

| 출력 항목          | 설명                                     |
| -------------- | -------------------------------------- |
| PromptTemplate | 완성된 프롬프트 템플릿 객체. 이후 LLM 노드에 연결하여 활용 가능 |

***

### 활용 예시

* 사용자 입력에 따라 **제품 설명, 슬로건, 추천 문구 등**을 자동 생성해야 할 때
* 특정 입력 구조에 기반한 **문서 초안 생성** 등의 반복 작업에 활용
* `Langchain Hub`를 통해 팀 차원에서 **공유된 프롬프트를 재사용**하고자 할 때
* 변수 기반 프롬프트를 사용하여 **입력 자동화 및 흐름 통제**가 필요한 파이프라인에 적용

***

### 사용 팁

* `Template` 내 변수명은 반드시 `Format Prompt Values`에서 설정한 key와 일치해야 합니다.
* `{product}`, `{goal}` 등 명확한 변수명을 사용하면 재사용성이 높아집니다.
* Langchain Hub 로딩 시 모델/언어/사용 사례를 선택한 후, 검색 결과를 반드시 클릭 후 'Load' 버튼을 눌러야 반영됩니다.

***

### 주의사항

* Template 필드 내 변수명과 `Format Prompt Values`의 key가 일치하지 않으면 프롬프트 생성 실패
* LangChain Hub에서 템플릿 로딩 시 네트워크 지연 또는 검색 오류가 발생할 수 있음
* 과도한 템플릿 길이나 복잡한 포맷은 토큰 초과 또는 출력 오류 유발 가능성 존재
