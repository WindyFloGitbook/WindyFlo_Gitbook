# OpenAI Assistant

**OpenAI Assistant 노드**는 OpenAI의 Assistant API를 활용해 생성된 **프리셋 기반 대화형 에이전트**를 WindyFlo 파이프라인 내에서 사용할 수 있도록 하는 노드입니다. 사용자는 OpenAI 플랫폼에서 미리 정의한 Assistant를 선택해 자연어 질의, 툴 호출, 파일 처리 등 복합 작업을 자동화할 수 있습니다.

***

### 주요 기능

* **사전 정의된 Assistant 연결**: OpenAI에서 미리 만든 Assistant를 선택해 사용
* **툴 연동**: Allowed Tools 설정을 통해 외부 도구 사용 가능 (예: 파일 검색, 계산기 등)
* **병렬 처리 가능**: 복수의 툴을 동시에 호출해 실행 속도 향상
* **파일 다운로드 차단 설정**: 응답에서 파일 다운로드 허용 여부 설정

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-08 164226.png" alt=""><figcaption><p>WindyFlo OpenAI Assistant</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-08 164237.png" alt=""><figcaption><p>WindyFlo OpenAI Assistant Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                   | 설명                                      | 필수 여부 |
| -------------------- | --------------------------------------- | ----- |
| **Allowed Tools**    | Assistant가 사용할 수 있도록 허용된 도구 목록입니다.      | 필수    |
| **Input Moderation** | 유해하거나 부적절한 입력을 필터링할지 여부                 | 선택    |
| **Select Assistant** | OpenAI 플랫폼에서 생성된 Assistant 중 연결할 항목을 선택 | 필수    |

***

### 파라미터 (Parameters)

| 항목                        | 설명                                              |
| ------------------------- | ----------------------------------------------- |
| **Tool Choice**           | 사용할 툴을 직접 지정하거나 자동 선택하도록 설정. 예: `file_search` 등 |
| **Parallel Tool Calls**   | 툴을 **동시에 병렬로 호출**할지 여부 설정 (기본: 활성화됨)            |
| **Disable File Download** | 생성된 파일 다운로드 기능을 **비활성화할지 여부** 설정 (기본: 허용됨)      |

***

### 출력값 (Outputs)

| 출력 항목               | 설명                                   |
| ------------------- | ------------------------------------ |
| **OpenAIAssistant** | OpenAI Assistant를 통해 생성된 응답 또는 실행 결과 |

***

### 활용 예시

1. **지식 기반 챗봇**\
   → OpenAI에서 제작한 정책 설명 Assistant를 연결\
   → “반품 정책 안내해줘” → 저장된 정책 문서에서 내용 추출 후 요약 응답
2. **문서 검색 + 요약**\
   → file\_search 도구와 연동한 Assistant 사용\
   → “2024년 회의록 중 3월 분만 요약해줘” → 조건 검색 → 요약
3. **툴 병렬 실행**\
   → 복수 툴을 동시에 호출하여 응답 속도 향상\
   → “최근 이슈 요약하고 관련 문서 링크도 찾아줘” → 검색 + 링크 생성 병렬 수행

***

### 권장 사용 상황

* **사전에 정의된 역할 기반 에이전트를 활용하고 싶은 경우**
* **툴을 자동으로 조합해 복합 작업을 처리해야 할 경우**
* **OpenAI 플랫폼에서 Assistant를 이미 구성한 조직/사용자**

***

### 주의사항

* **Select Assistant**는 OpenAI 플랫폼에서 미리 만들어둔 Assistant가 있어야 선택 가능합니다.
* 병렬 툴 호출이 성능을 향상시킬 수 있으나, **트래픽이 많거나 응답이 무거운 툴 조합 시 오류가 발생할 수 있습니다.**
* 파일 다운로드를 제한해야 할 경우 `Disable File Download` 옵션을 활성화하세요.

***

OpenAI Assistant 노드는 WindyFlo에서 **OpenAI의 강력한 Assistant API를 직접 활용할 수 있는 인터페이스**를 제공합니다. 프리셋 에이전트 중심의 다양한 자동화 시나리오에 이상적입니다.
