# Advanced Structured Output Parser

Advanced Structured Output Parser 노드는 Zod 스키마를 사용하여 LLM의 출력 결과를 정밀하게 구조화할 수 있는 고급 JSON 파서입니다. 배열, 열거형(enum), 문자열 길이 제한 등 복잡한 조건을 반영할 수 있으며, `Autofix` 기능을 통해 출력 오류도 보정할 수 있습니다.

***

### 주요 기능

* Zod 기반 스키마를 활용해 복잡한 JSON 구조 정의
* 문자열 길이, 숫자 타입, enum 목록 등 다양한 데이터 조건 지정 가능
* 다중 항목 배열, 중첩 구조 등 고급 출력 포맷 제어 지원
* `Autofix` 기능을 통해 스키마 불일치 시 자동 수정 가능

<figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption><p>WindyFlo Advanced Structured Output Parser</p></figcaption></figure>

### 입력값 (Inputs)

| 항목           | 설명                                                                                           | 필수 여부 |
| ------------ | -------------------------------------------------------------------------------------------- | ----- |
| Autofix      | 모델 출력이 스키마 조건과 일치하지 않을 경우, 한 번 더 모델을 호출하여 오류를 보정                                             | 선택    |
| Example JSON | <p>출력 구조를 정의하는 Zod 스키마 형식의 예시 입력<br>예: <code>z.object({ title: z.string(), ... })</code></p> | 필수    |

***

### 출력값 (Outputs)

| 출력 항목                          | 설명                             |
| ------------------------------ | ------------------------------ |
| AdvancedStructuredOutputParser | 정의된 Zod 스키마에 따라 파싱된 JSON 객체 반환 |

***

### 활용 예시

* 영화 정보, 제품 스펙, 정책 항목 등 복잡한 구조 데이터를 정제하여 응답 받을 때
* 문자열 조건(`max(500)`), 숫자(`.int()`), enum 배열 등 정밀 제어가 필요한 경우
* LLM이 생성하는 결과를 특정 형식(JSON 스펙)에 맞춰 후속 처리하거나 저장하는 경우
* JSON 조건을 엄격하게 맞춰야 하는 API 연동, 자동 보고서 생성 등에 활용 가능

***

### 사용 팁

* **Zod 스키마**는 `z.object({...})` 구조로 작성하며, `string()`, `number()`, `enum([...])`, `array()` 등 다양한 제약을 지정할 수 있습니다.
* `Autofix` 옵션은 스키마 불일치 시 모델을 재호출하여 포맷 오류를 자동으로 수정합니다. 단, 토큰이 추가 소모됩니다.
*   예시:

    ```ts
    z.object({
        title: z.string(), // Title of the movie as a string
        yearOfRelease: z.number().int(), // Release year as an integer number,
        genres: z.enum([
            "Action", "Comedy", "Drama", "Fantasy", "Horror",
            "Mystery", "Romance", "Science Fiction", "Thriller", "Documentary"
        ]).array().max(2), // Array of genres, max of 2 from the defined enum
        shortDescription: z.string().max(500) // Short description, max 500 characters
    })
    ```
* 구조가 너무 복잡하거나 중첩이 많을 경우, 모델 출력 정확도가 낮아질 수 있으므로 가능한 한 단순한 구조를 권장합니다.

***

### 주의사항

* 스키마 구조와 LLM 출력이 일치하지 않으면 파싱 오류가 발생할 수 있으며, Autofix 없이 사용할 경우 해당 결과는 무시됩니다.
* `enum` 항목은 사전에 정의한 값 이외의 문자열을 허용하지 않으므로, 프롬프트에서 명확한 가이드를 제공해야 합니다.
* 출력값이 배열일 경우 `.array()` 설정을 반드시 포함해야 합니다.
* `Autofix` 사용 시 비용이 2배로 발생할 수 있으므로, 필요한 경우에만 사용하세요.
