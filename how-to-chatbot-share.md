# ✨ How to Chatbot Share

## 파이프라인 배포: 웹사이트 임베드 및 API 활용 ('Embed as API')

이 가이드에서는 WindyFlo 파이프라인을 웹사이트에 통합하거나, 프로그래밍 방식으로 호출하거나, 독립적인 챗봇 링크로 공유하는 방법을 설명합니다. 모든 배포 옵션은 파이프라인 편집 화면의 **Embed as API** 버튼을 통해 접근할 수 있습니다.

&#x20;**Embed as API** 버튼을 클릭하면 아래와 같은 팝업 창이 나타납니다.

<figure><img src=".gitbook/assets/000 ~ 005.png" alt=""><figcaption></figcaption></figure>

이 팝업 창은 다음과 같은 주요 배포 방식을 제공합니다:

1. **웹사이트 임베드:** 웹사이트에 챗봇 위젯을 직접 삽입합니다 (Embed 탭).
2. **프로그래밍 API 호출:** 서버나 애플리케이션에서 파이프라인을 직접 호출합니다 (Python, JavaScript, cURL 탭).
3. **독립 챗봇 공유:** 간편하게 공유할 수 있는 웹 챗봇 링크를 생성합니다 (Share Chatbot 탭).

***

### 1. 웹사이트에 챗봇 위젯 임베드 (Embed 탭)

웹사이트 방문자가 직접 상호작용할 수 있는 챗봇 인터페이스를 추가하는 가장 일반적인 방법입니다.

#### 가. 임베드 형식 선택

Embed 탭 내에서 웹사이트 디자인과 필요에 맞는 형식을 선택합니다.

* **Popup Html:** 웹페이지에 작은 버튼을 추가하고, 클릭 시 팝업 형태의 챗봇 창이 나타납니다. (스크린샷 예시)
* **Fullscreen Html:** 웹페이지 전체를 챗봇 인터페이스로 사용합니다.
* **Popup React / Fullscreen React:** React 프레임워크를 사용하는 웹사이트에 통합하기 위한 컴포넌트 코드입니다.

#### 나. 코드 스니펫 적용

선택한 형식에 따라 제공되는 코드 스니펫을 복사하여 웹사이트의 HTML 코드에 삽입합니다. 일반적으로 \<script> 태그 형태이며, \<body> 태그 내부에 위치시키는 것이 좋습니다.

```
<!-- 예시: Popup Html 스니펫 (스크린샷 기반) -->
<script type="module">
  // WindyFlo 챗봇 라이브러리 임포트
  import Chatbot from "https://cdn.jsdelivr.net/npm/windyflo-embed@<version>/dist/web.js" // 필요시 버전 지정

  // 챗봇 초기화
  Chatbot.init({
    chatflowid: "b76dccea-4ce5-4a10-9470-a50151107759", // 여기에 실제 파이프라인 ID가 자동으로 채워집니다
    apiHost: "https://www.windyflo.com", // WindyFlo 서비스 주소
    // ... 추가 설정 옵션 (아래 '다. 설정 사용자 정의' 참조)
  })
</script>
```

