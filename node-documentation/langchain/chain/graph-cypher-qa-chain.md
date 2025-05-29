# Graph Cypher QA Chain

**Graph Cypher QA Chain 노드**는 자연어 질문을 Cypher 쿼리로 변환하고, Neo4j 그래프 DB에서 실행한 결과를 바탕으로 자연어 응답을 생성하는 **그래프 질의응답용 체인 노드**입니다.\
그래프 데이터를 활용한 고급 분석 및 질문 응답 자동화를 구현할 수 있습니다.

***

### 주요 기능

* 자연어 질문 → Cypher 쿼리 자동 생성
* 쿼리 결과 → 자연어 응답으로 재구성
* Neo4j 연결 기반의 **지식 그래프 질의응답 시스템 구현**
* LLM을 사용한 질의 변환 및 해석 처리 분리 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-09 171155.png" alt=""><figcaption><p>WindyFlo Graph Cypher QA Chain</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                           | 설명                                            | 필수 여부 |
| ---------------------------- | --------------------------------------------- | ----- |
| **Language Model**           | 전체 질의 흐름을 제어하는 기본 LLM                         | 필수    |
| **Neo4j Graph**              | 연결할 Neo4j 인스턴스 정보                             | 필수    |
| **Cypher Generation Prompt** | 자연어 → Cypher 변환을 위한 프롬프트                      | 선택    |
| **Cypher Generation Model**  | Cypher 쿼리를 생성할 LLM (지정 시 Language Model과 분리됨) | 선택    |
| **QA Prompt**                | 쿼리 결과를 자연어 응답으로 바꾸기 위한 프롬프트                   | 선택    |
| **QA Model**                 | 응답 생성을 담당할 LLM (지정 시 Language Model과 분리됨)     | 선택    |
| **Input Moderation**         | 유해 질문 필터링 기능                                  | 선택    |
| **Return Direct**            | 쿼리 결과를 가공 없이 그대로 반환할지 여부 (기본값: 비활성화)          | 선택    |

***

### 출력값 (Outputs)

| 출력 항목                     | 설명                         |
| ------------------------- | -------------------------- |
| **Graph Cypher QA Chain** | 최종 자연어 응답 (기본 출력값)         |
| **Output Prediction**     | 내부 처리 결과 예측 값 (옵션 선택 시 노출) |

***

### 활용 예시

1. **지식 그래프 기반 Q\&A**
   * "마크 저커버그와 연결된 회사는?" → Cypher 쿼리로 변환 → 관계 추출 → 응답
2. **Neo4j 데이터 탐색 자동화**
   * "2023년 이후 생성된 모든 노드 수 보여줘" → 자동 쿼리 실행 및 응답 생성
3. **시각화 플랫폼과의 연계**
   * Cypher 결과를 그대로 반환해 시각화 도구로 전달 가능 (`Return Direct` 활성화 시)

***

### 사용 팁

* Cypher 쿼리 생성용 프롬프트는 **명확한 필드명 및 노드/관계 구조 설명 포함** 시 정확도 향상
* `QA Model`과 `Cypher Generation Model`을 분리하면 더 정밀한 컨트롤 가능
* 그래프 스키마가 복잡할 경우, 사전 예시와 함께 프롬프트 튜닝 필수

***

### 주의사항

* Neo4j 연결이 사전에 설정되어 있어야 작동합니다.
* `Cypher Generation Prompt`에는 `{question}` 변수가 포함되어야 하며, `QA Prompt`에는 `{result}` 변수가 포함되어야 합니다.
* 쿼리 결과가 비어 있거나 예상과 다를 경우, LLM이 부정확한 응답을 생성할 수 있습니다.

***

Graph Cypher QA Chain은 WindyFlo에서 **Neo4j 그래프 기반 분석을 자동화하고 질의응답 서비스를 구현할 수 있는 핵심 노드**입니다.\
그래프 DB 기반의 비즈니스 인사이트 추출, 관계 네트워크 분석, 지식 기반 챗봇 등에서 활용할 수 있습니다.
