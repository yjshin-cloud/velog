<h1 id="🛡️-amazon-guardduty-정리">🛡️ Amazon GuardDuty 정리</h1>
<hr />
<h2 id="1️⃣-amazon-guardduty란">1️⃣ Amazon GuardDuty란?</h2>
<p>Amazon GuardDuty는
AWS 계정과 워크로드에서 발생하는 보안 위협을 탐지하는 위협 탐지(Threat Detection) 서비스입니다.</p>
<p>👉 쉽게 말해,
“AWS 환경에서 수상한 행동을 자동으로 잡아내는 보안 감시 서비스” 입니다.</p>
<hr />
<h2 id="2️⃣-주요-기능">2️⃣ 주요 기능</h2>
<h3 id="🔍-이상-행동-탐지-anomaly-detection">🔍 이상 행동 탐지 (Anomaly Detection)</h3>
<p>비정상적인 API 호출, 의심스러운 IAM 활동, 예상치 못한 네트워크 트래픽 탐지</p>
<h3 id="📡-데이터-소스-분석">📡 데이터 소스 분석</h3>
<p>VPC Flow Logs, AWS CloudTrail, DNS Logs 분석</p>
<h3 id="🤖-ml-기반-분석">🤖 ML 기반 분석</h3>
<p>머신러닝과 위협 인텔리전스 피드 기반 탐지</p>
<h3 id="🔔-알림대응-자동화">🔔 알림/대응 자동화</h3>
<p>EventBridge, Security Hub, Lambda와 연동해 자동 대응</p>
<h2 id="3️⃣-아키텍처-시각화">3️⃣ 아키텍처 시각화</h2>
<pre><code class="language-mermaid">flowchart TD
    A[&quot;AWS Logs (CloudTrail, VPC Flow, DNS)&quot;] --&gt; B[&quot;Amazon GuardDuty&quot;]
    B --&gt; C[&quot;Threat Detection (ML + Threat Intelligence)&quot;]
    C --&gt; D[&quot;Findings (보안 탐지 결과)&quot;]
    D --&gt; E[&quot;Amazon EventBridge&quot;]
    E --&gt; F[&quot;자동 대응 (Lambda, SNS, Security Hub)&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/95abc07d-774b-4928-ac5e-e4199e802045/image.png" /></p>
<hr />
<h2 id="4️⃣-guardduty-탐지-예시">4️⃣ GuardDuty 탐지 예시</h2>
<h3 id="🔑-iam-root-계정으로-의심스러운-api-호출">🔑 IAM: Root 계정으로 의심스러운 API 호출</h3>
<h3 id="🌍-네트워크-비정상적인-ip-주소와의-통신-예-botnet-악성-서버">🌍 네트워크: 비정상적인 IP 주소와의 통신 (예: Botnet, 악성 서버)</h3>
<h3 id="📦-s3-s3-버킷에-비정상적인-접근-시도">📦 S3: S3 버킷에 비정상적인 접근 시도</h3>
<h3 id="🕵-계정-활동-짧은-시간-내-다수의-실패한-로그인-시도">🕵 계정 활동: 짧은 시간 내 다수의 실패한 로그인 시도</h3>
<hr />
<h2 id="5️⃣-현업-활용-사례">5️⃣ 현업 활용 사례</h2>
<h3 id="🏦-금융사-→-해외-ip에서-비정상-접근-감지-→-자동-차단">🏦 금융사 → 해외 IP에서 비정상 접근 감지 → 자동 차단</h3>
<h3 id="🛒-이커머스-→-의심스러운-api-호출-탐지-후-보안팀-알림">🛒 이커머스 → 의심스러운 API 호출 탐지 후 보안팀 알림</h3>
<h3 id="🏢-기업-내부-보안팀-→-guardduty-findings를-security-hub에-통합-관리">🏢 기업 내부 보안팀 → GuardDuty Findings를 Security Hub에 통합 관리</h3>
<h3 id="⚡-자동-대응-→-eventbridge--lambda-연계-이상-징후-발생-시-계정-차단알림">⚡ 자동 대응 → EventBridge + Lambda 연계, 이상 징후 발생 시 계정 차단/알림</h3>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<p>Amazon GuardDuty = AWS 위협 탐지 서비스</p>
<p>데이터 소스: CloudTrail, VPC Flow Logs, DNS Logs</p>
<p>활용: 이상행동 탐지, 보안 경보, 자동 대응</p>
<p>연동: EventBridge, Security Hub, Lambda, SNS</p>
<h3 id="👉-한마디로-aws-환경의-보안-경비원-입니다">👉 한마디로, “AWS 환경의 보안 경비원” 입니다.</h3>