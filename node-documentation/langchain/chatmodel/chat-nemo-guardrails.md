# Chat Nemo Guardrails

ChatNemoGuardrails 노드는 NVIDIA NeMo 프레임워크 기반의 Guardrails 시스템과 연동된 LLM 응답 필터링/제어 기능을 제공합니다. 독립된 Configuration ID와 API Base URL을 기반으로, 외부 LLM의 응답을 **검열, 수정, 필터링**하는 데 적합합니다.

***

#### 주요 기능

* NVIDIA NeMo의 Guardrails 기능을 연동하여 응답 안전성 강화
* Configuration ID를 통해 사전 정의된 가이드라인(규칙 세트) 적용 가능
* Base URL 기반의 외부 NeMo Guardrails 서버 호출
* LLM 응답의 유해 표현 차단, 주제 제한, 금칙어 필터링 등 커스터마이징 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 111911.png" alt=""><figcaption><p>WindyFlo ChatNemoGuardrails</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목               | 설명                                                                                   | 필수 여부 |
| ---------------- | ------------------------------------------------------------------------------------ | ----- |
| Configuration ID | 사전 정의된 Guardrails 설정 식별자 (규칙 템플릿 ID 등)                                               | 필수    |
| Base URL         | NeMo Guardrails 서버의 API 엔드포인트 주소 (예: [http://localhost:8000](http://localhost:8000)) | 필수    |

***

#### 출력값 (Outputs)

| 출력 항목              | 설명                                |
| ------------------ | --------------------------------- |
| ChatNemoGuardrails | Guardrails를 통과한 최종 응답 또는 검열 결과 객체 |

***

#### 활용 예시

* **고객 상담 챗봇**에서 민감한 질문(금융, 의료 등)에 대한 제한된 응답만 허용
* LLM이 생성한 응답에서 **금칙어, 공격적 표현, 정치적 메시지** 등을 실시간 필터링
* 기업용 서비스에서 **컴플라이언스 요구사항**에 따른 사전 정의된 응답 제어 시스템 구축
* **어린이 대상 인터페이스** 등에서 주제 제한 및 응답 조정 기능 적용

***

#### 사용 팁

* **Configuration ID**는 NeMo Guardrails CLI 또는 API에서 사전 정의해 등록해야 사용 가능
* **Base URL**은 Docker 또는 클라우드 환경에서 구동 중인 NeMo 서버 주소와 일치해야 함
* LLM 응답 품질을 해치지 않으려면, 규칙은 최소한의 제약으로 점진적으로 설계할 것

***

#### 주의사항

* 실제 필터링은 NeMo Guardrails 엔진이 수행하며, WindyFlo에서는 연결 역할만 담당함
* Configuration이 과도하게 엄격하면 정상 응답도 차단될 수 있음
* Base URL 주소 오입력 또는 Guardrails 서버 미기동 시 연결 실패 발생
* GPU 자원 필요 여부는 NeMo 서버 환경에 따라 상이하므로 사전 확인 필요
