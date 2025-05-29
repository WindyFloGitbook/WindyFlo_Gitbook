# Notion Database

Notion Database 노드는 지정한 Notion 데이터베이스에서 모든 페이지 데이터를 가져와 문서 객체(Document)로 변환합니다. 사내 위키, 회의록, 프로젝트 로그 등의 정보를 AI 파이프라인에서 직접 활용할 수 있습니다.

***

### 주요 기능

* Notion API를 통해 특정 Database의 전체 데이터를 자동 수집
* 각 페이지를 pageContent 형태로 변환하여 문서 객체로 출력
* 사용자 지정 메타데이터 삽입 및 불필요한 메타데이터 제거 가능
* Text Splitter 연결 시 각 페이지를 소단위로 분할 처리 가능

<figure><img src="../../../.gitbook/assets/image (31).png" alt=""><figcaption><p>WindyFlo Notion Database</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (32).png" alt=""><figcaption><p>WindyFlo Notion Database Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                  | 필수 여부 |
| ------------------ | ----------------------------------- | ----- |
| Connect Credential | Notion API 인증 토큰 (Credential에 등록)   | 필수    |
| Notion Database Id | 데이터 수집 대상 Notion Database의 고유 ID    | 필수    |
| Text Splitter      | 페이지 내용을 분할하는 데 사용할 Text Splitter 노드 | 선택    |

***

### 파라미터 (Parameters)

| 항목                  | 설명                                    |
| ------------------- | ------------------------------------- |
| Additional Metadata | 각 문서에 삽입할 추가 메타데이터 (정적 값 또는 동적 매핑 가능) |
| Omit Metadata Keys  | 결과 문서에서 제거할 메타데이터 키 목록 (쉼표로 구분)       |

***

### 출력값 (Outputs)

| 출력 항목    | 설명                              |
| -------- | ------------------------------- |
| Document | 각 페이지를 변환한 문서 객체 리스트            |
| Text     | 전체 페이지의 pageContent를 병합한 단일 텍스트 |

***

### 활용 예시

* Notion으로 관리하던 회의록, 기획 문서를 AI 질의 응답에 바로 활용
* 프로젝트 로그를 정기적으로 수집해 자동 보고서 생성 파이프라인 구성
* 팀 내부 노하우를 벡터화하여 검색 가능한 지식베이스 구축

***

### 사용 팁

* Notion Database Id는 공유 링크에서 확인 가능하며, 전체 ID 값을 입력해야 정상 작동
* 데이터가 많은 경우 Text Splitter를 연결하여 chunk 단위로 나눠 성능 최적화
* Additional Metadata를 활용해 문서 유형, 작성자 등 추가 정보 태깅 가능

***

### 주의사항

* Notion API 제한으로 인해 대규모 데이터 로드 시 시간 지연 발생 가능
* Credential 누락 시 데이터 접근이 불가능하므로 반드시 등록 필요
* 비공개 Database는 공유 및 통합 권한 설정이 선행되어야 함
