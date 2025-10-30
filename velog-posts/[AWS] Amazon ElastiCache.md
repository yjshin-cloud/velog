<h1 id="⚡-amazon-elasticache-정리">⚡ Amazon ElastiCache 정리</h1>
<hr />
<h2 id="1️⃣-amazon-elasticache란">1️⃣ Amazon ElastiCache란?</h2>
<p>Amazon ElastiCache는
AWS에서 제공하는 인메모리(In-memory) 캐싱 서비스로,
자주 조회되는 데이터를 메모리에 저장해 데이터베이스 부하를 줄이고 애플리케이션 속도를 높여주는 서비스입니다.</p>
<p>👉 쉽게 말해,
“매번 DB에 접근하지 않고, 빠른 캐시(임시 저장소)에서 바로 데이터를 꺼내 쓰는 서비스” 입니다.</p>
<hr />
<h2 id="2️⃣-주요-특징">2️⃣ 주요 특징</h2>
<table>
<thead>
<tr>
<th>특징</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>⚡ <strong>초저지연 응답 속도</strong></td>
<td>밀리초보다 빠른 마이크로초 단위 응답</td>
</tr>
<tr>
<td>🧠 <strong>인메모리 저장 구조</strong></td>
<td>데이터가 디스크가 아닌 메모리에 저장되어 고속 처리 가능</td>
</tr>
<tr>
<td>🔄 <strong>자동 장애 복구</strong></td>
<td>Primary 장애 시 Standby로 자동 전환 (Multi-AZ)</td>
</tr>
<tr>
<td>📈 <strong>확장성 (Scaling)</strong></td>
<td>읽기 전용 노드(Read Replica) 추가로 확장 가능</td>
</tr>
<tr>
<td>🔒 <strong>보안 통합</strong></td>
<td>VPC, IAM, Security Group, KMS 암호화 통합 지원</td>
</tr>
<tr>
<td>☁️ <strong>완전관리형</strong></td>
<td>서버 프로비저닝, 패치, 장애 복구를 AWS가 자동 관리</td>
</tr>
</tbody></table>
<hr />
<h2 id="3️⃣-지원-엔진">3️⃣ 지원 엔진</h2>
<table>
<thead>
<tr>
<th>엔진</th>
<th>특징</th>
<th>주요 사용 사례</th>
</tr>
</thead>
<tbody><tr>
<td><strong>Redis</strong></td>
<td>키-값 기반 데이터 저장, 복제/영속화/클러스터 지원</td>
<td>세션 캐시, 실시간 랭킹, Pub/Sub 시스템</td>
</tr>
<tr>
<td><strong>Memcached</strong></td>
<td>단순 캐싱 전용, 분산 구조</td>
<td>단순 쿼리 캐시, 페이지 캐싱</td>
</tr>
</tbody></table>
<hr />
<h2 id="4️⃣-아키텍처-시각화">4️⃣ 아키텍처 시각화</h2>
<pre><code class="language-mermaid">flowchart TD
    A[&quot;👩‍💻 애플리케이션 (EC2 / Lambda / ECS)&quot;] --&gt; B{&quot;ElastiCache Cluster&quot;}
    B --&gt; C[&quot;Redis / Memcached Node (Primary)&quot;]
    C --&gt; D[&quot;Read Replica Node (옵션)&quot;]
    A --&gt;|Cache Miss| E[&quot;Amazon RDS / DynamoDB&quot;]
    E --&gt;|Query Result| C
    C --&gt;|Cache Hit| A</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/92232d26-d27b-4a75-aed0-829e8dc839f7/image.png" /></p>
