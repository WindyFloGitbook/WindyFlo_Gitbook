# DynamoDB Chat Memory

DynamoDB Chat Memory 노드는 AWS DynamoDB를 기반으로 에이전트의 대화 기록을 저장하고 불러올 수 있도록 지원합니다. 높은 가용성과 확장성을 바탕으로, 엔터프라이즈 환경에서의 메모리 저장소로 적합합니다.

***

### 주요 기능

* AWS DynamoDB 테이블을 활용한 분산형 대화 메모리 저장
* Table 이름, Partition Key, Region 등을 지정하여 유연한 설정 가능
* Session ID 기반 사용자별 세션 기록 분리 지원
* 영속성 있는 저장소로 장기 세션 및 고가용성 서비스 구현에 최적

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 162552.png" alt=""><figcaption><p>WindyFlo DynamoDB Chat Memory</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-15 162604.png" alt=""><figcaption><p>WindyFlo DynamoDB Chat Memory Parameters</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                 | 설명                                     | 필수 여부 |
| ------------------ | -------------------------------------- | ----- |
| Connect Credential | AWS 인증 정보 (Credential에 등록 필요)          | 필수    |
| Table Name         | 대화 히스토리를 저장할 DynamoDB 테이블 이름           | 필수    |
| Partition Key      | 레코드 분할 기준이 되는 파티션 키                    | 필수    |
| Region             | AWS 리전 정보 (예: `us-east-1`)             | 필수    |
| Session ID         | 사용자 또는 세션 구분 식별자                       | 선택    |
| Memory Key         | LLM과 연결할 대화 히스토리 키 (예: `chat_history`) | 필수    |

***

### 출력값 (Outputs)

| 출력 항목              | 설명                           |
| ------------------ | ---------------------------- |
| DynamoDBChatMemory | DynamoDB에 연결된 에이전트 메모리 객체 반환 |

***

### 활용 예시

* 고객별 세션 히스토리를 영구 저장하는 AI 상담 시스템 구축
* 서버리스 환경에서 고가용성 챗봇의 메모리 저장소로 활용
* 멀티 유저 기반 SaaS형 AI 어시스턴트 서비스
* 시간 경과 후에도 대화 이력을 기반으로 응답하는 지속형 AI

***

### 사용 팁

* Table과 Partition Key는 사전에 AWS 콘솔 또는 CLI를 통해 생성해야 합니다.
* Region은 실제 테이블이 존재하는 AWS 리전으로 정확히 입력해야 합니다.
* Memory Key와 Session ID는 Agent 또는 LLM 노드와 일관되게 설정해야 정상 작동합니다.
* Additional Parameters를 활용하면 TTL(Time To Live) 설정이나 Attribute 설정이 가능함

***

### 주의사항

* Credential에 AWS Access Key와 Secret Key가 등록되지 않으면 작동하지 않습니다.
* 지정한 Table 또는 Partition Key가 존재하지 않을 경우 오류가 발생합니다.
* AWS 요금이 저장량과 호출 빈도에 따라 발생할 수 있으므로 사용 전 확인이 필요합니다.
* 보안 설정(IAM Role, 정책 등)을 정확히 구성하지 않으면 액세스 제한이 발생할 수 있습니다.
