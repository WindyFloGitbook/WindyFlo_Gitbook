# Github

Github 노드는 지정한 Github 리포지토리의 파일을 불러와 문서 객체(Document)로 변환합니다. 코드 저장소 내 문서 또는 소스코드 주석 기반의 AI 파이프라인 구축에 유용하며, 대규모 기술 리포지토리 자동 수집에도 적합합니다.

***

#### 주요 기능

* 지정된 Github 리포지토리와 브랜치의 파일을 로드하여 문서 객체로 변환
* Markdown 등 특정 확장자 제외 또는 포함 지정 가능
* 불필요한 메타데이터 필터링 및 사용자 지정 메타데이터 삽입 가능
* Text Splitter와 연계하여 코드 기반 문서를 자동 분할 가능

<figure><img src="../../../.gitbook/assets/image (58).png" alt=""><figcaption><p>WindyFlo Github</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (59).png" alt=""><figcaption><p>WindyFlo Github Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                 | 설명                                                                                             | 필수 여부 |
| ------------------ | ---------------------------------------------------------------------------------------------- | ----- |
| Connect Credential | Github API 접근을 위한 인증 Credential에 등록된 항목                                                        | 선택    |
| Repo Link          | 수집할 리포지토리 주소 (예: [https://github.com/FlowiseAI/Flowise](https://github.com/FlowiseAI/Flowise)) | 필수    |
| Branch             | 수집 대상 브랜치명 (예: main, dev 등)                                                                    | 필수    |
| Recursive          | 하위 폴더까지 탐색할지 여부 (기본값: false)                                                                   | 선택    |
| Text Splitter      | 불러온 문서의 텍스트를 분할하는 데 사용할 Text Splitter 노드                                                       | 선택    |

***

#### 파라미터 (Parameters)

| 항목                  | 설명                                                             |
| ------------------- | -------------------------------------------------------------- |
| Max Concurrency     | 동시 처리 요청 수 제한 (예: 5)                                           |
| Github Base URL     | Github Enterprise 등 사용할 경우 custom base URL                     |
| Github Instance API | API 경로 (기본값: [https://api.github.com](https://api.github.com)) |
| Ignore Paths        | 무시할 파일 또는 디렉터리 경로 (예: \["\*.md", "tests/"])                    |
| Max Retries         | 요청 실패 시 재시도 횟수                                                 |
| Additional Metadata | 수집 문서에 부여할 사용자 정의 메타데이터 (JSON 형식)                              |
| Omit Metadata Keys  | 제외할 메타데이터 키 목록 (예: `key1, key2`)                               |

***

#### 출력값 (Outputs)

| 출력 항목    | 설명                                 |
| -------- | ---------------------------------- |
| Document | pageContent 및 메타데이터를 포함한 문서 객체 리스트 |
| Text     | 모든 문서의 pageContent를 하나의 문자열로 병합한 값 |

***

#### 활용 예시

* Github 저장소의 README, `.md` 문서 등을 기반으로 기술 매뉴얼 검색 시스템 구성
* 코드에 포함된 함수 주석 등을 AI가 요약/검색할 수 있도록 처리
* 오픈소스 프로젝트 문서를 주기적으로 크롤링하여 최신 문서 반영

***

#### 사용 팁

* 대용량 저장소의 경우 `Ignore Paths`로 필요 없는 경로를 제외하여 성능 최적화
* `Recursive` 옵션을 켜면 하위 디렉토리까지 수집되므로, 전체 구조 기반 작업에 적합
* `Text Splitter` 연결 시 코드 단위 또는 주석 단위로 세밀하게 분할 가능

***

#### 주의사항

* 인증이 필요한 Private Repo는 `Connect Credential`에 토큰 등록 필수
* Markdown 확장자만 포함되거나 제외된 경우, AI 분석 정확도가 낮아질 수 있음
* 리포지토리 구조가 복잡할수록 처리 시간이 증가하므로 병렬 처리 설정을 적절히 조정해야 함
