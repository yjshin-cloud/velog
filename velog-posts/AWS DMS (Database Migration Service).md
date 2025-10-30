<h1 id="🔄-aws-dms-database-migration-service-정리">🔄 AWS DMS (Database Migration Service) 정리</h1>
<hr />
<h2 id="1️⃣-aws-dms란">1️⃣ AWS DMS란?</h2>
<p>AWS DMS (Database Migration Service) 는
온프레미스나 클라우드 환경에 있는 데이터베이스를
AWS로 손쉽게 이전(Migration) 하도록 도와주는 서비스입니다.</p>
<p>👉 쉽게 말해,
“운영 중인 DB를 중단하지 않고, AWS로 안전하게 옮겨주는 이사 도우미 서비스” 입니다.</p>
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
<td>🚀 <strong>무중단 마이그레이션 (Minimal Downtime)</strong></td>
<td>기존 DB를 계속 사용하면서 실시간으로 데이터 복제</td>
</tr>
<tr>
<td>🔁 <strong>동종 및 이기종 간 마이그레이션 지원</strong></td>
<td>Oracle → Oracle 뿐 아니라, Oracle → Aurora / PostgreSQL 등 이기종 간 이전도 가능</td>
</tr>
<tr>
<td>⚙️ <strong>자동화된 복제 관리</strong></td>
<td>데이터 추출, 변환, 적재(ETL) 과정 자동 수행</td>
</tr>
<tr>
<td>💾 <strong>CDC (Change Data Capture)</strong></td>
<td>변경된 데이터만 지속적으로 동기화</td>
</tr>
<tr>
<td>☁️ <strong>안정성 &amp; 복구 지원</strong></td>
<td>실패 시 자동 재시작, 오류 로그 추적</td>
</tr>
<tr>
<td>🛡 <strong>보안 통합</strong></td>
<td>KMS 암호화, IAM 인증, VPC/Subnet 보안 그룹 연동</td>
</tr>
</tbody></table>
<hr />
<h2 id="3️⃣-지원-소스source--대상target">3️⃣ 지원 소스(Source) &amp; 대상(Target)</h2>
<table>
<thead>
<tr>
<th>소스 DB</th>
<th>대상 DB</th>
</tr>
</thead>
<tbody><tr>
<td>Oracle</td>
<td>Aurora, RDS, Redshift</td>
</tr>
<tr>
<td>MySQL</td>
<td>MySQL, PostgreSQL</td>
</tr>
<tr>
<td>SQL Server</td>
<td>S3, DynamoDB</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>Snowflake, Redshift</td>
</tr>
<tr>
<td>MongoDB</td>
<td>DocumentDB</td>
</tr>
<tr>
<td>On-Premise DB</td>
<td>AWS 클라우드 DB 전체 지원</td>
</tr>
</tbody></table>
<hr />
<h2 id="4️⃣-아키텍처-시각화">4️⃣ 아키텍처 시각화</h2>
<pre><code class="language-mermaid">flowchart TD
    A[&quot;On-Premise / Other Cloud DB (Source)&quot;] --&gt; B[&quot;AWS DMS Replication Instance&quot;]
    B --&gt; C[&quot;Amazon RDS / Aurora / Redshift / S3 (Target)&quot;]
    B --&gt; D[&quot;CDC (Change Data Capture) - 실시간 변경 데이터 동기화&quot;]
    C --&gt; E[&quot;AWS Analytics / Application&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/96d422d9-6e6c-46cb-984b-119b699d3378/image.png" /></p>
<p>🧠 설명:</p>
<p>Replication Instance: DMS의 핵심 컴퓨팅 리소스 (데이터 추출·변환·복제 담당)</p>
<p>CDC(Change Data Capture): 소스 DB의 변경 사항을 지속적으로 추적 및 반영</p>
<p>Target: RDS, S3, Redshift 등 AWS 내 데이터 저장소</p>
<hr />
<h2 id="5️⃣-dms-동작-과정">5️⃣ DMS 동작 과정</h2>
<table>
<thead>
<tr>
<th>단계</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>① <strong>소스/타깃 연결 설정</strong></td>
<td>온프레미스 DB와 AWS DB 연결 구성</td>
</tr>
<tr>
<td>② <strong>Replication Instance 생성</strong></td>
<td>마이그레이션 담당 EC2 역할 수행</td>
</tr>
<tr>
<td>③ <strong>테이블 매핑 및 변환 규칙 설정</strong></td>
<td>복사할 데이터 및 변환 규칙 지정</td>
</tr>
<tr>
<td>④ <strong>Full Load 수행</strong></td>
<td>기존 데이터 전체 복제</td>
</tr>
<tr>
<td>⑤ <strong>CDC 수행 (실시간 변경 동기화)</strong></td>
<td>소스 DB의 변경사항을 지속 반영</td>
</tr>
<tr>
<td>⑥ <strong>Cutover (전환)</strong></td>
<td>새 DB로 전환 후 운영 환경 전환 완료</td>
</tr>
</tbody></table>
<hr />
<h2 id="6️⃣-현업-활용-사례">6️⃣ 현업 활용 사례</h2>
<table>
<thead>
<tr>
<th>산업</th>
<th>활용 예시</th>
</tr>
</thead>
<tbody><tr>
<td>🏢 <strong>금융 / 공공기관</strong></td>
<td>Oracle → Amazon Aurora PostgreSQL 이전</td>
</tr>
<tr>
<td>🏭 <strong>제조 / IoT</strong></td>
<td>공장 DB를 S3로 이전해 Athena/Glue로 분석</td>
</tr>
<tr>
<td>🛒 <strong>이커머스 / 리테일</strong></td>
<td>실시간 CDC로 주문 데이터 Redshift로 동기화</td>
</tr>
<tr>
<td>🧠 <strong>데이터 분석 플랫폼</strong></td>
<td>RDS → S3 → Glue → QuickSight 분석 파이프라인 구성</td>
</tr>
</tbody></table>
<hr />
<h2 id="7️⃣-aws-dms--sct-조합">7️⃣ AWS DMS + SCT 조합</h2>
<p>DMS 단독으로도 마이그레이션 가능하지만, DB 스키마 변환이 필요한 경우
함께 쓰이는 도구가 바로 AWS SCT (Schema Conversion Tool) 입니다.</p>
<p>도구    역할
AWS SCT    스키마 변환 (예: Oracle → PostgreSQL 구조 변환)
AWS DMS    실제 데이터 복제 및 전송 담당</p>
<p>🧩 둘을 함께 사용하면 완전 자동화된 마이그레이션 가능!</p>
<hr />
<h2 id="8️⃣-aws-dms--analytics-통합-예시">8️⃣ AWS DMS + Analytics 통합 예시</h2>
<pre><code class="language-mermaid">flowchart TD
    A[&quot;On-Premise DB&quot;] --&gt; B[&quot;AWS DMS&quot;]
    B --&gt; C[&quot;Amazon S3 (Raw Data)&quot;]
    C --&gt; D[&quot;AWS Glue (ETL 변환)&quot;]
    D --&gt; E[&quot;Amazon Redshift (Data Warehouse)&quot;]
    E --&gt; F[&quot;Amazon QuickSight (BI 대시보드)&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/bf960fac-d7e2-4f21-b95d-59a771c09b83/image.png" /></p>
<p>📊 설명:
온프레미스 데이터베이스 → DMS로 AWS S3에 저장 → Glue로 정제 → Redshift에서 분석 → QuickSight로 시각화</p>
<p>💡 단계별 설명</p>
<table>
<thead>
<tr>
<th>단계</th>
<th>구성 요소</th>
</tr>
</thead>
<tbody><tr>
<td>🏠 <strong>On-Premise DB</strong></td>
<td>내부 서버나 타 클라우드의 원본 데이터 저장소</td>
</tr>
<tr>
<td>⚙️ <strong>AWS DMS</strong></td>
<td>데이터를 안전하게 AWS로 복제 및 이전</td>
</tr>
<tr>
<td>🪣 <strong>Amazon S3</strong></td>
<td>수집된 Raw 데이터를 저장하는 Data Lake 영역</td>
</tr>
<tr>
<td>🧩 <strong>AWS Glue</strong></td>
<td>ETL(Extract, Transform, Load) 작업으로 데이터 정제 및 변환</td>
</tr>
<tr>
<td>🏢 <strong>Amazon Redshift</strong></td>
<td>정제된 데이터를 분석용으로 저장하는 Data Warehouse</td>
</tr>
<tr>
<td>📊 <strong>Amazon QuickSight</strong></td>
<td>Redshift의 데이터를 시각화해 BI 대시보드로 제공</td>
</tr>
</tbody></table>
<hr />
<h2 id="9️⃣-✅-정리">9️⃣ ✅ 정리</h2>
<p>AWS DMS = 데이터베이스 마이그레이션 및 복제 서비스</p>
<p>장점:</p>
<p>무중단 데이터 이전</p>
<p>동종/이기종 간 마이그레이션 지원</p>
<p>CDC로 실시간 변경 반영</p>
<p>주요 구성: Source → DMS Replication Instance → Target</p>
<p>현업 활용: DB 이전, 데이터 분석 파이프라인, 클라우드 통합</p>
<p>👉 한마디로,
“AWS DMS는 데이터베이스를 중단 없이 클라우드로 이사시키는 자동 복제 도구” 입니다.</p>