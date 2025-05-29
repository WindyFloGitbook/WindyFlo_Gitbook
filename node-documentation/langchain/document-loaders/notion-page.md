# Notion Page

Notion Page 노드는 단일 Notion 페이지의 콘텐츠를 불러와 문서 객체(Document)로 변환합니다. 개별 회의록, 보고서, 정책 문서 등을 AI 응답에 바로 활용하고자 할 때 적합한 노드입니다.

***

### 주요 기능

* 단일 Notion 페이지의 콘텐츠를 API를 통해 자동 수집
* 페이지 내용을 pageContent로 변환하여 문서 객체로 출력
* 불필요한 메타데이터 제거 및 사용자 지정 메타데이터 삽입 가능
* Text Splitter와 연계하여 긴 페이지를 자동 분할 가능

<figure><img src="../../../.gitbook/assets/image (35).png" alt=""><figcaption><p>WindyFlo Notion Page</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (36).png" alt=""><figcaption><p>WindyFlo Notion Page Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                    | 필수 여부 |
| ------------------ | ------------------------------------- | ----- |
| Connect Credential | Notion API 접근용 인증 토큰 (Credential에 등록) | 필수    |
| Notion Page Id     | 수집할 Notion 페이지의 고유 ID                 | 필수    |
| Text Splitter      | 페이지 내용을 분할하는 데 사용할 Text Splitter 노드   | 선택    |

***

### 파라미터 (Parameters)

| 항목                  | 설명                                                  |
| ------------------- | --------------------------------------------------- |
| Additional Metadata | 문서에 삽입할 메타데이터 (정적 JSON 또는 경로 매핑 가능)                 |
| Omit Metadata Keys  | 결과 문서에서 제거할 메타데이터 키 목록 (예: created\_time, author 등) |

***

### 출력값 (Outputs)

| 출력 항목    | 설명                                 |
| -------- | ---------------------------------- |
| Document | pageContent 및 메타데이터를 포함한 문서 객체 리스트 |
| Text     | pageContent 전체를 병합한 단일 텍스트         |

***

### 활용 예시

* 개별 Notion 문서를 AI 챗봇에 불러와 질의응답 소스로 활용
* 주요 정책 문서를 텍스트화하여 버전 관리 및 검색 기반 시스템에 적용
* 페이지 하나만 수집해 요약 또는 번역 파이프라인으로 넘길 때 사용

***

### 사용 팁

* Notion Page Id는 공유 링크의 URL 끝에서 확인 가능
* 내용이 긴 경우 반드시 Text Splitter 노드를 연결해 분할 처리
* Additional Metadata를 통해 태그, 작성자, 작성일 등 정보를 포함 가능

***

### 주의사항

* Credential 누락 시 접근 권한 오류 발생
* 페이지 공유 설정이 ‘비공개’일 경우 로딩 불가
* 표, 이미지, 임베디드 블록 등은 텍스트로 정확히 변환되지 않을 수 있음
