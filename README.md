영화 예매 시스템 - FilmPass
사용자가 원하는 영화를 편리하게 찾고 예매할 수 있는 온라인 영화 예매 사이트를 개발하여 실제 서비스까지 배포하였습니다
영화 정보 조회, 상영 스케줄 확인, 상영 극장 확인, 좌석 선택 과정을 웹에서 처리할 수 있도록 구현했습니다
6. 주요 기능
<details>
<summary>🎥 영화 관리</summary>

등록 / 수정 / 삭제 (관리자 전용)
검색 / 목록 / 상세 조회 (사용자 전용)

</details>
<details>
<summary>🗓️ 상영 일정 & 좌석 관리</summary>

상영 스케줄 등록
좌석 자동 생성
잔여 좌석 관리

</details>
<details>
<summary>🎟️ 예매 & 결제</summary>

좌석 선택 → 임시 홀드 → 결제 확정
결제 실패 시 좌석 자동 반환

</details>
<details>
<summary>✍️ 리뷰 시스템</summary>

리뷰 작성 / 수정 / 삭제
평점 집계

</details>
<details>
<summary>🔐 인증 & 권한 관리</summary>

JWT 기반 인증및 유효성 검증
권한(Role) 분리

</details>
🎀 프로젝트 설계
<details>
<summary>📊 ERD - V1</summary>
이미지 표시
</details>
<details>
<summary>📊 ERD - V2</summary>
이미지 표시
</details>
<details>
<summary>🌍 와이어 프레임</summary>
이미지 표시
</details>
<details>
<summary>🎦 아키텍처</summary>
이미지 표시
</details>
<details>
<summary>📋 플로우 차트</summary>
이미지 표시
</details>
🛠️ 기술 스택
<details>
<summary>🔧 언어 및 프레임워크</summary>

Java 17
Spring Boot
Spring Data JPA

</details>
<details>
<summary>🔐 인증 인가</summary>

Spring Security
JWT

</details>
<details>
<summary>📝 JWT 로그</summary>

slf4j

</details>
<details>
<summary>🗄️ Database</summary>

MySQL
Redis

</details>
<details>
<summary>☁️ Infra & CI/CD</summary>

Docker
Amazon EC2
Amazon RDS
GitHub Actions
Nginx
Elasticsearch
Kibana

</details>
<details>
<summary>🧪 Test</summary>

Postman
JUnit5
K6
nGrinder

</details>
<details>
<summary>🛠️ Tools</summary>

IntelliJ IDEA

</details>
<details>
<summary>👥 Collaboration</summary>

Notion
GitHub
Slack
ERD cloud
RESTful API
draw.io

</details>
💡 기술적 의사 결정
<details>
<summary>🔒 Redis Lock</summary>
Redis Lock 선택 근거

개발팀 친숙도 및 낮은 학습 곡선
In-Memory 방식의 고성능 처리
SET NX EX TTL 기능으로 분산 클러스터 요구사항 충족
프로젝트 요구사항과 팀 역량에 최적 매칭

</details>
<details>
<summary>🪙 Redis Cache</summary>
Redis Cache 선택 근거

분산 캐시: 다중 서버 간 공유 캐시 지원
메모리 관리: LRU/LFU 등 eviction 정책 자동화
고성능: TTL 기반 자동 만료로 빠른 처리

</details>
<details>
<summary>🔍 Elasticsearch</summary>
Elasticsearch 선택 근거

RDBMS 방식: 순차적 검색으로 데이터 증가시 성능 저하
ES 역색인 방식: 키워드 기반 즉시 문서 매칭으로 고속 검색

이미지 표시
Auto Completion

검색 전: 사용자 입력에 따른 실시간 키워드 제안
검색 후: 검색 쿼리 수 감소로 성능 최적화

이미지 표시
주요 장점

성능: 역색인을 통한 빠른 전문 검색
확장성: 수평 확장 가능한 분산 구조
실시간: 데이터 저장 즉시 검색 가능
분석: 복잡한 데이터 집계 및 분석 기능
가용성: 자동 복제를 통한 무중단 서비스

</details>
<details>
<summary>💡 nGrinder</summary>
nGrinder 선택 근거
핵심 장점

확장성: Agent 추가로 손쉬운 부하 규모 확장
개발 친화적: Groovy/Jython 기반 코드 작성
운영 효율성: 웹 UI 기반 직관적 관리
낮은 러닝커브: 풍부한 한국어 문서 및 사례

기술적 우위

