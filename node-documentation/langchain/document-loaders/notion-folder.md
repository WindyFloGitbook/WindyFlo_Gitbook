# Notion Folder

Notion Folder 노드는 지정한 Notion 폴더 경로 내 모든 페이지를 불러와 문서 객체(Document)로 변환합니다. 비정형 콘텐츠를 다수 보관 중인 Notion 폴더 구조에서 손쉽게 데이터를 수집하고 AI 파이프라인에 연동할 수 있습니다.

***

### 주요 기능

* 지정된 Notion 폴더 내 모든 페이지 콘텐츠를 자동 수집
* 각 페이지를 pageContent로 변환하여 문서 객체로 출력
* 불필요한 메타데이터를 제외하거나 사용자 지정 메타데이터 삽입 가능
* Text Splitter 연계를 통해 긴 페이지도 효율적으로 분할 가능

<figure><img src="../../../.gitbook/assets/image (33).png" alt=""><figcaption><p>WindyFlo Notion Folder</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (34).png" alt=""><figcaption><p>WindyFlo Notion Folder Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목            | 설명                                    | 필수 여부 |
| ------------- | ------------------------------------- | ----- |
| Notion Folder | 수집 대상 Notion 폴더의 전체 경로 (URL 또는 경로 ID) | 필수    |
| Text Splitter | 페이지 내용을 분할하는 데 사용할 Text Splitter 노드   | 선택    |

***

### 파라미터 (Parameters)

| 항목                  | 설명                                              |
| ------------------- | ----------------------------------------------- |
| Additional Metadata | 각 문서에 삽입할 추가 메타데이터 (JSON 형식 또는 경로 매핑 사용 가능)     |
| Omit Metadata Keys  | 결과 문서에서 제거할 메타데이터 키 목록 (예: id, created\_time 등) |

***

### 출력값 (Outputs)

| 출력 항목    | 설명                              |
| -------- | ------------------------------- |
| Document | 각 페이지를 변환한 문서 객체 리스트            |
| Text     | 전체 페이지의 pageContent를 병합한 단일 텍스트 |

***

### 활용 예시

* 프로젝트별로 분류된 Notion 폴더의 자료를 수집하여 검색 가능한 지식 저장소로 구축
* 회의록, 작업 로그 등 누적되는 문서를 자동 벡터화하여 유사 문서 추천에 활용
* 마케팅/영업 콘텐츠 문서를 수집하여 요약 응답용 챗봇에 적용

***

### 사용 팁

* 폴더 경로는 공유 가능한 URL 또는 내부 ID를 정확히 입력해야 정상 작동
* 여러 하위 페이지를 포함한 경우 Text Splitter를 연결하면 처리 효율 향상
* Additional Metadata를 설정하면 각 문서에 팀명, 프로젝트명 등을 태깅 가능

***

### 주의사항

* 권한 설정이 올바르지 않거나 공유가 비활성화된 페이지는 불러올 수 없음
* 데이터가 많을수록 로딩 시간이 길어질 수 있으므로 사전 분류된 폴더 구조 권장
* Notion 페이지 구조 상, 텍스트 외 미디어/표 등은 제대로 수집되지 않을 수 있음
