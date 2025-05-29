# Custom Document Loader

JavaScript 코드를 기반으로 사용자가 직접 문서(Document)를 정의할 수 있는 로더 노드입니다. 외부 입력 없이도 동적으로 콘텐츠를 생성하거나, 특정 로직을 기반으로 문서 객체를 커스터마이징할 수 있습니다.

***

#### 주요 기능

* JavaScript 함수로 직접 Document 객체 반환 가능
* Input Variables를 통해 외부 입력과 동적 결합 처리
* 페이지 콘텐츠와 메타데이터를 자유롭게 조합하여 문서 생성
* 템플릿 기반 문서 생성, 샘플 데이터 테스트 등에 적합
* Text Splitter 연동으로 다량 콘텐츠 처리 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 133839.png" alt=""><figcaption><p>WindyFlo Custom Document Loader</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 133848.png" alt=""><figcaption><p>WindyFlo Custom Document Loader Input Variables</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                  | 설명                   | 필수 여부 |
| ------------------- | -------------------- | ----- |
| Input Variables     | 외부 노드에서 전달받을 변수들     | 선택    |
| Javascript Function | 문서 객체를 반환하는 JS 코드 입력 | 필수    |

_예시 코드:_

```javascript
return [
  {
    pageContent: 'Document Content',
    metadata: {
      title: 'Document Title',
    }
  }
]
```

***

#### 출력값 (Outputs)

| 출력 항목    | 설명                                                      |
| -------- | ------------------------------------------------------- |
| Document | JavaScript 함수에서 반환된 pageContent + metadata 형식의 문서 객체 배열 |
| Text     | 모든 문서를 텍스트로 병합한 문자열 (선택 출력 형식)                          |

***

#### 활용 예시

* 사전 정의된 템플릿 기반 Q\&A 문서 자동 생성
* 외부 입력(Input Variables)을 기반으로 실시간 문서 가공
* 자주 반복되는 기본 Document 객체를 생성하여 테스트 파이프라인 구축
* 사용자 정의 콘텐츠(공지사항, 안내문 등)를 LLM 입력으로 활용
* 간단한 테스트용 데이터 구성에 유용
* 입력값을 활용하여 다이내믹한 문서 생성 가능
* 메타데이터 기반 문서 필터링 전처리 가능

***

#### 사용 팁

* JavaScript 내부에서 반드시 `return [...]` 형식으로 반환해야 함
* `pageContent`는 문자열 필수, `metadata`는 객체 형태로 정의
* `Input Variables`와 함께 사용할 경우, 변수명을 정확히 지정해 호출 필요
* 코드 입력 후 반드시 Save 및 Execute 단계를 거쳐야 반영됨

***

#### 주의사항

* JavaScript 문법 오류 또는 `return` 누락 시 문서 생성 실패
* Input Variables는 연결 노드가 없으면 빈 값으로 처리됨
* 다량 문서를 생성할 경우 처리 시간이 길어질 수 있음
* 코드 내 데이터 하드코딩 시 유지보수 어려움 발생 가능
