# ChatOpenAI

ChatOpenAI 노드는 OpenAI의 GPT 시리즈 모델(gpt-4, gpt-4o, gpt-3.5 등)을 호출하는 가장 범용적인 Chat Model 노드입니다. 고성능 생성 능력과 풍부한 제어 파라미터를 바탕으로 다양한 AI 파이프라인에 중심 역할을 수행합니다.

***

#### 주요 기능

* OpenAI API 기반 GPT 모델(gpt-4o, gpt-4, gpt-3.5 등) 호출 가능
* Temperature, Top-P, Stop Sequence 등 정교한 응답 제어 옵션 제공
* Streaming 모드, 이미지 업로드 등 최신 기능 지원
* 툴 호출, 프록시 연동, 응답 Reasoning 강도 설정 기능 포함
* BasePath 및 ProxyUrl을 통한 유연한 API 라우팅 구성 가능

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 112659.png" alt=""><figcaption><p>WindyFlo ChatOpenAI</p></figcaption></figure>

<div><figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 112712.png" alt=""><figcaption><p>WindyFlo ChatOpenAI Parameters</p></figcaption></figure> <figure><img src="../../../.gitbook/assets/스크린샷 2025-05-12 112720.png" alt=""><figcaption><p>WindyFlo ChatOpenAI Parameters</p></figcaption></figure></div>

#### 입력값 (Inputs)

| 항목                  | 설명                                          | 필수 여부 |
| ------------------- | ------------------------------------------- | ----- |
| Connect Credential  | OpenAI API Key (Credential에 등록된 값)          | 필수    |
| Model Name          | 사용할 모델명 (예: gpt-4o, gpt-4, gpt-3.5-turbo 등) | 필수    |
| Temperature         | 응답 창의성 조절 값 (0.0 \~ 1.0, 기본값: 0.9)          | 선택    |
| Allow Image Uploads | 이미지 업로드 기능 사용 여부                            | 선택    |

***

#### 파라미터 (Parameters)

| 항목                  | 설명                             |
| ------------------- | ------------------------------ |
| Streaming           | 실시간 응답 스트리밍 활성화 (기본값: true)    |
| Max Tokens          | 생성할 최대 토큰 수 제한                 |
| Top Probability     | Top-P 기반 확률 샘플링 값              |
| Frequency Penalty   | 반복 단어 빈도 억제 계수                 |
| Presence Penalty    | 새로운 토픽 등장 유도 계수                |
| Timeout             | API 응답 제한 시간(ms)               |
| Strict Tool Calling | Tool 호출을 강제할지 여부 (true/false)  |
| Stop Sequence       | 응답 종료 조건 지정 문자열                |
| BasePath            | OpenAI API 대체 경로 (예: 프록시 경유 시) |
| Proxy Url           | 프록시 서버 URL 설정 (옵션)             |
| BaseOptions         | 추가 옵션(JSON 형태 입력)              |
| Image Resolution    | 이미지 입력 해상도 (Low / High 등)      |
| Reasoning Effort    | 추론 품질 설정 (Low / Medium / High) |

***

#### 출력값 (Outputs)

| 출력 항목      | 설명                       |
| ---------- | ------------------------ |
| ChatOpenAI | GPT 모델로부터의 응답 또는 스트리밍 객체 |

***

#### 활용 예시

* 고객센터 챗봇, 지식 응답 시스템 등에서 **가장 신뢰도 높은 LLM 호출**
* GPT-4o 기반의 **음성·이미지·텍스트 통합 인터페이스 구축**
* **툴 호출 기능 활성화**로 외부 API 연결 및 액션 실행 자동화
* 이미지와 텍스트를 동시에 처리하는 멀티모달 응답 생성기 개발

***

#### 사용 팁

* \*\*GPT-4o(gpt-4o)\*\*는 빠르고 저렴하며 고성능, 대부분의 일반 응답에는 최우선 선택
* **Streaming** 활성화 시 UX 개선 및 대화형 응답 구현에 유리
* `Strict Tool Calling`을 true로 설정하면 툴만 호출하도록 제한 가능
* Reasoning Effort를 “High”로 설정하면 복잡한 추론에 더 나은 성능 발휘

***

#### 주의사항

* 모델명은 OpenAI에서 허용한 명칭만 입력 가능하며 버전 표기 주의
* 이미지 업로드 사용 시 API 플랜 제한 또는 요금 과금 유의
* GPT-4 계열은 응답이 느리거나 토큰 비용이 높을 수 있음
* Proxy Url 또는 BasePath 설정은 기업 방화벽, 내부망 API 경유 시에만 필요
