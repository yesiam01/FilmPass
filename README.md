FilmPass - 영화 예매 시스템
이미지 표시
📚 목차

🎦 프로젝트 소개
📖 설계 문서
🛠️ 기술 스택
💡 기술적 의사 결정
⚙ 트러블 슈팅
🎯 성능 개선
🧑 팀원 소개

🎦 프로젝트 소개

영화 예매 시스템 - FilmPass

저희 Film Pass는 고객들에게 빠르고 안정적인 영화 티켓 예매 경험을 제공하고
고객들이 원하는 영화를 즐길 수 있도록 도와주는 영화 관람 티켓팅 전문 어플리케이션 입니다.
📖 설계 문서
🐬 API 명세서

API 문서 및 명세서 제공

🎀 ERD
V1
이미지 표시
V2
이미지 표시
🌍 와이어프레임
이미지 표시
🎦 아키텍처
이미지 표시
🛠️ 기술 스택
언어 및 프레임워크

Java 17
Spring Boot
Spring Data JPA

인증 인가

Spring Security
JWT

로그

slf4j

Database

MySQL
Redis

Infra & CI/CD

Docker
Amazon EC2
Amazon RDS
GitHub Actions
Nginx

모니터링 & 검색

Elasticsearch
Kibana

Test

Postman
JUnit5
K6
nGrinder
Swagger

Tools

IntelliJ IDEA

Collaboration

Notion
GitHub
Slack
ERD Cloud
Draw.io

💡 기술적 의사 결정
🔒 Redis Lock
기술 스택 비교 분석
기술 분류RedisZooKeeperetcd데이터 처리개발자 친화적모니터링 지원설정 정보 지원메모리In-Memory실시간으로 노출클러스터 구성특징SET NX EX TTL 기능Z-node WatchergRPC, Watch API운영 방식성능위주로 위험무결성 유지향정합성 확보
Redis 선택 이유

개발 친화성: 개발자가 사용하기 쉬운 구조
고성능: In-Memory 방식으로 빠른 처리
SET NX EX TTL 기능이 분산 락 구현에 충분

📌 GitHub Actions
CI/CD 도구 선택 근거
GitHub Actions 선택 시 장점:

관리 편의성: GitHub이 직접 관리해주어 별도의 설치/유지보수 부담 없음
설정의 간편함: 간단한 YAML 설정만으로 CI/CD 파이프라인 구현 가능
완벽한 GitHub 통합: PR, push, branch 등의 GitHub 이벤트와 즉시 연동 가능

Jenkins를 제외한 이유:

별도 서버 설치 및 유지보수 필요
플러그인/업데이트/보안 패치 직접 관리 부담
SSH 플러그인, 스크립트 직접 구성 등 설정 복잡성

🪙 Redis Cache
다른 캐시 기술들의 제약사항
기술핵심 단점프로젝트 영향도Memcached서버간 공유 캐시 불가능높음 - 분산 환경 구축 불가Hazelcast운영 난이도 복잡중간 - 높은 관리 리소스 요구ZooKeepereviction 정책 없음중간 - 메모리 관리 어려움Consul캐시 처리속도 느림중상 - 성능 병목 발생
Redis 선택을 통한 문제 해결

분산 캐시 지원: 다중 서버가 공유 캐시를 사용 가능
풍부한 운영 옵션: eviction 정책을 포함한 다양한 운영 옵션 존재
성능 최적화: 빠른 속도 및 TTL로 인한 키 관리 용이
Best Practice & 커뮤니티: 시행착오에 대한 많은 정보가 존재

🔍 Elasticsearch
Elasticsearch 선택 이유
특징:

분산 시스템: 데이터를 여러 노드에 분산하여 저장
전문 검색(Full-Text): Lucene의 강력한 검색 기능 활용
실시간 검색: 저장된 데이터에 대해 실시간 검색과 분석 수행
RESTful API: 다양한 프로그램 언어로 작성된 애플리케이션에서 쉽게 접근

장점:

빠른 검색 기능: Lucene 기반으로 대량의 데이터에 대한 빠른 검색
확장성: 수평적으로 확장 가능한 분산 시스템
다양한 데이터 처리: 복잡한 데이터 집계, 분석 기능 제공
가용성, 신뢰성: 데이터 자동 복제로 장애 상황에서도 서비스 지속

