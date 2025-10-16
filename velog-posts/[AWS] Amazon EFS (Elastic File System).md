<h1 id="📁-amazon-efs-elastic-file-system-정리">📁 Amazon EFS (Elastic File System) 정리</h1>
<hr />
<h2 id="1️⃣-amazon-efs란">1️⃣ Amazon EFS란?</h2>
<p>Amazon EFS (Elastic File System) 는
AWS에서 제공하는 완전관리형 네트워크 파일 스토리지(NAS) 서비스입니다.</p>
<p>👉 쉽게 말해,
“여러 EC2 인스턴스에서 동시에 접근할 수 있는 공유 폴더” 입니다.</p>
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
<td>☁️ <strong>완전관리형 서비스</strong></td>
<td>파일 서버 구축·운영 불필요 (AWS가 자동 관리)</td>
</tr>
<tr>
<td>📂 <strong>공유 스토리지</strong></td>
<td>여러 EC2 인스턴스가 동시에 접근 가능 (Linux NFS 방식)</td>
</tr>
<tr>
<td>📈 <strong>자동 확장(Elastic)</strong></td>
<td>저장 용량이 자동으로 확장/축소됨</td>
</tr>
<tr>
<td>🛡 <strong>고가용성 &amp; 내구성</strong></td>
<td>리전 내 여러 AZ에 자동 복제</td>
</tr>
<tr>
<td>💰 <strong>종량제 과금(Pay-as-you-go)</strong></td>
<td>저장한 데이터 용량만큼만 비용 부과</td>
</tr>
<tr>
<td>🔒 <strong>보안 통합</strong></td>
<td>IAM, Security Group, KMS 암호화 지원</td>
</tr>
</tbody></table>
<hr />
<h2 id="3️⃣-아키텍처-시각화">3️⃣ 아키텍처 시각화</h2>
<pre><code class="language-mermaid">flowchart TD
    A[&quot;EC2 Instance #1&quot;] --&gt; B[&quot;Amazon EFS&quot;]
    C[&quot;EC2 Instance #2&quot;] --&gt; B
    D[&quot;Lambda / ECS / EKS&quot;] --&gt; B
    B --&gt; E[&quot;S3 Backup (Lifecycle 관리 가능)&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/6c3fe620-b3f3-4705-926f-21df20e5706a/image.png" /></p>
<p>🧠 설명:
EFS는 여러 EC2, Lambda, ECS 등에서 동시에 연결되어 파일 데이터를 공유할 수 있으며,
파일 서버를 직접 구축하지 않아도 됩니다.</p>
<hr />
<h2 id="4️⃣-ebs--efs--s3-비교">4️⃣ EBS / EFS / S3 비교</h2>
<table>
<thead>
<tr>
<th>구분</th>
<th><strong>EBS</strong></th>
<th><strong>EFS</strong></th>
<th><strong>S3</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>형태</strong></td>
<td>블록 스토리지</td>
<td>파일 스토리지</td>
<td>객체 스토리지</td>
</tr>
<tr>
<td><strong>접근 방식</strong></td>
<td>1개의 EC2에만 연결</td>
<td>여러 EC2에서 동시 접근</td>
<td>웹/API 기반 접근</td>
</tr>
<tr>
<td><strong>확장성</strong></td>
<td>수동 확장</td>
<td>자동 확장</td>
<td>무한 확장</td>
</tr>
<tr>
<td><strong>프로토콜</strong></td>
<td>블록 (ext4, XFS)</td>
<td>NFS</td>
<td>HTTPS / SDK</td>
</tr>
<tr>
<td><strong>사용 예시</strong></td>
<td>데이터베이스, OS 디스크</td>
<td>애플리케이션 로그, 공유 폴더</td>
<td>백업, 이미지 저장소</td>
</tr>
</tbody></table>
<hr />
<p>5️⃣ 현업 활용 사례</p>
<h3 id="🧩-웹-애플리케이션-공유-스토리지">🧩 웹 애플리케이션 공유 스토리지</h3>
<p>여러 EC2 인스턴스가 동일한 코드나 이미지 파일을 공유</p>
<h3 id="🧠-머신러닝-학습-데이터-저장소">🧠 머신러닝 학습 데이터 저장소</h3>
<p>EFS에 대규모 학습 데이터 저장 → SageMaker/Lambda에서 접근</p>
<h3 id="🧾-로그-수집-및-분석">🧾 로그 수집 및 분석</h3>
<p>여러 서버의 로그를 한 곳(EFS)에 모아 분석</p>
<h3 id="🧰-ecs--eks-컨테이너-공유-파일시스템">🧰 ECS / EKS 컨테이너 공유 파일시스템</h3>
<p>컨테이너 간 공용 데이터 저장</p>
<hr />
<h2 id="6️⃣-주요-사용-시-고려-사항">6️⃣ 주요 사용 시 고려 사항</h2>
<table>
<thead>
<tr>
<th>항목</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td><strong>성능 모드</strong></td>
<td>General Purpose / Max I/O 선택 가능</td>
</tr>
<tr>
<td><strong>스루풋 모드</strong></td>
<td>Bursting / Provisioned</td>
</tr>
<tr>
<td><strong>마운트 방식</strong></td>
<td>NFS v4.1 (Linux 기반)</td>
</tr>
<tr>
<td><strong>백업</strong></td>
<td>AWS Backup 또는 Lifecycle 정책으로 S3에 저장 가능</td>
</tr>
<tr>
<td><strong>비용 최적화</strong></td>
<td>자주 쓰지 않는 데이터는 “EFS Infrequent Access (EFS-IA)”로 자동 이동</td>
</tr>
</tbody></table>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<p>Amazon EFS = 완전관리형 공유 파일 스토리지 서비스</p>
<p>여러 EC2, Lambda, ECS 등에서 동시에 접근 가능</p>
<p>자동 확장 + 다중 AZ 복제 + 높은 내구성 제공</p>
<p>현업 활용: 공유 코드 저장소, 로그 분석, 머신러닝 데이터 저장, 컨테이너 파일 공유</p>
<p>👉 한마디로,
“AWS에서 클릭 몇 번으로 구축하는 고가용성 네트워크 파일 서버 (NAS)” 입니다.</p>