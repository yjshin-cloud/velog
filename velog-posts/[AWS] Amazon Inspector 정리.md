<h1 id="🕵️♂️-amazon-inspector-정리">🕵️‍♂️ Amazon Inspector 정리</h1>
<hr />
<h2 id="1️⃣-amazon-inspector란">1️⃣ Amazon Inspector란?</h2>
<p>Amazon Inspector는 AWS 환경에서 실행 중인 리소스(EC2, ECR, Lambda 등)에 대해
보안 취약점을 자동으로 분석·평가(Vulnerability Assessment) 해주는 서비스입니다.</p>
<h3 id="👉-쉽게-말해-aws-리소스의-보안-헬스체크-자동-진단기-입니다">👉 쉽게 말해, “AWS 리소스의 보안 헬스체크 자동 진단기” 입니다.</h3>
<hr />
<h2 id="2️⃣-주요-기능">2️⃣ 주요 기능</h2>
<p>🔍 취약점 스캔 (Vulnerability Scanning)</p>
<p>EC2 인스턴스, 컨테이너 이미지(ECR), Lambda 함수의 보안 취약점 자동 감지</p>
<p>🧠 지속적 모니터링 (Continuous Scan)</p>
<p>리소스가 변경되면 자동 재스캔 (실시간 감시)</p>
<p>🛡️ CVE 기반 평가</p>
<p>CVE(공통 취약점 데이터베이스)와 비교해 위험도 평가</p>
<p>📊 심각도 기반 리포트 제공</p>
<p>Critical / High / Medium / Low 등으로 결과 분류</p>
<p>🔔 자동 알림 및 대응</p>
<p>Amazon EventBridge, Security Hub, SNS 등과 연동해 알림 또는 자동 조치 가능</p>
<hr />
<h2 id="3️⃣-아키텍처-시각화">3️⃣ 아키텍처 시각화</h2>
<pre><code class="language-mermaid">flowchart TD
    A[&quot;AWS 리소스 (EC2 / ECR / Lambda)&quot;] --&gt; B[&quot;Amazon Inspector&quot;]
    B --&gt; C[&quot;CVE Database (취약점 정보 매칭)&quot;]
    B --&gt; D[&quot;Findings (취약점 보고서)&quot;]
    D --&gt; E[&quot;Amazon EventBridge&quot;]
    E --&gt; F[&quot;자동 대응 (Lambda, SNS, Security Hub)&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/a2c20bc5-e9d8-49f8-b41f-fe85e535078e/image.png" /></p>
<hr />
<h2 id="4️⃣-분석-대상별-주요-점검-항목">4️⃣ 분석 대상별 주요 점검 항목</h2>
<hr />
<table>
<thead>
<tr>
<th>대상</th>
<th>점검 항목</th>
<th>예시</th>
</tr>
</thead>
<tbody><tr>
<td><strong>EC2 인스턴스</strong></td>
<td>OS 취약점, 잘못된 패키지 버전</td>
<td>OpenSSL, Apache 취약점</td>
</tr>
<tr>
<td><strong>ECR 컨테이너 이미지</strong></td>
<td>라이브러리 취약점, CVE 비교</td>
<td>Log4j, glibc 취약점</td>
</tr>
<tr>
<td><strong>Lambda 함수</strong></td>
<td>패키지 종속성 취약점</td>
<td>Python/Pip 모듈 버전 점검</td>
</tr>
</tbody></table>
<hr />
<h2 id="5️⃣-현업-활용-사례">5️⃣ 현업 활용 사례</h2>
<h3 id="🏢-보안팀--devsecops">🏢 보안팀 / DevSecOps</h3>
<p>신규 EC2, 컨테이너 배포 시 자동 취약점 점검 파이프라인 구성</p>
<h3 id="🚀-cicd-파이프라인-통합">🚀 CI/CD 파이프라인 통합</h3>
<p>CodePipeline → ECR → Inspector → 배포 전 자동 검증</p>
<h3 id="🧩-보안-규제-대응">🧩 보안 규제 대응</h3>
<p>PCI-DSS, ISO 27001 등 컴플라이언스 감사 시 보안 증적 확보</p>
<h3 id="🧠-보안-자동화">🧠 보안 자동화</h3>
<p>EventBridge + Lambda 연동 → Critical 취약점 발견 시 자동 알림 및 격리</p>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<p>Amazon Inspector = AWS 리소스 보안 취약점 자동 분석 서비스</p>
<p>대상: EC2, ECR, Lambda</p>
<p>기능: CVE 기반 취약점 스캔, 지속 모니터링, 자동 알림/대응</p>
<p>현업 활용: DevSecOps 파이프라인, 보안 감사, 자동 보안 대응</p>
<h3 id="👉-한마디로-aws-보안팀의-자동화된-취약점-탐지-도우미-입니다">👉 한마디로, “AWS 보안팀의 자동화된 취약점 탐지 도우미” 입니다.</h3>