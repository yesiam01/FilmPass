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

## 1. 프로젝트 소개
영화 예매 시스템 - **FilmPass**  
사용자가 원하는 영화를 편리하게 찾고 예매할 수 있는 온라인 영화 예매 사이트를 개발하여 실제 서비스까지 배포하였습니다
영화 정보 조회, 상영 스케줄 확인, 상영 극장 확인, 좌석 선택 과정을 웹에서 처리할 수 있도록 구현했습니다



---

## 2. 팀원 소개
<img width="1628" height="809" alt="Desktop Screenshot 2025 08 26 - 13 23 15 81" src="https://github.com/user-attachments/assets/b2b66d94-8231-4128-bd1d-e5fc66d8e4f3" />


---

## 3. 개발 기간
📅 **2025/07/17 ~ 2025/08/22**

---

## 4. 개발 환경
- **OS**: Windows 10 / macOS (팀원별 환경)  
- **IDE**: IntelliJ IDEA Ultimate  
- **Version Control**: Git, GitHub  
- **Build Tool**: Gradle 8.x  
- **Database(Local)**: H2 Database (개발용)  
- **Database(Prod)**: MySQL 8.x  
- **Cache**: Redis 7.x  
- **Infra**: Docker, AWS EC2  
- **협업 툴**: Notion, Slack, ERD Cloud  

---

## 5. 시스템 설계 자료

### 🗂️ 아키텍처
<img width="450" height="421" alt="1조 아키텍처 drawio" src="https://github.com/user-attachments/assets/8e09798b-8c2d-4f67-8642-5c0d4dad21e8" />


### 🗄️ ERD (Entity Relationship Diagram)
<img width="976" height="671" alt="20250806_223034 (1)" src="https://github.com/user-attachments/assets/1165b51d-5f05-45b6-a63f-9d801d563dce" />


### 🖼️ 와이어프레임
<img width="910" height="645" alt="20250718_144951 (1)" src="https://github.com/user-attachments/assets/bb47674f-4da1-43b5-869d-ba7db2280aa1" />


---

## 6. 주요 기능

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

### ⚡ 성능 최적화
- **Redis 캐싱**  
  → 자주 조회되는 영화 검색 결과를 캐싱하여 응답 속도 개선  
- **Elasticsearch기반 검색**  
  → 한국어 형태소 분석 지원
  



## 7. 사용한 기술 목록

### 언어 및 프레임워크
- Java 17
- Spring Boot
- Spring Data JPA

### 인증 · 인가
- Spring Security
- JWT
- slf4j

### Database
- MySQL
- Redis

### Infra & CI/CD
- Docker
- Amazon EC2
- Amazon RES
- GitHub Actions
- Nginx
- Elasticsearch
- Kibana

### Test
- Postman
- Junit5

## 8. API 명세서

(https://www.notion.so/teamsparta/1-One-Take-2482dc3ef51480f985aff3278597742f?source=copy_link#2532dc3ef51480ae9cb8f6b729725101)

## 9. 트러블슈팅 (Troubleshooting)

### 1. 영화 검색 기능 최적화
문제: 사용자가 영화 제목의 일부만 입력하면 "검색 결과가 없습니다"가 표시되어 사용자 경험에 문제 발생\

해결:
-Elasticsearch 도입: 한국어 형태소 분석이 필요한 부분 검색과 자동완성 기능 구현
-한국어 최적화: nori 토큰과 edgeNGram을 활용한 한국어 형태소 분석 구현
-인덱싱 최적화: 초기에는 영화 제목, 장르, 감독 정보를 모두 인덱싱했으나, 성능 테스트 결과 오히려 DB보다 느려지는 문제 발생. 핵심 검색 필드인 영화 제목과 내용만 선별적으로 인덱싱하여 검색 속도 향상

성능 개선 결과:
-100개 데이터: MySQL 35ms → ES 31ms (11% 개선)
-500개 데이터: MySQL 39ms → ES 32ms (18% 개선)
-1,000개 데이터: MySQL 41ms → ES 32ms (22% 개선)


모니터링: Kibana 기반 검색 패턴 분석 및 성능 지표 모니터링 체계 구축

### 2. NGrinder 부하 테스트 CPU 병목
문제: 트래픽 제너레이터 CPU 점유율 99% → 부하 테스트 결과 왜곡

해결방법:
-요청 간격 조정: 연속 요청 사이에 50ms 지연 추가

성과: CPU 사용률 60~80%로 안정화하여 정확한 부하 테스트 결과 확보

### 3. 중복 예약(트랜잭션 락) 발생
문제: 좌석 중복 예약 및 트랜잭션 락으로 인한 데드락 문제 발생

해결 방법:
-@Transactional 분리: 좌석 조회와 예약 처리를 별도 트랜잭션으로 분리
-비관적 락 적용: @Lock(LockModeType.PESSIMISTIC_WRITE) 사용하여 동시성 제어
-예외 처리 강화: 락 획득 실패 시 사용자에게 적절한 안내 메시지 제공

성과: 중복 예약 완전 방지 및 데드락 해결로 예매 시스템 안정성 확보

### 4. Redis 연결 실패
문제: 로컬 Redis(6379)와 애플리케이션 서버(8080) 간 연결 불가

해결 방법:
-Docker 네트워크 설정 수정: bridge 네트워크에서 host 네트워크로 변경
-포트 바인딩 확인: Redis 컨테이너 포트 매핑 재설정 (6379:6379)

성과: 정상 연결 및 데이터 저장/조회 가능, 캐싱을 통한 응답 속도 개선 달성
