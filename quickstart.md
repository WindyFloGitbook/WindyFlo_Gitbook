---
icon: bullseye-arrow
---

# Quickstart

WindyFlo의 가장 큰 장점 중 하나는 **별도의 설치 과정 없이 웹 브라우저에서 바로 사용**할 수 있다는 점입니다. 복잡한 설정이나 준비는 필요 없이 AI 파이프라인 구축을 시작해 보세요!

이 가이드에서는 WindyFlo를 사용하여 첫 AI 파이프라인을 만들고 실행하는 기본적인 단계를 안내합니다.

<figure><img src="https://gitbookio.github.io/onboarding-template-images/quickstart-hero.png" alt=""><figcaption></figcaption></figure>

**사전 준비:**

* WindyFlo 계정이 필요합니다. 아직 없다면 [WindyFlo 설정](windyflo-setting.md) 가이드를 참고하여 계정을 생성하고 로그인해주세요.
* **OpenAI API 키:** 이 예제에서는 OpenAI 모델을 사용합니다. 작동을 위해서는 본인의 OpenAI API 키가 필요합니다. (유료 플랜 사용자는 WindyFlo에서 제공하는 API KEY를 사용할 수도 있습니다. 자격증명(Credentials) 가이드 참조)

{% hint style="info" %}
OpenAI API 키가 무엇이고 어떻게 얻는지 잘 모르겠다면 \[여기 가이드]를 참고하세요.
{% endhint %}

### 1단계: 새 파이프라인 생성

1. WindyFlo에 로그인합니다.
2. `내 파이프라인` 버튼을 클릭합니다.
3. `Create Pipeline` 버튼을 클릭합니다.
4. **파이프라인 이름**을 입력합니다 (예: `MyFirstChatbot`).
5. (필수사항) 설명과 태그를 추가합니다.
6. `AI 모델 파이프라인 생성` 버튼을 클릭합니다. 빈 워크스페이스(캔버스)가 열립니다.

<div data-full-width="false"><figure><img src="https://gitbookio.github.io/onboarding-template-images/quickstart-import.png" alt=""><figcaption></figcaption></figure></div>

### 2단계: 노드 추가 및 연결

이제 대화형 챗봇의 핵심 구성 요소들을 추가하고 연결합니다.

1. 화면 좌측 상단의 `노드 추가` 버튼을 클릭합니다.
2. **chat models** 카테고리에서 `ChatOpenAI` 노드를 찾아 캔버스로 드래그 앤 드롭합니다. (챗봇의 두뇌 역할)
3. `노드 추가`를 다시 클릭하고, **Memory** 카테고리에서 `Buffer Memory` 노드를 캔버스로 드래그합니다. (대화 기억 역할)
4. 다시 `노드 추가`를 클릭하고, **Chains** 카테고리에서 `Conversation Chain` 노드를 캔버스로 드래그합니다. (chat mdel과 Memory 흐름 관리)
5. **노드 연결:** (아래 이미지와 같이 연결합니다)
   * `ChatOpenAI` 노드의 오른쪽 출력 포트 (`ChatOpenAI`)를 `Conversation Chain` 노드의 왼쪽 입력 포트 (`Chat Model`)로 연결합니다.
   * `Buffer Memory` 노드의 오른쪽 출력 포트 (`BufferMemory`)를 `Conversation Chain` 노드의 왼쪽 입력 포트 (`Memory`)로 연결합니다.

<figure><img src="https://gitbookio.github.io/onboarding-template-images/quickstart-import.png" alt=""><figcaption><p><em>챗봇의 기본 파이프라인</em></p></figcaption></figure>

### 3단계: ChatOpenAI 노드 설정 (API 키 및 모델)

`ChatOpenAI` 노드가 실제로 작동하려면 OpenAI API 키를 연결하고 모델을 선택해야 합니다.

