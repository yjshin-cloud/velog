<h1 id="💾-aws-ebs-elastic-block-store-정리">💾 AWS EBS (Elastic Block Store) 정리</h1>
<h2 id="1️⃣-aws-ebs란">1️⃣ AWS EBS란?</h2>
<p><strong>Amazon EBS (Elastic Block Store)</strong> 는<br />Amazon EC2 인스턴스에서 사용하는 <strong>블록 수준의 스토리지 서비스</strong>입니다.</p>
<p>👉 쉽게 말해,<br /><strong>“EC2에 붙여 쓰는 가상 하드디스크”</strong> 라고 이해하면 됩니다.</p>
<hr />
<h2 id="2️⃣-주요-특징">2️⃣ 주요 특징</h2>
<ul>
<li><p>📂 <strong>블록 스토리지</strong></p>
<ul>
<li>일반적인 하드디스크처럼 파일 시스템을 올려 사용</li>
</ul>
</li>
<li><p>🔄 <strong>탄력성</strong></p>
<ul>
<li>필요에 따라 크기 확장/축소 가능</li>
</ul>
</li>
<li><p>🛡️ <strong>내구성 &amp; 가용성</strong></p>
<ul>
<li>동일 AZ(가용영역) 내에서 자동 복제 → 데이터 손실 방지</li>
</ul>
</li>
<li><p>🚀 <strong>성능 옵션 다양</strong></p>
<ul>
<li>범용 SSD (gp3), 프로비저닝 IOPS SSD (io2), HDD (st1, sc1) 등 워크로드에 맞게 선택</li>
</ul>
</li>
<li><p>💾 <strong>스냅샷(Snapshot)</strong></p>
<ul>
<li><p>S3에 저장되는 백업 기능 제공</p>
</li>
<li><p>다른 AZ/리전으로 복제 가능</p>
</li>
</ul>
</li>
</ul>
<hr />
<h2 id="3️⃣-아키텍처-시각화">3️⃣ 아키텍처 시각화</h2>
<pre><code class="language-mermaid">
flowchart TD
    A[&quot;Amazon EC2 Instance&quot;] --&gt; B[&quot;Attached EBS Volume&quot;]
    B --&gt; C[&quot;Data Storage (Block Level)&quot;]
    B --&gt; D[&quot;EBS Snapshot (Stored in S3)&quot;]
</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/82160a25-a8ac-4bdf-b520-4672b3c143b7/image.png" /></p>
<hr />
<h2 id="4️⃣-ebs-볼륨-유형">4️⃣ EBS 볼륨 유형</h2>
<ol>
<li><p><strong>SSD 계열</strong></p>
<ul>
<li><p><code>gp3</code> (범용 SSD): 대부분의 워크로드에 적합, 가격/성능 균형</p>
</li>
<li><p><code>io2</code> (프로비저닝 IOPS SSD): 높은 성능/일관된 IOPS, DB용</p>
</li>
</ul>
</li>
<li><p><strong>HDD 계열</strong></p>
<ul>
<li><p><code>st1</code> (처리량 최적화 HDD): 빅데이터, 로그 처리</p>
</li>
<li><p><code>sc1</code> (Cold HDD): 잘 쓰지 않는 데이터 아카이빙</p>
</li>
</ul>
</li>
</ol>
<hr />
<h2 id="5️⃣-현업-활용-사례">5️⃣ 현업 활용 사례</h2>
<ul>
<li><p>🛠 <strong>운영 DB 스토리지</strong> → RDS, EC2 기반 DB 서버에 고성능 io2 EBS 사용</p>
</li>
<li><p>📊 <strong>로그/데이터 처리</strong> → st1 HDD로 대규모 로그 저장</p>
</li>
<li><p>🛡️ <strong>백업 &amp; 복구</strong> → 스냅샷으로 자동 백업/재해 복구(DR) 활용</p>
</li>
<li><p>🚀 <strong>테스트 환경 복제</strong> → 스냅샷으로 동일한 개발/테스트 환경 생성</p>
</li>
</ul>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<ul>
<li><p><strong>EBS = EC2 인스턴스에 붙이는 블록 스토리지</strong></p>
</li>
<li><p>특징: <strong>고성능, 내구성, 스냅샷, 다양한 볼륨 타입</strong></p>
</li>
<li><p>현업 활용: <strong>DB, 로그 저장, 백업/복구, 테스트 환경 복제</strong></p>
</li>
</ul>
<p>👉 한마디로, <strong>“EC2 전용 가상 하드디스크”</strong> 입니다.</p>