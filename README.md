영화 예매 시스템 -

**FilmPass**

사용자가 원하는 영화를 편리하게 찾고 예매할 수 있는 온라인 영화 예매 사이트를 개발하여 실제 서비스까지 배포하였습니다
영화 정보 조회, 상영 스케줄 확인, 상영 극장 확인, 좌석 선택 과정을 웹에서 처리할 수 있도록 구현했습니다

**6. 주요 기능**

**🎥 영화 관리**

- **등록 / 수정 / 삭제 (관리자 전용)**
- **검색 / 목록 / 상세 조회 (사용자 전용)**

---

**🗓️ 상영 일정 & 좌석 관리**

- **상영 스케줄 등록**
- **좌석 자동 생성**
- **잔여 좌석 관리**

---

**🎟️ 예매 & 결제**

- **좌석 선택 → 임시 홀드 → 결제 확정**→
- **결제 실패 시 좌석 자동 반환**

---

**✍️ 리뷰 시스템**

- **리뷰 작성 / 수정 / 삭제**
- **평점 집계**

---

**🔐 인증 & 권한 관리**

- **JWT 기반 인증**및 유효성 검증
- **권한(Role) 분리**

<aside>
💡

### **🎀ERD**

- V1
    
    ![erd.PNG](attachment:0b855d3d-c133-4647-986c-c59a566317e8:erd.png)
    
- V2
    
    ![20250806_223034.png](attachment:643eb1b4-d5dd-46d2-991d-f7f53a1a8585:20250806_223034.png)
    
</aside>

<aside>
💡

### **🌍와이어 프레임**

![20250718_144951.png](attachment:f040d537-3b42-460d-8843-7ab2292118fb:20250718_144951.png)

</aside>

<aside>
💡

### 🎦아키텍처

![1조 아키텍처.drawio.png](attachment:7f6be77f-aa72-4848-bb89-fb76b029ca2f:1조_아키텍처.drawio.png)

</aside>

<aside>
💡

### 플로우 차트

![20250906_201446.png](attachment:c8b26fb2-9330-4f38-a60b-ace8786d1acc:20250906_201446.png)

</aside>

## 🛠️ 기술 스택

언어 및 프레임 워크

