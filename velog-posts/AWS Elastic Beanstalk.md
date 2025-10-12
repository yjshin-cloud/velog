<h1 id="🌱-aws-elastic-beanstalk-정리">🌱 AWS Elastic Beanstalk 정리</h1>
<hr />
<h2 id="1️⃣-aws-elastic-beanstalk이란">1️⃣ AWS Elastic Beanstalk이란?</h2>
<p>AWS Elastic Beanstalk은
애플리케이션 배포와 관리를 자동으로 처리해주는 PaaS(Platform as a Service) 형태의 서비스입니다.</p>
<p>👉 쉽게 말해,
“서버 인프라 신경 안 쓰고, 코드를 올리면 AWS가 알아서 배포해주는 서비스” 입니다.</p>
<hr />
<h2 id="2️⃣-주요-특징">2️⃣ 주요 특징</h2>
<h3 id="🚀-자동-인프라-프로비저닝">🚀 자동 인프라 프로비저닝</h3>
<p>EC2, Auto Scaling, Load Balancer, Security Group 등을 자동으로 생성</p>
<h3 id="🧩-멀티-언어-지원">🧩 멀티 언어 지원</h3>
<p>Java, Python, Node.js, Go, PHP, Ruby, .NET 등</p>
<h3 id="⚙️-자동-배포--롤백">⚙️ 자동 배포 &amp; 롤백</h3>
<p>새 버전 배포 시 자동 트래픽 전환 및 장애 발생 시 롤백</p>
<h3 id="📈-모니터링-통합">📈 모니터링 통합</h3>
<p>CloudWatch, Health Dashboard로 상태 확인 가능</p>
<h3 id="💾-환경-구성-자동화">💾 환경 구성 자동화</h3>
<p>환경별(개발/운영) 설정, 버전 관리, 환경 변수 관리</p>
<hr />
<h2 id="3️⃣-아키텍처-시각화">3️⃣ 아키텍처 시각화</h2>
<hr />
<pre><code class="language-mermaid">flowchart TD
    A[&quot;👨‍💻 개발자&lt;br/&gt;(Code Push)&quot;] --&gt; B[&quot;🌿 AWS Elastic Beanstalk&quot;]
    B --&gt; C[&quot;💻 EC2 인스턴스&lt;br/&gt;(Auto Scaling)&quot;]
    B --&gt; D[&quot;⚖️ Application Load Balancer&quot;]
    B --&gt; E[&quot;🗄️ Amazon RDS&lt;br/&gt;(선택적 구성)&quot;]
    B --&gt; F[&quot;🪣 Amazon S3&lt;br/&gt;(배포 아티팩트 저장소)&quot;]
    B --&gt; G[&quot;📊 Amazon CloudWatch&lt;br/&gt;(모니터링 및 알람)&quot;]
    D --&gt; H[&quot;🌍 사용자&lt;br/&gt;(웹 요청)&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/401653f5-3a1a-46d4-8d2f-6cec4458d4b0/image.png" /></p>
<hr />
<h2 id="4️⃣-구성-요소">4️⃣ 구성 요소</h2>
<hr />
<table>
<thead>
<tr>
<th>구성 요소</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td><strong>Application</strong></td>
<td>Beanstalk에서 관리하는 전체 앱 단위</td>
</tr>
<tr>
<td><strong>Environment</strong></td>
<td>개발/운영 환경 (예: dev, prod)</td>
</tr>
<tr>
<td><strong>Version</strong></td>
<td>애플리케이션 배포 버전</td>
</tr>
<tr>
<td><strong>Configuration Template</strong></td>
<td>EC2 타입, Auto Scaling 설정 등 환경 구성</td>
</tr>
<tr>
<td><strong>Platform</strong></td>
<td>실행 언어 및 런타임 (Python, Node.js 등)</td>
</tr>
</tbody></table>
<hr />
<h2 id="5️⃣-장점">5️⃣ 장점</h2>
<h3 id="🧑💻-개발-중심-환경">🧑‍💻 개발 중심 환경</h3>
<p>인프라 관리 부담 최소화 (DevOps 자동화)</p>
<h3 id="📦-aws-서비스와-통합">📦 AWS 서비스와 통합</h3>
<p>RDS, S3, CloudWatch, CodePipeline 등과 연동</p>
<h3 id="💰-비용-효율성">💰 비용 효율성</h3>
<p>사용하는 리소스(EC2, RDS 등)에 대해서만 과금</p>
<h3 id="♻️-유연성">♻️ 유연성</h3>
<p>EC2, VPC, 보안 그룹 등 하위 인프라 직접 수정 가능</p>
<hr />
<h2 id="6️⃣-현업-활용-사례">6️⃣ 현업 활용 사례</h2>
<h3 id="🌐-웹-애플리케이션-배포">🌐 웹 애플리케이션 배포</h3>
<p>Python Django, Node.js, Java Spring 앱을 Beanstalk으로 자동 배포</p>
<h3 id="🏢-스타트업-초기-서비스-구축">🏢 스타트업 초기 서비스 구축</h3>
<p>인프라 구성 없이 빠른 MVP 배포</p>
<h3 id="🧩-cicd-파이프라인-통합">🧩 CI/CD 파이프라인 통합</h3>
<p>CodePipeline + Beanstalk 연동으로 자동 배포 파이프라인 구현</p>
<h3 id="🧠-교육실습용-플랫폼">🧠 교육/실습용 플랫폼</h3>
<p>AWS 학습 및 테스트 환경으로 자주 활용</p>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<p>AWS Elastic Beanstalk = 자동화된 애플리케이션 배포 플랫폼 (PaaS)</p>
<p>자동으로 EC2, ALB, Auto Scaling, RDS 구성</p>
<p>언어/플랫폼 지원: Java, Node.js, Python, Go 등</p>
<p>현업에서는 웹 서비스 운영, 자동 배포 파이프라인, 스타트업 MVP 배포 등에 활용</p>
<p>👉 한마디로, “코드만 올리면 자동으로 인프라를 구성해주는 AWS의 배포 마법사” 입니다.</p>