⚡ nGrinder
성능 테스트 도구 선택 근거
nGrinder 선택의 핵심 장점:

확장성: 분산/부하를 쉽게 늘릴 수 있음
코드 친화적 접근: API 호출 흐름을 코드처럼 표현 가능
국내 생태계 우위: 국내 문서와 사례가 많고, 도입/학습 장벽이 낮음

다른 도구들의 제외 사유:

JMeter: 분산 부하 환경 구축 번거로움, 관리 복잡성
Gatling: 국내 활용사례 부족, 학습비용 증가

⚙ 트러블 슈팅
🔥 nGrinder Agent CPU 병목현상
문제: nGrinder Agent의 CPU가 99%~100%로 사용되는 병목현상 발생
원인 분석:

무거운 실행 스크립트
불필요한 쿠키 처리
과도한 로깅
무제한 요청으로 인한 연속적인 처리 부하

해결 방법:

스크립트 최적화: 로그 코드 최소화, 불필요한 쿠키 처리 제거
요청 패턴 최적화: 요청 간 5초 지연 시간 추가

결과: CPU 사용률이 정상 범위로 안정화
🔍 다중 검색 기능 오류
문제: 다중 키워드로 영화 검색이 되지 않는 현상
원인: 쿼리메서드로 다중 키워드를 포함하도록 구현했으나 정적 쿼리 구조의 한계
해결 방법: 동적 쿼리(JPQL) 도입
java@Query(
    value = "SELECT * FROM movies " +
            "WHERE (:id IS NULL OR id = :id) " +
            "AND (:title IS NULL OR title = :title) " +
            "AND (:director IS NULL OR director = :director)" +
            "AND (:genre IS NULL OR genre = :genre)",
    nativeQuery = true
)
Page<Movie> searchMoviesNative(@Param("id") Long id, ...);
결과: 유연하고 안정적인 다중 검색 기능 완성
🔐 트랜잭션 커밋 전 락 해제로 인한 중복 예약
문제: 락을 적용했음에도 동시성 이슈가 발생
원인: 트랜잭션이 커밋되기 전에 락이 해제되어 동시성 제어 실패
해결 방법:

로직 분리: 검증 로직과 저장 로직 분리
트랜잭션 범위 조정: 락 해제를 트랜잭션 커밋 이후로 조정

결과: 안정적인 동시성 제어 구현
💾 Cache가 Redis에 등록되지 않는 현상
문제: 캐시를 적용했으나 Redis에 저장되지 않음
원인: Docker와 로컬에서 Redis가 동시 실행되어 확인하는 곳과 저장되는 곳이 달랐음
해결 방법: 로컬 Redis 프로세스 종료 후 Docker Redis로 통일
결과: 정상적으로 Docker Redis에 캐시 저장 확인
⚡ ES가 DB보다 3배 느려짐
문제: Elasticsearch가 MySQL보다 3배 느린 성능 (191ms vs 65ms)
원인 분석:

Cloud ES 네트워크 오버헤드
nori + edge_ngram 분석 비용
_source 전체 로드
불필요한 total count 계산

해결 방법:

_source 최소화: 필요한 필드만 선택
track_total_hits: false: 불필요한 전체 카운트 계산 제거

결과: 목표 응답 시간 74ms 달성 (74% 성능 향상)
🎯 성능 개선
🚀 Elasticsearch 성능 개선
개선 전후 성능 비교
데이터 규모MySQL (ms)Elasticsearch (ms)성능 향상률상태100 페이지32ms29ms9.4% ↑🟢 개선500 페이지38ms31ms18.4% ↑🟢 개선1000 페이지41ms32ms22.0% ↑🟢 개선
핵심 인사이트: 데이터량이 증가할수록 ES의 성능 우위가 더욱 뚜렷해짐
⚡ Redis Cache 성능 개선
영화 목록 API에 대한 Cache 적용 결과:
개선 효과:

사용자 경험 향상: 빠른 응답 시간으로 UX 개선
인프라 비용 절감: DB 부하 감소로 서버 리소스 최적화
확장성 증대: 높은 트래픽 상황에서도 안정적 서비스

기술적 이점:

고성능: 메모리 기반 빠른 데이터 접근
가용성: DB 장애 시에도 캐시된 데이터 제공
확장성: 수평 확장 가능한 아키텍처

🧑 팀원 소개
1조 One Take 팀원들이 함께 개발한 프로젝트입니다.
