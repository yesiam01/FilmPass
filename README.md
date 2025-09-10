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
