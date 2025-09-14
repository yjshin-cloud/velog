<h1 id="🔔-aws-sns-simple-notification-service-정리">🔔 AWS SNS (Simple Notification Service) 정리</h1>
<hr />
<h2 id="1️⃣-aws-sns란">1️⃣ AWS SNS란?</h2>
<p>Amazon SNS는 Pub/Sub 메시징 서비스로,
애플리케이션이나 시스템에서 발생한 이벤트를 다수의 구독자(Subscriber)에게 동시에 알림을 전송할 수 있는 서비스입니다.</p>
<p>👉 쉽게 말해,
“하나의 알림을 여러 사람/시스템에 자동으로 퍼뜨려주는 방송국” 역할을 합니다.</p>
<hr />
<h2 id="2️⃣-주요-개념">2️⃣ 주요 개념</h2>
<p>주제(Topic)</p>
<p>메시지를 발행(Publish)할 수 있는 채널</p>
<p>발행자(Publisher)</p>
<p>이벤트/메시지를 Topic에 발행하는 주체 (예: 애플리케이션, Lambda 등)</p>
<p>구독자(Subscriber)</p>
<p>Topic에 연결된 엔드포인트 (예: Email, SMS, SQS, Lambda 등)</p>
<p>프로토콜(Protocol)</p>
<p>메시지 전달 방식 (HTTP/S, Email, SMS, Lambda, SQS 등)</p>
<hr />
<h2 id="3️⃣-아키텍처-시각화">3️⃣ 아키텍처 시각화</h2>
<p>flowchart TD
    A[&quot;Publisher (EC2, Lambda, App)&quot;] --&gt; B[&quot;SNS Topic&quot;]
    B --&gt; C[&quot;Email Subscriber&quot;]
    B --&gt; D[&quot;SMS Subscriber&quot;]
    B --&gt; E[&quot;SQS Queue&quot;]
    B --&gt; F[&quot;Lambda Function&quot;]</p>
<hr />
<h2 id="4️⃣-특징">4️⃣ 특징</h2>
<p>📡 푸시 기반 전달 → 실시간 알림</p>
<p>📩 다양한 프로토콜 지원 (Email, SMS, HTTP/S, SQS, Lambda 등)</p>
<p>📈 확장성 → 수많은 구독자에게 동시에 메시지 전송</p>
<p>💸 비용 효율적 → 전송량에 따라 과금 (소량은 무료 제공)</p>
<p>🛡️ 보안 → IAM 정책, KMS 암호화, VPC 엔드포인트 지원</p>
<hr />
<h2 id="5️⃣-현업-활용-사례">5️⃣ 현업 활용 사례</h2>
<p>🛎️ 알림 시스템</p>
<p>EC2 서버 CPU 80% 초과 시 CloudWatch Alarm → SNS 통해 Slack/Email 알림</p>
<p>📦 이커머스 주문 처리</p>
<p>주문 발생 시 SNS Topic → SQS(배송 시스템), Lambda(결제 처리), Email(고객 알림) 동시 전송</p>
<p>🚨 보안 이벤트 경보</p>
<p>IAM Root 계정 로그인 발생 시 → SNS 통해 보안팀에 SMS 즉시 알림</p>
<p>🤖 서버리스 이벤트 트리거</p>
<p>Lambda와 연결해 특정 이벤트 발생 시 자동 처리</p>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<p>AWS SNS = Pub/Sub 알림 서비스</p>
<p>구성요소: Publisher → Topic → Subscriber</p>
<p>다양한 프로토콜로 실시간 알림 가능 (Email, SMS, HTTP, Lambda, SQS 등)</p>
<p>현업에서는 모니터링 알림, 주문 처리, 보안 경보, 서버리스 이벤트 트리거 등에 활용</p>
<p>👉 한마디로, “AWS의 방송국 알림 서비스” 라고 이해하면 쉽습니다.</p>