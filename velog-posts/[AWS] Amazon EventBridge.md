<h1 id="🔔-amazon-eventbridge-정리">🔔 Amazon EventBridge 정리</h1>
<hr />
<h2 id="1️⃣-amazon-eventbridge란">1️⃣ Amazon EventBridge란?</h2>
<p>Amazon EventBridge는
애플리케이션, AWS 서비스, SaaS 애플리케이션에서 발생하는 이벤트를 수집하고 라우팅하는 서버리스 이벤트 버스(Event Bus) 서비스입니다.</p>
<p>👉 쉽게 말해,
“AWS의 이벤트 중심 알림·자동화 중계 시스템” 이라고 할 수 있습니다.</p>
<hr />
<h2 id="2️⃣-주요-기능">2️⃣ 주요 기능</h2>
<h3 id="📡-이벤트-소스event-source">📡 이벤트 소스(Event Source)</h3>
<p>AWS 서비스 (S3, EC2, DynamoDB 등)</p>
<p>사용자 정의 애플리케이션</p>
<p>SaaS 애플리케이션 (Zendesk, Datadog, Auth0 등)</p>
<h3 id="🎯-이벤트-버스event-bus">🎯 이벤트 버스(Event Bus)</h3>
<p>이벤트를 받아서 규칙(Rule)에 따라 대상(Target)으로 라우팅</p>
<h3 id="🛠️-이벤트-타겟event-target">🛠️ 이벤트 타겟(Event Target)</h3>
<p>Lambda, SQS, SNS, Step Functions, Kinesis 등 다양한 서비스</p>
<h3 id="🔎-규칙rule">🔎 규칙(Rule)</h3>
<p>특정 조건(패턴 매칭)에 맞는 이벤트만 타겟으로 전달</p>
<hr />
<h2 id="3️⃣-아키텍처-시각화">3️⃣ 아키텍처 시각화</h2>
<pre><code class="language-mermaid">flowchart TD
    A[&quot;Event Source (S3, EC2, SaaS App)&quot;] --&gt; B[&quot;EventBridge (Event Bus)&quot;]
    B --&gt;|Rule 1| C[&quot;Lambda Function&quot;]
    B --&gt;|Rule 2| D[&quot;SQS Queue&quot;]
    B --&gt;|Rule 3| E[&quot;SNS Topic&quot;]
    B --&gt;|Rule 4| F[&quot;Step Functions&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/b97ec170-7e36-4e56-a47a-b913b62e2ffa/image.png" /></p>
<hr />
<h2 id="4️⃣-특징">4️⃣ 특징</h2>
<p>서버리스 기반 → 인프라 관리 불필요</p>
<p>다양한 AWS 서비스 및 외부 SaaS와 통합</p>
<p>실시간 이벤트 기반 아키텍처 구현 가능</p>
<p>이벤트 패턴 매칭으로 세밀한 필터링 가능</p>
<p>확장성과 내구성 보장</p>
<hr />
<h2 id="5️⃣-현업-활용-사례">5️⃣ 현업 활용 사례</h2>
<h3 id="🛡-보안-모니터링">🛡 보안 모니터링</h3>
<p>CloudTrail 이벤트 → EventBridge → Lambda → Slack 알림 전송</p>
<h3 id="📦-이커머스-주문-처리">📦 이커머스 주문 처리</h3>
<p>주문 생성 이벤트 → SQS → 결제/배송 시스템 처리</p>
<h3 id="📊-데이터-파이프라인-자동화">📊 데이터 파이프라인 자동화</h3>
<p>S3에 파일 업로드 이벤트 → EventBridge → Lambda → ETL 처리</p>
<h3 id="🕹-마이크로서비스-연동">🕹 마이크로서비스 연동</h3>
<p>여러 서비스 간 이벤트를 EventBridge로 연결해 느슨한 결합(Decoupling) 구현</p>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<p>Amazon EventBridge = 이벤트 라우팅 서비스</p>
<p>구성 요소: Event Source → Event Bus → Rules → Targets</p>
<p>활용: 자동화, 마이크로서비스 통합, 보안 경보, 데이터 처리 파이프라인</p>
<p>한마디로, “AWS의 이벤트 허브(Event Hub)”</p>