content\_copydownloadUse code [with caution](https://support.google.com/legal/answer/13505487).Html

#### 다. 설정 사용자 정의 (Chatbot.init 옵션)

Chatbot.init({...}) 객체 내부에 다양한 옵션을 추가하여 챗봇의 동작과 모양을 사용자 정의할 수 있습니다.

* **chatflowid (필수):** 임베드하려는 WindyFlo 파이프라인의 고유 ID입니다. 코드가 생성될 때 자동으로 채워집니다.
* **apiHost (필수):** WindyFlo 서비스의 호스트 주소입니다. 일반적으로 자동으로 채워집니다.
* **theme (선택 사항):** 챗봇 위젯의 시각적 테마를 설정합니다. (예: 색상, 폰트 등. 사용 가능한 옵션은 WindyFlo 테마 가이드 참조)
*   **chatWindow (선택 사항):** 챗봇 창의 제목, 초기 메시지 등을 설정합니다.

    ```
    chatWindow: {
      title: "WindyFlo 챗봇",
      welcomeMessage: "안녕하세요! 무엇을 도와드릴까요?",
      // ... 기타 창 관련 설정
    }
    ```

    content\_copydownloadUse code [with caution](https://support.google.com/legal/answer/13505487).JavaScript
*   **button (선택 사항):** (Popup 형식 사용 시) 팝업 버튼의 아이콘, 색상, 위치 등을 설정합니다.

    **팁:** 팝업 창 하단의 **Show Embed Chat Config** 체크박스를 선택하면, 이러한 설정들을 시각적으로 조정하고 해당 설정값이 포함된 Chatbot.init 코드를 얻을 수 있습니다. (실제 기능 확인 필요)

***

### 2. 프로그래밍 방식 API 호출 (Python, JavaScript, cURL 탭)

서버 백엔드, 모바일 앱 또는 기타 자동화 스크립트에서 WindyFlo 파이프라인의 기능을 직접 호출하고 결과를 받아 처리하는 방식입니다.

1. **언어 탭 선택:** Python, JavaScript, cURL 등 사용하려는 프로그래밍 환경에 맞는 탭을 선택합니다.
2. **코드 예제 확인:** 선택한 언어로 작성된 API 호출 예제 코드가 제공됩니다. 이 코드는 일반적으로 다음 요소를 포함합니다:
   * **요청 URL:** 파이프라인의 고유 API 엔드포인트 주소.
   * **HTTP 메소드:** 보통 POST.
   * **헤더:** Content-Type: application/json 및 필요한 경우 Authorization 헤더.
   * **요청 본문(Body/Payload):** 파이프라인에 전달할 입력 데이터를 담는 JSON 객체. 이 구조는 파이프라인의 입력 노드 구성에 따라 달라집니다.
3. **코드 적용:** 제공된 예제 코드를 복사하여 자신의 애플리케이션 코드에 통합합니다. 실제 사용 시에는 입력 데이터를 동적으로 구성하고, API로부터 받은 응답(JSON)을 파싱하여 활용하는 로직을 구현해야 합니다.

***

### 3. 독립 챗봇으로 공유 (Share Chatbot 탭)

가장 간단하게 파이프라인을 공유하는 방법으로, 고유한 URL을 가진 독립적인 웹 챗봇 페이지를 생성합니다.

1. **Share Chatbot 탭 선택:** 팝업 창 상단의 Share Chatbot 탭을 클릭합니다.
2. **설정 조정:** 챗봇 페이지의 제목(Title), 환영 메시지(Welcome Message) 등을 원하는 대로 수정합니다.
3. **URL 생성 및 공유:** 설정을 저장하면 고유한 공유 URL이 생성됩니다. 이 URL을 복사하여 다른 사람에게 전달하면, WindyFlo 계정 없이도 누구나 해당 챗봇과 대화할 수 있습니다. 데모 시연이나 빠른 피드백 수집에 유용합니다.

***

### 4. 보안: API 인증 설정 (Authorization)

파이프라인 API를 보호해야 하는 경우, API 키 기반 인증을 설정할 수 있습니다.

1. **인증 설정 접근:** 'Embed as API' 팝업 창 우측 상단의 Authorization 드롭다운 메뉴를 클릭합니다. (기본값: No Authorization)
2. **API 키 생성/선택:**
   * Create New API Key (또는 유사 명칭)를 선택하여 새 API 키를 생성하고 이름을 지정합니다.
   * 이미 생성된 키가 있다면 목록에서 선택합니다.
3.  **API 키 사용:**

    * **프로그래밍 방식 API 호출 시:** 생성된 API 키 값을 복사하여 HTTP 요청의 Authorization 헤더에 포함시켜야 합니다. (일반적으로 Bearer \<YOUR\_API\_KEY> 형식)
    * **웹사이트 임베드 또는 챗봇 공유 시:** 인증 설정이 적용된 상태로 코드가 생성되거나 링크가 작동할 수 있습니다. (내부 처리 방식은 WindyFlo 구현에 따름)

    **주의:** API 키는 민감한 정보이므로 안전하게 관리해야 합니다. 자세한 내용은 [API 보안 가이드](https://www.google.com/url?sa=E\&q=.%2Fapi-security.md)를 참조하세요.

***

이제 'Embed as API' 기능을 통해 제공되는 다양한 옵션을 활용하여 WindyFlo 파이프라인을 목적에 맞게 효과적으로 배포할 수 있습니다.
