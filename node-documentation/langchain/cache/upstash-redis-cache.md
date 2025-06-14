# Upstash Redis Cache

**Upstash Redis Cache 노드**는 서버리스 Redis 플랫폼인 [Upstash](https://upstash.com/)와 연결하여, 세션 간 데이터를 저장하고 재사용할 수 있도록 지원하는 **외부 캐시 연동 노드**입니다. 복잡한 파이프라인에서도 빠른 데이터 접근성과 상태 유지가 필요한 경우에 사용됩니다.

***

### 주요 기능

* **Upstash Redis와 연동된 서버리스 캐시 구성**
* **세션을 넘어 상태를 유지하는 외부 저장소 제공**
* **풍부한 API와 사용량 기반 과금으로 유연한 확장 가능**

<figure><img src="../../../.gitbook/assets/스크린샷 2025-05-09 161630.png" alt=""><figcaption><p>WindyFlo Upstash Redis Cache</p></figcaption></figure>

### 입력값 (Inputs)

| 항목                     | 설명                                                             | 필수 여부 |
| ---------------------- | -------------------------------------------------------------- | ----- |
| **Connect Credential** | Upstash Redis에 연결하기 위한 인증 정보. WindyFlo Credential Manager에서 등록 | 필수    |

***

### 출력값 (Outputs)

| 출력 항목                 | 설명                                                                      |
| --------------------- | ----------------------------------------------------------------------- |
| **UpstashRedisCache** | Upstash Redis와 연결된 캐시 객체. 이후 키-값 저장, 조회, 삭제 등의 작업을 지원하는 캐시 구성 요소로 활용 가능 |

***

### 활용 예시

1. **API 응답 결과 임시 저장 및 캐싱**\
   → 외부 API → Upstash Redis Cache → 반복 질의 시 빠른 응답 처리
2. **상태 기반 세션 관리**\
   → 유저별 인터랙션 진행 상태 저장 → 다음 단계로 이어질 때 재활용
3. **다중 파이프라인 간 공유 상태 저장소 구성**\
   → 하나의 캐시 저장소를 여러 파이프라인에서 함께 활용

***

### 장점

* **서버리스 환경에 최적화**: 인프라 운영 없이 고성능 Redis 사용
* **자동 확장, 지연 없는 응답**: LLM 기반 애플리케이션 캐시에 적합
* **글로벌 배포 및 낮은 레이턴시** 지원

***

### 주의사항

* **Upstash 계정이 필요**하며, Redis 인스턴스를 생성 후 인증 정보를 WindyFlo Credential Manager에 등록해야 합니다.
* TTL, Key 구성, 네임스페이스 등은 후속 노드 또는 Custom Tool에서 관리해야 하며, 본 노드는 기본 연결 기능만 담당합니다.
* 보안 정보(예: 인증 토큰)는 캐시에 저장할 경우 반드시 만료 시간을 설정하거나 암호화 적용 권장

***

Upstash Redis Cache는 WindyFlo에서 **서버리스 기반의 고성능 외부 상태 저장소를 구축할 수 있는 확장성 높은 캐시 노드**입니다. 서버 인프라 부담 없이 안정적인 상태 관리를 필요로 하는 경우에 이상적입니다.
