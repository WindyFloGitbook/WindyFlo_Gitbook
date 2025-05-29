# Epub File

전자책 형식의 `.epub` 파일을 업로드하고, 챕터 단위 또는 전체 파일 단위로 문서(Document)로 변환하는 로더 노드입니다. 책 형태의 콘텐츠를 AI 파이프라인에서 활용하고자 할 때 유용합니다.

***

#### 주요 기능

* `.epub` 형식 전자책 파일을 문서 객체로 변환
* 챕터 단위 또는 전체 파일 단위 문서화 선택 가능
* Text Splitter와 연결하여 장문 분할 처리 가능
* 사용자 정의 메타데이터 추가 및 필요 없는 키 제외 가능
* 구조화된 콘텐츠를 LLM 기반 파이프라인에서 활용 가능

<figure><img src="../../../.gitbook/assets/image (47).png" alt=""><figcaption><p>WindyFlo Epub File</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 142551 (2).png" alt=""><figcaption><p>WindyFlo Epub File Parameters</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목            | 설명                                  | 필수 여부 |
| ------------- | ----------------------------------- | ----- |
| Text Splitter | 긴 텍스트 분할 처리용 노드 연결                  | 선택    |
| Epub File     | 업로드할 .epub 파일                       | 필수    |
| Usage         | 문서 생성 방식 선택 (챕터별 문서 or 전체 파일 통합 문서) | 필수    |

_Usage 옵션:_

* **One document per chapter**: 각 챕터를 개별 Document로 분리
* **One document per file**: 전체 콘텐츠를 하나의 Document로 생성

***

#### 파라미터 (Parameters)

| 항목                  | 설명                                              |
| ------------------- | ----------------------------------------------- |
| Additional Metadata | 각 문서에 추가할 사용자 정의 메타데이터                          |
| Omit Metadata Keys  | 제외할 metadata 키 목록 (쉼표 구분, 예: `title, location`) |

***

#### 출력값 (Outputs)

| 출력 항목    | 설명                                   |
| -------- | ------------------------------------ |
| Document | pageContent + metadata로 구성된 문서 객체 배열 |
| Text     | 전체 문서의 텍스트를 하나로 병합한 문자열 (선택 출력 형식)   |

***

#### 활용 예시

* 사내 교육자료 또는 가이드북을 챕터 단위로 나눠 파이프라인에 연결
* 기술 문서를 전자책으로 변환 후 요약/검색 파이프라인에 적용
* 전자책 기반으로 독서 요약 챗봇 제작
* 지식 기반 콘텐츠를 RAG 파이프라인에 적재
* 챕터별 FAQ 생성 파이프라인 구축
* 학습 자료를 AI 요약 파이프라인으로 연동
* 전체 전자책 내용을 하나의 문서로 처리하여 질의응답 가능

***

#### 사용 팁

* 챕터별 분할이 필요한 경우 "One document per chapter"로 설정
* Text Splitter와 연결 시 장문의 챕터도 안정적으로 처리 가능
* 불필요한 metadata 필드는 `Omit Metadata Keys`로 제거 가능
* ePub 형식은 HTML 기반이므로 다양한 서식 정보를 그대로 유지함

***

#### 주의사항

* `.epub` 외 다른 전자책 포맷(mobi, azw 등)은 지원되지 않음
* 문서 구조가 비표준인 ePub 파일은 챕터 분할이 정확하지 않을 수 있음
* 텍스트 외의 삽화, 표 등은 일부 누락되거나 비정상 처리될 수 있음
* 챕터 수가 많은 경우 Document 객체 수 증가로 성능 저하 가능
