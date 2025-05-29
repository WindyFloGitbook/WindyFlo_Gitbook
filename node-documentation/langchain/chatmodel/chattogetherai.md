# ChatTogetherAI

ChatTogetherAI 노드는 **Together AI 플랫폼의 오픈소스 LLM**을 호출할 수 있는 Chat Model 노드입니다. 저렴한 비용으로 다양한 공개 모델을 실험하거나, 고성능 대안 모델을 빠르게 테스트할 수 있어 모델 전략 확장에 유용합니다.

***

#### 주요 기능

* Together AI가 제공하는 다양한 LLM(Mistral, LLaMA, Mixtral 등) 호출 가능
* OpenAI 호환 인터페이스 기반으로 쉽게 파이프라인에 통합 가능
* 실시간 응답을 위한 Streaming 기능 제공
* 기본 Temperature 설정으로 창의성 조절 가능
* 비용 효율적인 고성능 LLM 대안 구성 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 131201.png" alt=""><figcaption><p>WindyFlo ChatTogetherAI</p></figcaption></figure>

#### 입력값 (Inputs)

| 항목                 | 설명                                      | 필수 여부 |
| ------------------ | --------------------------------------- | ----- |
| Connect Credential | Together AI API Key (Credential에 등록된 값) | 필수    |
| Model Name         | 사용할 모델 이름 (예: mixtral-8x7b-32768)       | 필수    |
| Temperature        | 응답 다양성 조절 값 (0.0 \~ 1.0, 기본값: 0.9)      | 선택    |

***

#### 출력값 (Outputs)

| 출력 항목          | 설명                                  |
| -------------- | ----------------------------------- |
| ChatTogetherAI | Together AI의 지정 모델 응답 객체 또는 스트리밍 결과 |

***

#### 활용 예시

* **비용 효율이 중요한 스타트업**에서 GPT 대체용 LLM으로 대화형 챗봇 구축
* **성능 실험이 필요한 연구팀**이 다양한 오픈 모델을 빠르게 비교/테스트
* **파인튜닝 전 모델 후보군 선별**을 위한 신속한 벤치마킹
* **해외 API 정책 제한 회피용** 대체 LLM 구축

***

#### 사용 팁

* Together AI는 비용이 저렴하므로 대량 테스트용 챗봇 시나리오에 유리
* Model Name은 정확한 전체 이름을 입력해야 하며, 사전 확인 필수
* Streaming 기능은 UX 개선에 효과적이며 기본 활성화를 권장
* 높은 Temperature 값을 사용할 경우 생성 다양성은 증가하지만 안정성은 낮아질 수 있음

***

#### 주의사항

* 모델별 기능 편차가 큼 (예: 일부 모델은 함수 호출, 이미지 입력 미지원)
* Together AI는 API Rate Limit이 상대적으로 엄격하므로 주기적 호출 시 주의 필요
* 모델 명 오입력 시 에러 없이 빈 응답이 발생할 수 있음
* 가격 정책 및 지원 모델은 수시로 변경될 수 있으므로 공식 문서 확인 필수
