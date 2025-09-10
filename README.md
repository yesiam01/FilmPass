# 🎬 FilmPass

## 📑 목차
1. [프로젝트 소개](#1-프로젝트-소개)  
2. [팀원 소개](#2-팀원-소개)  
3. [개발 기간](#3-개발-기간)  
4. [개발 환경](#4-개발-환경)  
5. [시스템 설계 자료](#5-시스템-설계-자료)  
   - [아키텍처](#️-아키텍처)  
   - [ERD](#️-erd-entity-relationship-diagram)  
   - [와이어프레임](#️-와이어프레임)  
6. [주요 기능](#6-주요-기능)  
7. [사용한 기술 목록](#7-사용한-기술-목록)  
8. [API 명세서](#8-api-명세서)  
9. [트러블슈팅](#9-트러블슈팅-troubleshooting)  

---

## 프로젝트 소개
영화 예매 시스템 - **FilmPass**  
<img width="380" height="270" alt="filmpass_resized_380x270 (2)" src="https://github.com/user-attachments/assets/f0e1fd79-209e-4250-9d9a-c8446b4964e9" />

FilmPass는 고객들에게 빠르고 안정적인 영화 티켓 예매 경험을 제공하고,  
고객들이 원하는 영화를 즐길 수 있도록 도와주는 영화 관람 티켓팅 전문 어플리케이션입니다.

---

##  팀원 소개
<img width="1628" height="809" alt="Desktop Screenshot 2025 08 26 - 13 23 15 81" src="https://github.com/user-attachments/assets/b2b66d94-8231-4128-bd1d-e5fc66d8e4f3" />


---

##  개발 기간
📅 **2025/07/17 ~ 2025/08/22**

---


##  시스템 설계 자료

### 🗂️ 아키텍처

<details>
  <summary>아키텍처 다이어그램 보기</summary>

  <img width="450" height="421" alt="1조 아키텍처 drawio" src="https://github.com/user-attachments/assets/8e09798b-8c2d-4f67-8642-5c0d4dad21e8" />

</details>

### 🗄️ ERD (Entity Relationship Diagram)

<details>
  <summary>ERD 다이어그램 보기</summary>

  <img width="976" height="671" alt="20250806_223034 (1)" src="https://github.com/user-attachments/assets/1165b51d-5f05-45b6-a63f-9d801d563dce" />

</details>


### 🖼️ 와이어프레임

<details>
  <summary>와이어프레임 이미지 보기</summary>

  <img width="910" height="645" alt="20250718_144951 (1)" src="https://github.com/user-attachments/assets/bb47674f-4da1-43b5-869d-ba7db2280aa1" />

</details>

### 🛠️ 기술 스택

<details>
  <summary>기술 스택 이미지 보기</summary>

  <img width="749" height="570" alt="image" src="https://github.com/user-attachments/assets/3c14bee6-83ff-4308-a118-0c1f736f0c30" />

</details>

---


##  주요 기능

### 사용자, 관리자 이용 흐름
<img width="952" height="327" alt="20250910_191422" src="https://github.com/user-attachments/assets/55ffc947-4f42-4f8b-82c0-e85f68ce8e32" />

---

### 🎥 영화 관리
- **등록 / 수정 / 삭제 (관리자 전용)**  
  → 관리자는 새로운 영화를 등록하고, 기존 영화 정보를 업데이트하거나 삭제할 수 있음  
- **검색 / 목록 / 상세 조회 (사용자 전용)**  
  → 사용자는 영화 제목, 감독, 장르 등을 기준으로 검색 가능  
  → 개별 영화 상세 정보(상영 시간, 장르, 감독, 리뷰 등) 확인 가능  

---

### 🗓️ 상영 일정 & 좌석 관리
- **상영 스케줄 등록**  
  → 영화별 상영관, 상영 시간 지정 가능  
- **좌석 자동 생성**  
  → 스크린마다 A~J행, 1~7열 구조의 좌석 자동 생성  
- **잔여 좌석 관리**  
  → 실시간으로 예약 가능한 좌석 조회 가능  

---

### 🎟️ 예매 & 결제
- **좌석 선택 → 임시 홀드 → 결제 확정**  
  → 사용자가 좌석을 선택하면 일정 시간 동안 좌석이 홀드됨  
  → 결제 완료 시 좌석 예약이 최종 확정  
- **결제 실패 시 좌석 자동 반환**  

---

### ✍️ 리뷰 시스템
- **리뷰 작성 / 수정 / 삭제**  
  → 사용자는 본인이 예매한 영화에 대한 리뷰 작성 가능  
- **평점 집계**  
  → 영화별 평균 평점 계산 및 노출  

---

### 🔐 인증 & 권한 관리
- **JWT 기반 인증**  
  → 로그인 시 JWT 토큰 발급 및 유효성 검증  
- **권한(Role) 분리**  
  - `ROLE_USER`: 영화 조회, 예매, 리뷰 작성 가능  
  - `ROLE_ADMIN`: 영화 등록/수정/삭제, 스케줄 관리 가능  

---


##  기술적 의사 결정

### 🔐 Redis Lock

<details>
  <summary>선택 근거 보기</summary>
  

  - **개발팀 친숙도**: 학습 곡선이 낮음  
  - **인메모리 고성능 처리**  
  - **Set NX EX TTL 기능 제공**  
  - **분산 클러스터 요구사항 충족**  
  - **프로젝트 요구사항과 팀 역량에 최적의 매칭**

</details>


### 🪙 Redis Cache

<details>
  <summary>선택 근거 보기</summary>



  - **분산 캐시**: 다중 서버 환경 지원  
  - **메모리 관리**: LRU/LFU 기반 자동 Eviction 정책  
  - **고성능**: TTL 기반 자동 만료  

</details>


### 📊 Elasticsearch

<details>
  <summary>선택 근거 보기</summary>
  

  <img width="683" height="424" alt="20250825_000412" src="https://github.com/user-attachments/assets/f8b73d78-81fa-422f-ba08-e80c05936195" />


  #### 인덱싱 
  - **RDBMS 방식** : 순차적 검색으로 데이터 증가시 성능 저하
  - **ES 역색인 방식** : 키워드 기반 즉시 문서 매칭으로 고속 검색

  <img width="859" height="391" alt="20250827_152213" src="https://github.com/user-attachments/assets/76a769de-4a76-4be1-bd38-c2ab4b58f929" />


  #### 자동완성
  - **키워드 제안**  
  - **검색 후 최적화**: 검색 쿼리 수를 줄여 성능 향상  
  

  #### 주요 장점
  1. **성능**: 역색인 기반 빠른 전문 검색  
  2. **확장성**: 수평 확장 가능한 분산 구조  
  3. **실시간성**: 저장 즉시 검색 가능  
  4. **분석 기능**: 복잡한 데이터 집계 및 분석 지원  
  5. **가용성**: 자동 복제 제공  

</details>


### 💡 nGrinder

<details>
  <summary>선택 근거 보기</summary>
  

  #### 선택 근거
  1. **확장성**: 부하 크기 확장 용이  
  2. **개발 친화성**: Groovy/Jython 기반 코드 작성  
  3. **운영 효율성**: Web UI 기반 직관적 관리  
  4. **낮은 러닝 커브**: 한국어 문서와 예제 풍부  

  #### 기술적 장점
  - 안정적인 Controller-Agent 분산 처리 구조  
  - 복잡한 시나리오 프로그래밍 가능  
  - 국내 대규모 서비스에서 검증된 안정성  

  **결론**  
  → 확장성 검증 + 개발 효율성 + 최적의 선택  

</details>

---


##  트러블슈팅 (Troubleshooting)

### 💻 NGRINDER CPU 병목 현상

<details>
  <summary>자세히 보기</summary>

  #### 문제 정의
  - NGRINDER 성능 테스트 중  
  - 트래픽 제너레이터 CPU 사용률이 **99% ~ 100%** 도달  
  - 리소스 과부하 발생  

  #### 해결 방안
  - 요청 간격 조정 → 연속 요청 사이에 50ms 지연 추가  
  - 불필요한 로깅 코드 제거  

  #### 결과 및 검증
  | 상태 | CPU 사용률 | 안정성 | 테스트 정확도 |
  |------|------------|--------|----------------|
  | **최적화 전** | 99% ~ 100% | ❌ 불안정 | ❌ 왜곡 |
  | **최적화 후** | 정상 (60~80% 유지) | ✅ 안정적 | ✅ 정확 |

</details>


### 🔒 트랜잭션 락 문제  <summary>자세히 보기</summary>

<details>
  <summary>자세히 보기</summary>

  #### 문제 정의
  - 커밋 전에 락이 해제되는 문제 발생  
  - **동시성 제어 실패**: 커밋 전후의 간극에서 처리 충돌 발생  

  #### 해결 방안
  - `@Transactional` 분리 → 조회와 예약을 별도 트랜잭션으로 설정  
  - `@Lock(LockModeType.PESSIMISTIC_WRITE)` 적용 → 동시성 제어 강화  

  #### 결과 및 검증
  - 중복 예약 방지  
  - 데드락 해결  
  - 티켓 예매 시스템 안정성 확보  

</details>


### 🔗 Redis 연결 문제

<details>
  <summary>자세히 보기</summary>

  #### 문제 정의
  - Local Redis(6379) ↔ Application Server(8080) 연결 불가  
  - 원인: Docker 네트워크 설정 문제, 포트 매핑 오류  

  #### 해결 방안
  - Docker 네트워크 → Bridge → Host로 수정  
  - 불필요한 로깅 코드 제거  

  #### 결과 및 검증
  - 정상 연결 확인  
  - 데이터 저장 및 조회 정상 동작  

</details>


### 📊 Elasticsearch 성능 저하

<details>
  <summary>자세히 보기</summary>

  #### 문제 정의
  - DB보다 검색 속도 저하  
  - 불필요한 필드 인덱싱 → 인덱스 크기 과도 증가  
  - 전체 필드 검색 시 응답 속도 저하  

  #### 해결 방안
  - 핵심 필드(키워드, 영화 제목, 내용)만 인덱싱  
  - 불필요한 필드 제거로 검색 범위 축소  

  #### 결과 및 검증
  - 검색 성능 **11~22% 개선**  

</details>