[Java 17](https://www.notion.so/Java-17-2664bdb590fb81d4883ccf0bc9b99d97?pvs=21)

[Spring Boot](https://www.notion.so/Spring-Boot-2664bdb590fb8128a15bdba87d318354?pvs=21)

[Spring Data JPA](https://www.notion.so/Spring-Data-JPA-2664bdb590fb81d3808fe2ee33fe779b?pvs=21)

인증 인가

[Spring Security](https://www.notion.so/Spring-Security-2664bdb590fb8179a123ea2e542da105?pvs=21)

[JWT](https://www.notion.so/JWT-2664bdb590fb819fa91ef2e93653a20d?pvs=21)

JWT 로그

[slf4j ](https://www.notion.so/slf4j-2664bdb590fb816abd47ed4e25e81ce7?pvs=21)

**Database**

[MySQL](https://www.notion.so/MySQL-2664bdb590fb81a29f66f6b12b13c670?pvs=21)

[Redis](https://www.notion.so/Redis-2664bdb590fb81daa99fe20d3362450b?pvs=21)

**Infra & CI/CD**

[Docker](https://www.notion.so/Docker-2664bdb590fb8197bc7ae9cb73943992?pvs=21)

[Amazon EC2](https://www.notion.so/Amazon-EC2-2664bdb590fb818192c2d1a7c7151c40?pvs=21)

[Amazon RES ](https://www.notion.so/Amazon-RES-2664bdb590fb81bcabc6da5692c5cea8?pvs=21)

[GItHub Actions](https://www.notion.so/GItHub-Actions-2664bdb590fb81d6afe7d9bc83caf7e1?pvs=21)

[Nginx](https://www.notion.so/Nginx-2664bdb590fb812eb489fbf7e51387ba?pvs=21)

[Elasticsearch](https://www.notion.so/Elasticsearch-2664bdb590fb8148baa1dfc2b0a7c89a?pvs=21)

[Kibana](https://www.notion.so/Kibana-2664bdb590fb811e8f5cd3e4180501fd?pvs=21)

**Test**

[Postman](https://www.notion.so/Postman-2664bdb590fb81fbb59edcd8b9329fc5?pvs=21)

[Junit5](https://www.notion.so/Junit5-2664bdb590fb81d1a547fdd989119a6b?pvs=21)

[K6](https://www.notion.so/K6-2664bdb590fb8187800af2f2611dbfcf?pvs=21)

[nGrinder](https://www.notion.so/nGrinder-2664bdb590fb813b8fb8f4f92b8f88ef?pvs=21)

**Tools**

[Intellij IDEA](https://www.notion.so/Intellij-IDEA-2664bdb590fb81d2b214cc41c9f1cf75?pvs=21)

**Collaboration**

[Notion](https://www.notion.so/Notion-2664bdb590fb819f8625c6d8337abcdc?pvs=21)

[GitHub](https://www.notion.so/GitHub-2664bdb590fb81a5bea2f36bc7d39f06?pvs=21)

[Slack](https://www.notion.so/Slack-2664bdb590fb816e9adade941a3a0333?pvs=21)

[ERD cloud](https://www.notion.so/ERD-cloud-2664bdb590fb813a9502db344eb0f482?pvs=21)

[RESTful API](https://www.notion.so/RESTful-API-2664bdb590fb81fa8991e3176a705d31?pvs=21)

[draw.io](https://www.notion.so/draw-io-2664bdb590fb8198b499d061b2419e94?pvs=21)

## 💡 기술적 의사 결정

<aside>
🔒

### Redis Lock

# Redis Lock 선택 근거

---

- 개발팀 친숙도 및 낮은 학습 곡선
- In-Memory 방식의 고성능 처리
- SET NX EX TTL 기능으로 분산 클러스터 요구사항 충족
- 프로젝트 요구사항과 팀 역량에 최적 매칭
</aside>

<aside>
🪙

### Redis cache

# Redis cache 선택 근거

---

- **분산 캐시**: 다중 서버 간 공유 캐시 지원
- **메모리 관리**: LRU/LFU 등 eviction 정책 자동화
- **고성능**: TTL 기반 자동 만료로 빠른 처리

---

</aside>

<aside>
🔍

### Elasticsearch

# ElasticSearch 선택 근거

---

- **RDBMS 방식**: 순차적 검색으로 데이터 증가시 성능 저하
- **ES 역색인 방식**: 키워드 기반 즉시 문서 매칭으로 고속 검색
    
    ![20250825_000412.png](attachment:f6e9c909-79e6-4627-8f08-68bc06855661:20250825_000412.png)
    

### Auto Completion

- **검색 전**: 사용자 입력에 따른 실시간 키워드 제안
- **검색 후**: 검색 쿼리 수 감소로 성능 최적화
    
    ![20250827_152213.png](attachment:9a6caee1-3b8e-4897-8beb-0242c8db7d6e:20250827_152213.png)
    

## 주요 장점

1. **성능**: 역색인을 통한 빠른 전문 검색
2. **확장성**: 수평 확장 가능한 분산 구조
3. **실시간**: 데이터 저장 즉시 검색 가능
4. **분석**: 복잡한 데이터 집계 및 분석 기능
5. **가용성**: 자동 복제를 통한 무중단 서비스

---

</aside>

<aside>
💡

### nGrinder

## nGrinder 선택 근거

---

### 핵심 장점

1. **확장성**: Agent 추가로 손쉬운 부하 규모 확장
2. **개발 친화적**: Groovy/Jython 기반 코드 작성
3. **운영 효율성**: 웹 UI 기반 직관적 관리
4. **낮은 러닝커브**: 풍부한 한국어 문서 및 사례

### 기술적 우위

- Controller-Agent 구조의 안정적 분산 처리
- 복잡한 시나리오의 프로그래밍적 구현 가능
- 국내 대형 서비스 검증된 안정성

**결론**: 확장성 검증 + 개발 효율성 + 운영 안정성을 모두 충족하는 최적 선택

---

</aside>

## ⚙ 트러블 슈팅

<aside>

### nGrinder 사용 중 agent의 CPU 병목현상

## 문제 정의

### **발생한 문제**

nGrinder를 사용하여 성능 테스트를 진행하던 중, **트래픽 발생기인 agent의 CPU가 99% ~ 100%로 사용**되는  병목현상 발생

---

## 원인 분석

### 과도한 동시 요청 처리로 인한 CPU 리소스 과부하

---

## 해결 방법

### **스크립트 최적화 전략**

### **1. 요청 간격 조정: 연속 요청 사이에 50ms 지연 추가**

### **2. 불필요한 로깅 코드 제거**

---

## 결과 & 검증

### **CPU 사용량 비교**

| 상태 | CPU 사용률 | 안정성 | 테스트 정확도 |
| --- | --- | --- | --- |
| **최적화 전** | 99% ~ 100% | ❌ 불안정 | ❌ 결과 왜곡 |
| **최적화 후** | 정상 범위 | ✅ 안정적 | ✅ 정확한 측정 |

### 개선 전/후 CPU 사용량

- CPU 사용률 60~80%로 안정화

</aside>

<aside>

### 중복 예약(트랜잭션 락) 발생

## 문제 정의

좌석 중복 예약 및 트랜잭션 락으로 인한 데드락 문제 발생

---

## **원인 분석**

- **락 해제 타이밍** : 트랜잭션이 커밋되기 전에 락이 해제되는 문제
- **동시성 제어 실패**: 락이 해제된 뒤 트랜잭션 커밋 사이 간극에서 동시성 이슈 발생

---

## 해결 방법

### 1. **-@Transactional 분리: 좌석 조회와 예약 처리를 별도 트랜잭션으로 분리**

### 2. -비관적 락 적용: @Lock(LockModeType.PESSIMISTIC_WRITE) 사용하여 동시성 제어

 

---

### 결과 & 검증

- 중복 예약 완전 방지 및 데드락 해결로 예매 시스템 안정성 확보
</aside>

<aside>

### Redis 연결 실패

## 문제 정의

### **발생한 문제**

 로컬 Redis(6379)와 애플리케이션 서버(8080) 간 연결 불가

---

## 원인 분석

- Docker 컨테이너 간 네트워크 설정 오류
- Redis 컨테이너의 포트 매핑 설정 문제

---

## 해결 방법

### **1. Docker 네트워크 설정 수정**: bridge 네트워크에서 host 네트워크로 변경

### **2. 불필요한 로깅 코드 제거**

---

## 결과 & 검증

- 정상 연결 및 데이터 저장/조회 가능

### 

</aside>

<aside>

### ES 가 DB 보다 느려진 현상 발생

## 문제 정의

### **발생한 문제**

 모든 키워드(영화 제목, 장르, 감독 등)를 인덱싱한 결과 오히려 DB보다 느려지는 성능 문제 발생

---

## 원인 분석

- 과도한 인덱싱으로 인한 검색 성능 저하
- 불필요한 필드까지 포함하여 인덱스 크기 증가
- 검색 시 모든 필드를 대상으로 하여 응답 속도 감소

---

## 해결 방법

### **1.인덱싱 최적화**: 모든 키워드에서 핵심 검색 필드인 영화 제목과 내용만 선별적으로 인덱싱

### **2. 검색 범위 축소**: 불필요한 필드 제거로 검색 효율성 향상

---

## 결과 & 검증

- 데이터량 증가에 따른 검색 성능 11~22% 개선 달성

### 

</aside>

## 🎯 성능 개선

<aside>

### ES 성능 개선

# Elasticsearch 성능 개선

---

## 개선 전후 성능 비교

![20250825_164332.png](attachment:0ae1de15-6d2d-4882-a1ab-945050518f07:20250825_164332.png)

### 📈 성능 비교 결과

| 데이터 규모 | MySQL (ms) | Elasticsearch (ms) | 성능 향상률 | 상태 |
| --- | --- | --- | --- | --- |
| **100 페이지** | `32ms` | `29ms` | **9.4% ↑** | 🟢 개선 |
| **500 페이지** | `38ms` | `31ms` | **18.4% ↑** | 🟢 개선 |
| **1000 페이지** | `41ms` | `32ms` | **22.0% ↑** | 🟢 개선 |

---

### 성능 패턴 분석

- **100 페이지**: 9.4% 향상 (소폭 개선)
- **500 페이지**: 18.4% 향상 (중간 개선)
- **1000 페이지**: 22.0% 향상 (큰 폭 개선)

### 성능 트렌드

- **MySQL**: 데이터량 증가 시 선형적 성능 저하 (32ms → 41ms)
- **Elasticsearch**: 데이터량 증가에도 안정적 성능 유지 (29ms → 32ms)

---

</aside>

<aside>

### Redis Cache 성능 개선

# 🚀 Redis Cache 성능 개선

---

## 📊 테스트 결과

### 캐시 적용 전

- **응답 시간**: 데이터베이스 직접 조회
- **성능 특성**: 매 요청마다 DB 쿼리 실행
    
    ![캐시 없음.PNG](attachment:d1649096-e3c7-4fa1-b8b2-4ac96e52f95a:캐시_없음.png)
    

### 캐시 적용 후

- **응답 시간**: Redis 메모리 캐시 활용
- **성능 특성**: 첫 요청 후 캐시된 데이터 재사용
    
    ![캐시 적용.PNG](attachment:86ad1f4e-c1b4-4727-9491-ed0dddd001b8:캐시_적용.png)
    

</aside>
