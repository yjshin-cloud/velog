<h1 id="🧠-aws-sct-schema-conversion-tool-정리">🧠 AWS SCT (Schema Conversion Tool) 정리</h1>
<hr />
<h2 id="1️⃣-aws-sct란">1️⃣ AWS SCT란?</h2>
<p>AWS Schema Conversion Tool (SCT) 는
온프레미스나 타사 클라우드의 데이터베이스 스키마(테이블 구조, SQL, 뷰, 함수 등) 를
AWS 데이터베이스 형식으로 자동 변환해주는 무료 도구입니다.</p>
<p>👉 쉽게 말해,
“Oracle, SQL Server 같은 DB 구조를 AWS RDS나 Aurora용으로 자동 바꿔주는 도구” 입니다.</p>
<hr />
<h2 id="2️⃣-주요-역할">2️⃣ 주요 역할</h2>
<table>
<thead>
<tr>
<th>기능</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>🧩 <strong>스키마 변환 (Schema Conversion)</strong></td>
<td>기존 DB의 테이블 구조, 인덱스, 프로시저 등을 대상 DB 포맷으로 자동 변환</td>
</tr>
<tr>
<td>⚙️ <strong>데이터베이스 호환성 분석</strong></td>
<td>변환 가능 여부 및 수동 수정이 필요한 항목 자동 분석</td>
</tr>
<tr>
<td>📊 <strong>변환 리포트 제공</strong></td>
<td>변환 성공률, 비호환 객체, SQL 수정 제안 리포트 생성</td>
</tr>
<tr>
<td>🔄 <strong>DMS와 통합 연동</strong></td>
<td>DMS(Database Migration Service)와 함께 데이터까지 자동 마이그레이션 가능</td>
</tr>
<tr>
<td>☁️ <strong>데이터 웨어하우스 변환 지원</strong></td>
<td>OLTP DB → Amazon Redshift로 변환 지원</td>
</tr>
</tbody></table>
<hr />
<h2 id="3️⃣-주요-사용-시나리오">3️⃣ 주요 사용 시나리오</h2>
<table>
<thead>
<tr>
<th>시나리오</th>
<th>예시</th>
</tr>
</thead>
<tbody><tr>
<td>✅ <strong>이기종 마이그레이션 (Heterogeneous Migration)</strong></td>
<td>Oracle → Amazon Aurora (PostgreSQL/MySQL 호환)</td>
</tr>
<tr>
<td>✅ <strong>데이터 웨어하우스 이전</strong></td>
<td>Teradata / Netezza → Amazon Redshift</td>
</tr>
<tr>
<td>✅ <strong>클라우드 통합 마이그레이션</strong></td>
<td>SQL Server (On-Premise) → AWS RDS</td>
</tr>
<tr>
<td>✅ <strong>Hybrid 환경 마이그레이션</strong></td>
<td>일부만 AWS로 이전, 나머지 온프레미스 유지</td>
</tr>
</tbody></table>
<hr />
<h2 id="4️⃣-aws-sct--dms-아키텍처-시각화">4️⃣ AWS SCT + DMS 아키텍처 시각화</h2>
<pre><code class="language-mermaid">flowchart TD
    A[&quot;🏠 On-Premise DB (💾 Oracle · SQL Server · etc.)&quot;] --&gt; B[&quot;🧰 AWS SCT (Schema Conversion Tool)&quot;]
    B --&gt; C[&quot;📘 Converted Schema (🐘 PostgreSQL · 🌊 Aurora · 🧮 Redshift)&quot;]
    A --&gt; D[&quot;⚙️ AWS DMS (Database Migration Service)&quot;]
    D --&gt; E[&quot;🎯 Target DB (☁️ RDS · 🌊 Aurora · 🧮 Redshift)&quot;]
    B --&gt; F[&quot;📝 Migration Assessment Report&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/ec746210-ab76-4b1f-b4f9-f89f35e11cb9/image.png" /></p>
<p>🧠 설명:</p>
<p>AWS SCT로 스키마를 변환하고,</p>
<p>AWS DMS로 데이터를 복제(이전) 하며,</p>
<p>AWS에서 최종 운영 환경으로 이전 완료.</p>
<hr />
<h2 id="5️⃣-지원되는-변환-유형">5️⃣ 지원되는 변환 유형</h2>
<table>
<thead>
<tr>
<th>소스 DB</th>
<th>대상 DB</th>
</tr>
</thead>
<tbody><tr>
<td>Oracle</td>
<td>Amazon Aurora / PostgreSQL / MySQL / Redshift</td>
</tr>
<tr>
<td>SQL Server</td>
<td>Amazon Aurora / PostgreSQL / Redshift</td>
</tr>
<tr>
<td>MySQL</td>
<td>Amazon Aurora / PostgreSQL / Redshift</td>
</tr>
<tr>
<td>Db2 / Sybase</td>
<td>Amazon RDS / Redshift</td>
</tr>
<tr>
<td>Teradata / Netezza</td>
<td>Amazon Redshift</td>
</tr>
</tbody></table>
<hr />
<h2 id="6️⃣-aws-sct-변환-단계">6️⃣ AWS SCT 변환 단계</h2>
<table>
<thead>
<tr>
<th>단계</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>① <strong>소스 DB 연결</strong></td>
<td>온프레미스 DB에 연결</td>
</tr>
<tr>
<td>② <strong>대상 DB 연결</strong></td>
<td>RDS / Aurora / Redshift 등 AWS DB 연결</td>
</tr>
<tr>
<td>③ <strong>스키마 분석</strong></td>
<td>변환 가능 여부 및 비호환 요소 탐지</td>
</tr>
<tr>
<td>④ <strong>자동 변환 수행</strong></td>
<td>테이블, 뷰, 인덱스, 함수, 프로시저 변환</td>
</tr>
<tr>
<td>⑤ <strong>검토 및 수동 수정</strong></td>
<td>일부 SQL 구문은 수동으로 조정</td>
</tr>
<tr>
<td>⑥ <strong>AWS DMS와 연동</strong></td>
<td>데이터 복사(ETL) 진행</td>
</tr>
</tbody></table>
<hr />
<h2 id="7️⃣-변환-리포트-예시-assessment-report">7️⃣ 변환 리포트 예시 (Assessment Report)</h2>
<p>✅ Conversion Success Rate: 변환 가능한 객체 비율</p>
<p>⚠️ Action Items: 수동 변환 필요 SQL / Stored Procedure</p>
<p>📄 Recommendations: AWS DB 엔진별 최적화 제안</p>
<p>🧠 예시</p>
<p>Oracle DB의 PL/SQL → PostgreSQL의 PL/pgSQL로 변환
일부 패키지 함수(DBMS_OUTPUT.PUT_LINE)는 수동 수정 필요</p>
<hr />
<h2 id="8️⃣-현업-활용-사례">8️⃣ 현업 활용 사례</h2>
<table>
<thead>
<tr>
<th>산업</th>
<th>활용 예시</th>
</tr>
</thead>
<tbody><tr>
<td>🏦 <strong>금융권</strong></td>
<td>Oracle → Amazon Aurora PostgreSQL 마이그레이션</td>
</tr>
<tr>
<td>🏭 <strong>제조 / IoT</strong></td>
<td>온프레미스 SQL Server → RDS MySQL 변환</td>
</tr>
<tr>
<td>🧠 <strong>데이터 분석 플랫폼</strong></td>
<td>Teradata → Redshift 이전 후 Glue + QuickSight 분석</td>
</tr>
<tr>
<td>🏢 <strong>공공기관</strong></td>
<td>상용 DB → 오픈소스 Aurora PostgreSQL로 비용 절감 전환</td>
</tr>
</tbody></table>
<hr />
<h2 id="9️⃣-aws-dms와의-연계-요약">9️⃣ AWS DMS와의 연계 요약</h2>
<table>
<thead>
<tr>
<th>항목</th>
<th>AWS SCT</th>
<th>AWS DMS</th>
</tr>
</thead>
<tbody><tr>
<td>역할</td>
<td>스키마 및 코드 변환</td>
<td>데이터 마이그레이션</td>
</tr>
<tr>
<td>대상</td>
<td>테이블 구조, SQL, 프로시저</td>
<td>실제 데이터</td>
</tr>
<tr>
<td>실행 시점</td>
<td>사전 변환 단계</td>
<td>변환 후 실시간 복제</td>
</tr>
<tr>
<td>통합 방식</td>
<td>DMS 프로젝트와 연계 가능</td>
<td>SCT 변환 스키마 기반으로 데이터 복제</td>
</tr>
</tbody></table>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<p>AWS SCT (Schema Conversion Tool) = 데이터베이스 스키마 변환 도구</p>
<p>주요 기능: 스키마 변환, 호환성 분석, 리포트 생성, DMS 연동</p>
<p>장점:</p>
<p>이기종 DB 간 구조 변환 자동화</p>
<p>변환 리포트로 위험도 사전 파악 가능</p>
<p>DMS와 함께 사용 시 완전 자동화된 마이그레이션 구현</p>
<p>활용: Oracle → Aurora, Teradata → Redshift, SQL Server → PostgreSQL</p>
<p>👉 한마디로,
“AWS SCT는 데이터베이스 마이그레이션의 설계자(Structure Transformer)” 입니다.</p>