<p>🧠 설명:</p>
<p>“Cache Hit” → 이미 캐시에 데이터가 있어 DB 접근 없이 즉시 응답</p>
<p>“Cache Miss” → 캐시에 없을 때만 DB에서 읽어와 캐시에 저장</p>
<hr />
<h2 id="5️⃣-주요-용어-정리">5️⃣ 주요 용어 정리</h2>
<table>
<thead>
<tr>
<th>용어</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td><strong>Cache Hit</strong></td>
<td>요청한 데이터가 캐시에 존재함 → 빠른 응답</td>
</tr>
<tr>
<td><strong>Cache Miss</strong></td>
<td>캐시에 없음 → DB에서 조회 후 캐시에 저장</td>
</tr>
<tr>
<td><strong>TTL (Time To Live)</strong></td>
<td>캐시 데이터의 유효 기간 (만료 시 자동 삭제)</td>
</tr>
<tr>
<td><strong>Replication</strong></td>
<td>Primary 데이터 복제 → 고가용성 유지</td>
</tr>
<tr>
<td><strong>Cluster Mode</strong></td>
<td>데이터를 여러 샤드(Shard)에 분산 저장하여 대규모 확장 지원</td>
</tr>
</tbody></table>
<hr />
<h2 id="6️⃣-elasticache-주요-활용-사례">6️⃣ ElastiCache 주요 활용 사례</h2>
<table>
<thead>
<tr>
<th>시나리오</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>⚡ <strong>웹 애플리케이션 가속화</strong></td>
<td>DB 쿼리 결과를 캐시에 저장 → 응답속도 향상</td>
</tr>
<tr>
<td>🧠 <strong>세션 관리(Session Store)</strong></td>
<td>사용자 로그인 세션 정보를 Redis에 저장</td>
</tr>
<tr>
<td>🕹️ <strong>실시간 순위 / 게임 리더보드</strong></td>
<td>Redis 정렬된 집합(Sorted Set)으로 순위 관리</td>
</tr>
<tr>
<td>💬 <strong>실시간 채팅 / Pub-Sub 시스템</strong></td>
<td>Redis의 Pub/Sub 기능을 이용해 메시지 브로커 역할 수행</td>
</tr>
<tr>
<td>📊 <strong>데이터 분석 임시 저장소</strong></td>
<td>ETL 처리 중간 결과를 메모리에 저장해 빠른 재사용 가능</td>
</tr>
</tbody></table>
<hr />
<h2 id="7️⃣-redis-vs-memcached-비교">7️⃣ Redis vs Memcached 비교</h2>
<table>
<thead>
<tr>
<th>항목</th>
<th><strong>Redis</strong></th>
<th><strong>Memcached</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>데이터 구조</strong></td>
<td>String, List, Set, Hash, Sorted Set 등 다양</td>
<td>Key-Value 단순 구조</td>
</tr>
<tr>
<td><strong>Persistence (영속성)</strong></td>
<td>지원 (RDB, AOF)</td>
<td>미지원</td>
</tr>
<tr>
<td><strong>복제/클러스터링</strong></td>
<td>지원</td>
<td>부분 지원</td>
</tr>
<tr>
<td><strong>Pub/Sub 기능</strong></td>
<td>지원</td>
<td>미지원</td>
</tr>
<tr>
<td><strong>사용 사례</strong></td>
<td>세션 관리, 순위, 실시간 분석</td>
<td>간단한 캐싱 전용</td>
</tr>
<tr>
<td><strong>운영 복잡도</strong></td>
<td>다소 높음</td>
<td>단순</td>
</tr>
</tbody></table>
<hr />
<h2 id="8️⃣-현업-활용-사례">8️⃣ 현업 활용 사례</h2>
<h3 id="🏢-대형-쇼핑몰">🏢 대형 쇼핑몰</h3>
<p>인기상품 조회, 세션 데이터, 추천 결과를 Redis 캐시로 관리</p>
<h3 id="🏦-금융-시스템">🏦 금융 시스템</h3>
<p>잦은 잔액 조회·계좌 인증 요청을 캐시로 가속화</p>
<h3 id="🎮-게임-서비스">🎮 게임 서비스</h3>
<p>실시간 순위(Leaderboard)와 랭킹 시스템 Redis로 구현</p>
<h3 id="💬-메시징--채팅-시스템">💬 메시징 / 채팅 시스템</h3>
<p>Pub/Sub 기능으로 실시간 메시지 브로커 역할 수행</p>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<p>Amazon ElastiCache = 완전관리형 인메모리 캐시 서비스</p>
<p>지원 엔진: Redis / Memcached</p>
<p>장점: 초고속 응답, 고가용성, 확장성, 서버 관리 불필요</p>
<p>현업 활용: 세션 관리, 순위 시스템, 쿼리 캐싱, 실시간 데이터 처리</p>
<p>👉 한마디로,
“ElastiCache는 DB 부하를 줄이고 속도를 극대화하는 AWS의 메모리 가속기” 입니다.</p>