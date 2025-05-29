# Figma

Figma 디자인 파일에서 특정 노드의 텍스트 콘텐츠를 추출하여 문서(Document) 형식으로 변환하는 로더 노드입니다. UI 텍스트, 컴포넌트 설명 등 디자인 기반 콘텐츠를 AI 파이프라인에 통합할 수 있습니다.

***

#### 주요 기능

* Figma API를 통해 디자인 파일 내 텍스트 요소 추출
* Node ID를 지정하여 원하는 요소만 선택적 로딩 가능
* 재귀 설정으로 하위 컴포넌트까지 탐색 가능
* 추출된 텍스트는 Document 형태로 LLM 파이프라인에 활용 가능
* Text Splitter와 연동하여 장문의 UI 텍스트도 안정적으로 처리 가능

<figure><img src="../../../.gitbook/assets/image (48).png" alt=""><figcaption><p>WindyFlo Figma</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (49).png" alt=""><figcaption><p>WindyFlo Figma Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                 | 설명                                               | 필수 여부         |
| ------------------ | ------------------------------------------------ | ------------- |
| Text Splitter      | 추출된 텍스트 분할 처리용 노드 연결                             | 선택            |
| Connect Credential | Figma Personal Access Token을 Credential에 등록 후 선택 | 필수            |
| File Key           | 대상 Figma 파일의 고유 키 (파일 URL에서 확인 가능)               | 필수            |
| Node IDs           | 텍스트 추출 대상 Figma 노드 ID 목록 (쉼표로 구분)                | 필수            |
| Recursive          | 하위 노드까지 텍스트를 재귀적으로 추출할지 여부                       | 선택 (기본값: 비활성) |

***

#### 파라미터 (Parameters)

| 항목                  | 설명                                                      |
| ------------------- | ------------------------------------------------------- |
| Additional Metadata | 문서에 추가할 사용자 정의 메타데이터 (예: 컴포넌트명, 화면 정보 등)                |
| Omit Metadata Keys  | 제외할 metadata 키 목록 (쉼표 구분, 예: `id, absoluteBoundingBox`) |

***

#### 출력값 (Outputs)

| 출력 항목    | 설명                                 |
| -------- | ---------------------------------- |
| Document | 추출된 텍스트와 메타데이터로 구성된 문서 객체 배열       |
| Text     | 모든 텍스트 콘텐츠를 하나로 병합한 문자열 (선택 출력 형식) |

***

#### 활용 예시

* UI 문구를 추출하여 다국어 번역 및 LLM 기반 카피 생성에 활용
* 디자인 기반 설명 텍스트를 추출하여 온보딩 문서 자동 생성
* Figma에 입력된 가이드 내용을 추출해 QA 파이프라인 연동
* 컴포넌트별 문서를 추출하여 제품 매뉴얼 제작
* 예: 버튼, 입력창, 모달 등 UI 요소에 기입된 문구 자동 수집
* 다국어 현지화 전 사전 문구 분류 및 AI 감수 적용
* 사용자 가이드 생성 자동화 파이프라인 구축

***

#### 사용 팁

* File Key는 Figma 파일 URL 중 `/file/` 다음에 오는 값
* Node ID는 Figma에서 'Copy as JSON' 또는 개발자 콘솔을 통해 확인 가능
* Recursive 옵션 활성화 시, 자식 노드까지 전체 탐색하므로 속도 고려 필요
* Text Splitter를 연결하면 UI 설명이 긴 경우에도 안정적 처리 가능

***

#### 주의사항

* Credential 누락 시 API 인증 실패로 동작하지 않음
* Node ID가 유효하지 않거나 비어 있을 경우 텍스트 추출 불가
* Figma 파일 내 텍스트가 없는 경우 빈 Document 반환
* 재귀 설정이 과도할 경우 처리 시간이 길어질 수 있음
