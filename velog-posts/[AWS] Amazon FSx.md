<h1 id="🗂️-aws-fsx-amazon-fsx-정리">🗂️ AWS FSx (Amazon FSx) 정리</h1>
<hr />
<h2 id="1️⃣-aws-fsx란">1️⃣ AWS FSx란?</h2>
<p>Amazon FSx는 AWS에서 제공하는 완전관리형 파일 스토리지 서비스입니다.
기업이 사용하는 Windows, Lustre, NetApp, OpenZFS 같은 파일 시스템을
AWS 클라우드 환경에서 손쉽게 구축하고 운영할 수 있도록 지원합니다.</p>
<p>👉 쉽게 말해,
“AWS에서 제공하는 고성능 네트워크 파일 서버 (NAS)” 라고 이해하면 됩니다.</p>
<hr />
<h2 id="2️⃣-주요-특징">2️⃣ 주요 특징</h2>
<h3 id="💾-파일-스토리지-file-storage">💾 파일 스토리지 (File Storage)</h3>
<p>EC2, 온프레미스 서버 등에서 네트워크 드라이브처럼 접근 가능 (SMB, NFS, Lustre 프로토콜)</p>
<h3 id="⚙️-완전관리형">⚙️ 완전관리형</h3>
<p>하드웨어, 백업, 패치, 확장 자동 관리</p>
<h3 id="⚡-고성능-io-지원">⚡ 고성능 I/O 지원</h3>
<p>머신러닝, HPC(고성능 컴퓨팅), 대규모 데이터 처리에 적합</p>
<h3 id="🔒-보안--통합">🔒 보안 &amp; 통합</h3>
<p>AWS IAM, VPC, KMS 암호화 지원</p>
<hr />
<h2 id="3️⃣-fsx-제품군-4가지-유형">3️⃣ FSx 제품군 (4가지 유형)</h2>
<hr />
<table>
<thead>
<tr>
<th>서비스</th>
<th>특징</th>
<th>사용 사례</th>
</tr>
</thead>
<tbody><tr>
<td><strong>FSx for Windows File Server</strong></td>
<td>SMB 프로토콜 기반, AD 통합 지원</td>
<td>Windows 워크로드, 파일 공유, 홈 디렉터리</td>
</tr>
<tr>
<td><strong>FSx for Lustre</strong></td>
<td>고성능 병렬 파일 시스템</td>
<td>머신러닝, 빅데이터, HPC 워크로드</td>
</tr>
<tr>
<td><strong>FSx for NetApp ONTAP</strong></td>
<td>스냅샷, 복제, 멀티프로토콜 지원</td>
<td>하이브리드 클라우드 스토리지, 백업</td>
</tr>
<tr>
<td><strong>FSx for OpenZFS</strong></td>
<td>ZFS 기반, 저지연 파일 액세스</td>
<td>데이터베이스 백업, 개발 환경</td>
</tr>
</tbody></table>
<hr />
<h2 id="4️⃣-아키텍처-시각화">4️⃣ 아키텍처 시각화</h2>
<pre><code class="language-mermaid">flowchart TD
    A[&quot;EC2 / 온프레미스 서버&quot;] --&gt; B[&quot;Amazon FSx File System&quot;]
    B --&gt; C[&quot;FSx for Windows (SMB)&quot;]
    B --&gt; D[&quot;FSx for Lustre (HPC, ML)&quot;]
    B --&gt; E[&quot;FSx for NetApp ONTAP&quot;]
    B --&gt; F[&quot;FSx for OpenZFS&quot;]
    B --&gt; G[&quot;S3 (데이터 백업/연동)&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/d145c66f-d090-47bf-89d3-22e4563891fe/image.png" /></p>
<hr />
<h2 id="5️⃣-특징별-정리">5️⃣ 특징별 정리</h2>
<h3 id="🧩-windows-호환성">🧩 Windows 호환성</h3>
<p>Active Directory, SMB, NTFS 지원</p>
<h3 id="🧠-aiml-워크로드-지원-fsx-for-lustre">🧠 AI/ML 워크로드 지원 (FSx for Lustre)</h3>
<p>S3와 연동 → 대규모 데이터셋 실시간 처리</p>
<h3 id="💾-데이터-백업-및-dr-disaster-recovery">💾 데이터 백업 및 DR (Disaster Recovery)</h3>
<p>자동 백업 + Cross-Region 복제 가능</p>
<h3 id="🧱-온프레미스-통합">🧱 온프레미스 통합</h3>
<p>AWS Direct Connect, VPN으로 연결 가능</p>
<hr />
<h2 id="6️⃣-현업-활용-사례">6️⃣ 현업 활용 사례</h2>
<h3 id="🏢-기업-파일-서버-마이그레이션">🏢 기업 파일 서버 마이그레이션</h3>
<p>온프레미스 Windows 파일 서버 → FSx for Windows로 이전</p>
<h3 id="🧬-머신러닝-학습-데이터-관리">🧬 머신러닝 학습 데이터 관리</h3>
<p>S3 데이터셋 → FSx for Lustre에서 병렬 처리</p>
<h3 id="🏦-금융제조-대용량-워크로드">🏦 금융/제조 대용량 워크로드</h3>
<p>HPC 시뮬레이션, 로그 분석, CAD 설계 파일 공유</p>
<h3 id="☁️-하이브리드-스토리지-구축">☁️ 하이브리드 스토리지 구축</h3>
<p>NetApp ONTAP 기반으로 클라우드/온프레미스 통합</p>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<p>AWS FSx = 완전관리형 네트워크 파일 시스템 서비스</p>
<p>제공 유형: Windows, Lustre, NetApp ONTAP, OpenZFS</p>
<p>장점: 성능, 보안, 확장성, 자동 관리</p>
<p>현업 활용: 파일 서버 대체, ML·HPC, 백업·DR, 하이브리드 환경 구축</p>
<h3 id="👉-한마디로-aws에서-클릭-몇-번으로-구축하는-고성능-기업용-파일-서버-입니다">👉 한마디로, “AWS에서 클릭 몇 번으로 구축하는 고성능 기업용 파일 서버” 입니다.</h3>