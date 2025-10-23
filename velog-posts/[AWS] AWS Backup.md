<h1 id="💾-aws-backup-정리">💾 AWS Backup 정리</h1>
<hr />
<h2 id="1️⃣-aws-backup이란">1️⃣ AWS Backup이란?</h2>
<p>AWS Backup은
AWS 리소스의 백업(Backup) 생성, 관리, 복구를 중앙에서 자동화해주는 서비스입니다.</p>
<p>👉 쉽게 말해,
“여러 AWS 서비스의 백업을 한 곳에서 관리할 수 있는 통합 백업 솔루션” 입니다.</p>
<hr />
<h2 id="2️⃣-주요-특징">2️⃣ 주요 특징</h2>
<table>
<thead>
<tr>
<th>기능</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>☁️ <strong>중앙 집중 관리</strong></td>
<td>S3, EBS, RDS, DynamoDB, EFS, FSx 등의 백업을 한 콘솔에서 관리</td>
</tr>
<tr>
<td>⏱ <strong>자동 백업 스케줄링</strong></td>
<td>정책 기반으로 주기적인 백업 자동 수행</td>
</tr>
<tr>
<td>🔒 <strong>보안 및 암호화</strong></td>
<td>AWS KMS 통합으로 백업 데이터 암호화</td>
</tr>
<tr>
<td>🧱 <strong>크로스 리전 / 크로스 계정 백업</strong></td>
<td>다른 리전 또는 계정으로 백업 복제 가능</td>
</tr>
<tr>
<td>🧩 <strong>정책 기반 백업 (Backup Plan)</strong></td>
<td>특정 리소스 그룹별 백업 주기, 보존 기간 자동화</td>
</tr>
<tr>
<td>🩹 <strong>신속한 복구</strong></td>
<td>클릭 한 번으로 백업에서 복구 가능</td>
</tr>
</tbody></table>
<hr />
<h2 id="3️⃣-아키텍처-시각화">3️⃣ 아키텍처 시각화</h2>
<hr />
<pre><code class="language-mermaid">flowchart TD
    A[&quot;AWS 리소스 (EC2 / RDS / EFS / DynamoDB 등)&quot;] --&gt; B[&quot;AWS Backup&quot;]
    B --&gt; C[&quot;Backup Vault (암호화된 저장소)&quot;]
    B --&gt; D[&quot;Cross-Region / Cross-Account Backup&quot;]
    C --&gt; E[&quot;복구 (Restore)&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/c76f7676-14ec-424d-8120-ae66e1af16c6/image.png" /></p>
<hr />
<h2 id="4️⃣-주요-구성-요소">4️⃣ 주요 구성 요소</h2>
<hr />
<table>
<thead>
<tr>
<th>구성 요소</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td><strong>Backup Plan</strong></td>
<td>백업 일정, 보존 기간, 규칙 정의</td>
</tr>
<tr>
<td><strong>Backup Vault</strong></td>
<td>백업 데이터가 저장되는 암호화 스토리지</td>
</tr>
<tr>
<td><strong>Backup Policy</strong></td>
<td>조직 단위(Organizations)로 백업 규칙 자동 적용</td>
</tr>
<tr>
<td><strong>Recovery Point</strong></td>
<td>실제 복원 가능한 시점(백업 결과물)</td>
</tr>
<tr>
<td><strong>AWS Organizations 통합</strong></td>
<td>여러 계정의 백업 정책 중앙 관리 가능</td>
</tr>
</tbody></table>
<hr />
<h2 id="5️⃣-백업-가능한-주요-서비스">5️⃣ 백업 가능한 주요 서비스</h2>
<table>
<thead>
<tr>
<th>서비스</th>
<th>백업 가능 항목</th>
</tr>
</thead>
<tbody><tr>
<td><strong>EBS</strong></td>
<td>스냅샷</td>
</tr>
<tr>
<td><strong>RDS / Aurora</strong></td>
<td>DB 백업</td>
</tr>
<tr>
<td><strong>DynamoDB</strong></td>
<td>테이블 백업</td>
</tr>
<tr>
<td><strong>EFS / FSx</strong></td>
<td>파일시스템 백업</td>
</tr>
<tr>
<td><strong>EC2</strong></td>
<td>인스턴스 상태 포함 전체 백업</td>
</tr>
<tr>
<td><strong>Storage Gateway</strong></td>
<td>온프레미스 백업 데이터 연동</td>
</tr>
</tbody></table>
<hr />
<h2 id="6️⃣-현업-활용-사례">6️⃣ 현업 활용 사례</h2>
<h3 id="🏢-기업-운영-데이터-보호">🏢 기업 운영 데이터 보호</h3>
<p>RDS, EFS 백업을 자동 스케줄링 → 데이터 유실 방지</p>
<h3 id="🌍-재해-복구disaster-recovery">🌍 재해 복구(Disaster Recovery)</h3>
<p>다른 리전으로 자동 복제 → 리전 장애에도 복구 가능</p>
<h3 id="🧑💻-컴플라이언스-대응">🧑‍💻 컴플라이언스 대응</h3>
<p>ISO, SOC, GDPR 등 규제에 맞는 백업 정책 관리</p>
<h3 id="🧰-msp--멀티계정-운영">🧰 MSP / 멀티계정 운영</h3>
<p>AWS Organizations 통합으로 여러 계정의 백업 정책 중앙화</p>
<hr />
<h2 id="7️⃣-aws-backup--organizations--vault-구조-예시">7️⃣ AWS Backup + Organizations + Vault 구조 예시</h2>
<hr />
<pre><code class="language-mermaid">flowchart TD
    A[&quot;Management Account&quot;] --&gt; B[&quot;AWS Backup Plan (정책)&quot;]
    B --&gt; C[&quot;Member Accounts&quot;]
    C --&gt; D[&quot;Backup Vault (각 리전별 저장소)&quot;]
    D --&gt; E[&quot;Cross-Region / Cross-Account 복제&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/4a802610-0d58-434f-92a6-711c13ff0a1c/image.png" /></p>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<p>AWS Backup = 백업 자동화 및 중앙 관리 서비스</p>
<p>주요 기능: 스케줄링, 암호화, 복제, 복구</p>
<p>백업 대상: EBS, RDS, DynamoDB, EFS, FSx, EC2 등</p>
<p>현업 활용: DR 구축, 데이터 보호, 규제 준수, 멀티계정 백업 정책 관리</p>
<h2 id="👉-한마디로-aws-backup은-클라우드-환경의-데이터-안전벨트-역할을-하는-서비스-입니다">👉 한마디로, “AWS Backup은 클라우드 환경의 데이터 안전벨트 역할을 하는 서비스” 입니다.</h2>