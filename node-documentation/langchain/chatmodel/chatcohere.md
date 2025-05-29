# ChatCohere

ChatCohere 노드는 Cohere에서 제공하는 Command R+ 등 대화형 언어 모델을 호출하는 Chat Model 노드입니다. 빠른 응답과 합리적인 성능의 LLM이 필요한 상황에서 적합하며, 특히 영어 텍스트 기반의 추론 및 응답 품질이 강점입니다.

***

#### 주요 기능

* Cohere의 최신 LLM(Command R+)을 호출해 대화형 응답 생성
* Temperature 값 조절로 창의성 및 응답 다양성 제어
* Streaming 모드 지원으로 빠른 응답 체감 가능
* 비용 효율적이고 안정적인 LLM 호출 수단으로 사용 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 103139.png" alt=""><figcaption><p>WindyFlo ChatCohere</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                 | 설명                                       | 필수 여부 |
| ------------------ | ---------------------------------------- | ----- |
| Connect Credential | Cohere API 키를 Credential에 등록한 항목         | 필수    |
| Model Name         | 사용할 Cohere 모델명 (예: command-r-plus 등)     | 필수    |
| Temperature        | 응답 생성의 창의성 조절 값 (0.0 \~ 1.0, 기본값 예: 0.7) | 선택    |
| Streaming          | 응답을 스트리밍 방식으로 수신할지 여부 (기본값: true)        | 선택    |

***

#### 출력값 (Outputs)

| 출력 항목      | 설명                           |
| ---------- | ---------------------------- |
| ChatCohere | Cohere 모델의 응답 텍스트 또는 스트리밍 객체 |

***

#### 활용 예시

* 빠른 성능이 필요한 고객 응대형 챗봇 서비스에서 Cohere 모델을 활용해 대화 품질 확보
* 비용 효율성이 중요한 스타트업 SaaS 서비스에 내장형 LLM 기능 탑재 시 활용
* 영어 중심의 이메일, 문서 요약 및 응답 자동화 기능에 적용
* 대량 사용자 대상 인터랙션 기능이 필요한 교육·커뮤니티 플랫폼에서 안정적 운영

***

#### 사용 팁

* Temperature를 낮게 설정(예: 0.3\~0.5)하면 더 일관되고 안정적인 응답 생성 가능
* Command R+는 최신 LLM으로서 추론 성능이 우수하므로 고정된 템플릿보다는 유연한 Prompt 설계 추천
* API 응답 속도가 매우 빠르므로 Streaming 모드와 병렬 호출을 함께 활용 시 체감 응답 개선

***

#### 주의사항

* API 키가 Credential에 사전 등록되어 있어야 하며, 해당 키에 적절한 모델 호출 권한이 부여되어 있어야 합니다
* Model Name은 정확한 명칭(command-r, command-r-plus 등)을 사용해야 하며, 오타 또는 미지원 모델명 사용 시 오류 발생
* 토큰 단가 및 호출 제한은 Cohere 요금 정책에 따라 달라지므로 사전 확인 필요
