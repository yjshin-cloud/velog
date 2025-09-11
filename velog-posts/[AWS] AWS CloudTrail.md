<h1 id="📜-aws-cloudtrail-정리">📜 AWS CloudTrail 정리</h1>
<h2 id="1️⃣-aws-cloudtrail이란">1️⃣ AWS CloudTrail이란?</h2>
<p>AWS CloudTrail은
AWS 계정 내에서 발생하는 API 호출 이력(누가, 언제, 무엇을 했는지) 을 기록하고 추적하는 서비스입니다.</p>
<p>👉 쉽게 말해,
“AWS 계정의 CCTV” 역할을 하는 서비스입니다.</p>
<h2 id="2️⃣-주요-기능">2️⃣ 주요 기능</h2>
<h3 id="👤-사용자-활동-기록">👤 사용자 활동 기록</h3>
<p>IAM 사용자, Root 계정, 서비스가 어떤 작업을 했는지 기록</p>
<h3 id="🛡️-보안-감사security-audit">🛡️ 보안 감사(Security Audit)</h3>
<p>보안팀이 변경 이력을 추적해 이상 행위 탐지 가능</p>
<h3 id="🔄-문제-해결troubleshooting">🔄 문제 해결(Troubleshooting)</h3>
<p>서비스 중단/장애 원인 파악</p>
<h3 id="📂-로그-저장">📂 로그 저장</h3>
<p>S3 버킷에 이벤트 로그 저장</p>
<p>Athena/CloudWatch와 연동해 분석 가능</p>
<h2 id="3️⃣-아키텍처-시각화">3️⃣ 아키텍처 시각화</h2>
<pre><code class="language-mermaid">flowchart TD
    A[사용자/서비스] --&gt; B[API Call (AWS SDK, CLI, Console)]
    B --&gt; C[CloudTrail]
    C --&gt; D[S3 버킷 - 로그 저장]
    C --&gt; E[CloudWatch Logs - 모니터링/알람]
    C --&gt; F[Athena - 로그 분석]]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/c18991ef-c191-437c-a838-c11fd29fe616/image.png" /></p>
<h2 id="4️⃣-cloudtrail-이벤트-예시">4️⃣ CloudTrail 이벤트 예시</h2>
<pre><code>{
  &quot;eventVersion&quot;: &quot;1.08&quot;,
  &quot;userIdentity&quot;: {
    &quot;type&quot;: &quot;IAMUser&quot;,
    &quot;userName&quot;: &quot;admin&quot;
  },
  &quot;eventTime&quot;: &quot;2025-09-10T12:34:56Z&quot;,
  &quot;eventSource&quot;: &quot;ec2.amazonaws.com&quot;,
  &quot;eventName&quot;: &quot;StartInstances&quot;,
  &quot;awsRegion&quot;: &quot;ap-northeast-2&quot;,
  &quot;sourceIPAddress&quot;: &quot;192.168.1.1&quot;
}</code></pre><h2 id="📝-해석">📝 해석:</h2>
<p>admin 사용자가 서울 리전(ap-northeast-2)에서</p>
<p>EC2 인스턴스를 시작(StartInstances)</p>
<p>언제(2025-09-10) 어떤 IP에서 실행했는지 기록</p>
<h2 id="5️⃣-현업-활용-사례">5️⃣ 현업 활용 사례</h2>
<p>🛡️ 보안팀 → Root 계정 사용 여부 모니터링, S3 퍼블릭 변경 이벤트 감시</p>
<p>🏢 운영팀 → 장애 원인 분석 (누가 보안 그룹 규칙 변경했는지 확인)</p>
<p>💰 컴플라이언스 → PCI-DSS, HIPAA 같은 규제 감사 대응</p>
<p>🔍 포렌식 조사 → 계정 침해 사고 시 행동 추적</p>
<h2 id="✅-정리">✅ 정리</h2>
<p>CloudTrail = AWS 계정의 모든 활동 기록 서비스</p>
<p>기록 대상: API 호출 (Console, CLI, SDK, 서비스 간 호출)</p>
<p>로그 저장: S3, CloudWatch, Athena</p>
<p>주요 활용: 보안 감사, 장애 분석, 규제 준수, 포렌식 조사</p>
<p>👉 한마디로, “누가 AWS에서 무엇을 했는지” 반드시 알려주는 서비스입니다.</p>