Controller-Agent 구조의 안정적 분산 처리
복잡한 시나리오의 프로그래밍적 구현 가능
국내 대형 서비스 검증된 안정성

결론: 확장성 검증 + 개발 효율성 + 운영 안정성을 모두 충족하는 최적 선택
</details>
⚙ 트러블 슈팅
<details>
<summary>nGrinder 사용 중 agent의 CPU 병목현상</summary>
문제 정의
nGrinder를 사용하여 성능 테스트를 진행하던 중, 트래픽 발생기인 agent의 CPU가 99% ~ 100%로 사용되는 병목현상 발생
원인 분석
과도한 동시 요청 처리로 인한 CPU 리소스 과부하
해결 방법
스크립트 최적화 전략

요청 간격 조정: 연속 요청 사이에 50ms 지연 추가
불필요한 로깅 코드 제거

결과 & 검증
CPU 사용량 비교
상태CPU 사용률안정성테스트 정확도최적화 전99% ~ 100%❌ 불안정❌ 결과 왜곡최적화 후정상 범위✅ 안정적✅ 정확한 측정

CPU 사용률 60~80%로 안정화

</details>
<details>
<summary>중복 예약(트랜잭션 락) 발생</summary>
문제 정의
좌석 중복 예약 및 트랜잭션 락으로 인한 데드락 문제 발생
원인 분석

락 해제 타이밍: 트랜잭션이 커밋되기 전에 락이 해제되는 문제
동시성 제어 실패: 락이 해제된 뒤 트랜잭션 커밋 사이 간극에서 동시성 이슈 발생

해결 방법

@Transactional 분리: 좌석 조회와 예약 처리를 별도 트랜잭션으로 분리
비관적 락 적용: @Lock(LockModeType.PESSIMISTIC_WRITE) 사용하여 동시성 제어

결과 & 검증

중복 예약 완전 방지 및 데드락 해결로 예매 시스템 안정성 확보

</details>
<details>
<summary>Redis 연결 실패</summary>
문제 정의
로컬 Redis(6379)와 애플리케이션 서버(8080) 간 연결 불가
원인 분석

Docker 컨테이너 간 네트워크 설정 오류
Redis 컨테이너의 포트 매핑 설정 문제

해결 방법

Docker 네트워크 설정 수정: bridge 네트워크에서 host 네트워크로 변경
포트 매핑 재설정

결과 & 검증

정상 연결 및 데이터 저장/조회 가능

</details>
<details>
<summary>ES가 DB보다 느려진 현상 발생</summary>
문제 정의
모든 키워드(영화 제목, 장르, 감독 등)를 인덱싱한 결과 오히려 DB보다 느려지는 성능 문제 발생
원인 분석

과도한 인덱싱으로 인한 검색 성능 저하
불필요한 필드까지 포함하여 인덱스 크기 증가
검색 시 모든 필드를 대상으로 하여 응답 속도 감소

해결 방법

인덱싱 최적화: 모든 키워드에서 핵심 검색 필드인 영화 제목과 내용만 선별적으로 인덱싱
검색 범위 축소: 불필요한 필드 제거로 검색 효율성 향상

결과 & 검증

데이터량 증가에 따른 검색 성능 11~22% 개선 달성

</details>
🎯 성능 개선
<details>
<summary>ES 성능 개선</summary>
Elasticsearch 성능 개선
이미지 표시
📈 성능 비교 결과
데이터 규모MySQL (ms)Elasticsearch (ms)성능 향상률상태100 페이지32ms29ms9.4% ↑🟢 개선500 페이지38ms31ms18.4% ↑🟢 개선1000 페이지41ms32ms22.0% ↑🟢 개선
성능 패턴 분석

100 페이지: 9.4% 향상 (소폭 개선)
500 페이지: 18.4% 향상 (중간 개선)
1000 페이지: 22.0% 향상 (큰 폭 개선)

성능 트렌드

MySQL: 데이터량 증가 시 선형적 성능 저하 (32ms → 41ms)
Elasticsearch: 데이터량 증가에도 안정적 성능 유지 (29ms → 32ms)

</details>
<details>
<summary>🚀 Redis Cache 성능 개선</summary>
📊 테스트 결과
캐시 적용 전

응답 시간: 데이터베이스 직접 조회
성능 특성: 매 요청마다 DB 쿼리 실행

이미지 표시
캐시 적용 후

응답 시간: Redis 메모리 캐시 활용
성능 특성: 첫 요청 후 캐시된 데이터 재사용

이미지 표시
</details>