1. 캔버스 위의 `ChatOpenAI` 노드를 클릭합니다. 화면 오른쪽에 설정 패널이 나타납니다.
2. **Connect Credential** 섹션에서 드롭다운 메뉴를 클릭하고 `Create New`를 선택하여 **본인의 OpenAI API 키**를 입력하고 저장합니다. (이미 저장된 키가 있다면 선택합니다.)
3. **Model Name** 섹션에서 드롭다운 메뉴를 클릭하고 사용 가능한 다른 모델을 선택합니다.&#x20;
4.  (선택 사항) `Temperature` 값을 조정할 수 있습니다.&#x20;

    {% hint style="info" %}
    Temperature는 모델 답변의 창의성 또는 무작위성을 조절하는 값입니다.\
    \* 낮은 값 (0에 가까울수록): 더 일관성 있고 예측 가능한 답변을 생성합니다. (사실 정보 전달에 적합)\
    \* 높은 값 (1에 가까울수록): 더 다양하고 창의적인 답변을 생성합니다. (아이디어 구상, 이야기 만들기에 적합)\
    기본값은 보통 0.7\~0.9 사이이며, 필요에 따라 조절하여 원하는 답변 스타일을 얻을 수 있습니다.
    {% endhint %}
5. `Buffer Memory`와 `Conversation Chain` 노드는 이 기본 예제에서는 추가 설정 없이 연결만으로도 작동합니다.

### 4단계: 저장 및 테스트 실행

이제 파이프라인을 저장하고, 챗봇을 테스트 합니다.

1. 화면 우측 상단의 `저장` 버튼을 클릭하여 파이프라인을 저장합니다.
2. 저장 버튼 옆의 **실행** 버튼을 클릭하여 테스트 채팅창을 엽니다.
3. **첫 번째 질문 (정보 주기):** 채팅창에 "내 이름은 WindyFlo야." 라고 입력하고 엔터를 누릅니다. 챗봇의 응답을확인합니다. (예: "안녕하세요, WindyFlo!").
4. **두 번째 질문 (기억 확인):** 이어서 채팅창에 "내 이름이 뭐야?" 라고 입력하고 보내기를 누릅니다.
5. 챗봇이 "당신의 이름은  WindyFlo입니다." 와 같이 **이전 대화에서 알려준 이름을 기억하고** 답변하는지 확인합니다. 이렇게 `Buffer Memory`와 `Conversation Chain`이 정상 작동 하는지 확인 합니다.

<figure><img src="https://gitbookio.github.io/onboarding-template-images/quickstart-import.png" alt=""><figcaption><p><em>챗봇 저장 및 테스트</em></p></figcaption></figure>

### 5단계: (선택 사항) 챗봇으로 공유하기

만든 대화형 챗봇을 다른 사람과 쉽게 공유할 수 있습니다.

1. 우측 상단의 `API로 삽입` 버튼을 클릭합니다.
2. `Share Chatbot` 탭을 선택합니다.
3. 필요하면 챗봇 제목이나 환영 메시지를 수정하고 `Save Changes`버튼을 눌러 저장 합니다.
4. 상단에생성된 **공유 URL**을 복사합니다.
5. 이 URL을 통해 다른 사람도 당신이 만든, 대화를 기억하는 챗봇과 이야기할 수 있습니다.

<figure><img src="https://gitbookio.github.io/onboarding-template-images/quickstart-import.png" alt=""><figcaption><p><em>챗봇 공유하기</em></p></figcaption></figure>

***

**축하합니다!** 🎉 대화 내용을 기억하는 좀 더 스마트한 나만의 챗봇을 성공적으로 만들었습니다.

이처럼 WindyFlo는 다양한 노드를 조합하여 복잡한 AI 기능도 쉽게 구현할 수 있도록 돕습니다. 더 많은 기능을 탐색하려면 다음 문서들을 살펴보세요:

* **핵심 개념:** 파이프라인, 노드, 체인, 메모리 등 주요 개념을 더 깊이 이해합니다.
* **노드 라이브러리:** 사용 가능한 모든 노드들의 상세 기능과 설정을 알아봅니다.
* **Embed as API** : 완성한 AI 파이프라인을 Embed as API 기능으로 손쉽게 외부 서비스에 연결해보세요.
* **튜토리얼:** 문서 기반 Q\&A 봇,  MCP를 활용한 에이전트 만들기 등 특정 활용 사례 가이드를 따릅니다.



