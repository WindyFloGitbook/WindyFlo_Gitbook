# S3 Directory

S3 Directory 노드는 Amazon S3 버킷의 특정 경로(디렉토리) 내 파일들을 불러와 문서 객체(Document)로 일괄 변환합니다. 다수의 문서 파일을 정기적으로 불러와 자동 처리하거나 분석 파이프라인에 투입하는 데 적합합니다.

***

### 주요 기능

* 지정한 S3 버킷 경로 내의 모든 파일을 자동 수집 및 로딩
* PDF 파일에 대해 페이지 단위 또는 파일 단위 분할 처리 가능
* Text Splitter 연계를 통해 긴 텍스트 자동 분할 가능
* 메타데이터 삽입 및 불필요한 필드 제거 기능 제공

<figure><img src="../../../.gitbook/assets/image (23).png" alt=""><figcaption><p>WindyFlo S3 Directory</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (24).png" alt=""><figcaption><p>WindyFlo S3 Directory Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목            | 설명                                           | 필수 여부 |
| ------------- | -------------------------------------------- | ----- |
| Credential    | S3 접근 권한용 인증 정보 (Credential에 등록)             | 필수    |
| Bucket        | 대상 S3 버킷 이름                                  | 필수    |
| Region        | 버킷이 속한 AWS 리전 (예: us-east-1)                 | 필수    |
| Server URL    | S3 호환 스토리지 사용 시 커스텀 서버 주소                    | 선택    |
| Prefix        | 불러올 파일이 위치한 S3 디렉토리 경로 (예: `myfolder/data/`) | 선택    |
| Text Splitter | 불러온 텍스트를 분할하는 데 사용할 Text Splitter 노드         | 선택    |

***

### 파라미터 (Parameters)

| 항목                  | 설명                                       |
| ------------------- | ---------------------------------------- |
| Pdf Usage           | PDF 파일 처리 방식: 페이지별 또는 파일별 문서로 처리         |
| Additional Metadata | 문서에 삽입할 추가 메타데이터 (예: { "source": "s3" }) |
| Omit Metadata Keys  | 제거할 메타데이터 키 목록 (쉼표 구분 입력)                |

***

### 출력값 (Outputs)

| 출력 항목    | 설명                             |
| -------- | ------------------------------ |
| Document | 파일별 또는 페이지별로 생성된 문서 객체 리스트     |
| Text     | 모든 pageContent를 병합한 단일 텍스트 문자열 |

***

### 활용 예시

* 사내 저장소(S3)에 업로드된 보고서, 매뉴얼 등을 자동 수집해 요약 처리
* 고객사가 업로드한 파일을 실시간 문서 분석 또는 벡터화 파이프라인으로 연결
* 백오피스 PDF 파일을 수집해 검색 가능한 지식베이스 구축

***

### 사용 팁

* 다량의 PDF를 처리할 경우 `Pdf Usage`를 “One document per page”로 설정하면 성능이 개선됨
* `Prefix`를 지정하면 원하는 하위 폴더만 불러올 수 있어 효율적인 필터링 가능
* S3 외 스토리지 사용 시 Server URL 항목을 통해 호환 API 설정 가능

***

### 주의사항

* Credential 등록 누락 시 S3 버킷 접근이 불가능함
* PDF 이외의 파일 형식은 자동 처리되지 않으며, 지원 확장은 환경 설정에 따라 다를 수 있음
* 리전에 맞지 않는 설정 또는 잘못된 버킷명 입력 시 로딩 실패 발생 가능
