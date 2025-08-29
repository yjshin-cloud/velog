<h1 id="📊-aws-cloudwatch-정리">📊 AWS CloudWatch 정리</h1>
<hr />
<h2 id="1️⃣-aws-cloudwatch란">1️⃣ AWS CloudWatch란?</h2>
<p>Amazon CloudWatch 는
AWS 리소스(EC2, RDS, Lambda 등)와 애플리케이션을 모니터링 및 로깅할 수 있는 서비스입니다.</p>
<h3 id="👉-쉽게-말해-aws-서비스들의-건강-상태를-실시간으로-지켜보고-문제가-생기면-알려주는-감시자-입니다"><strong>👉 쉽게 말해, “AWS 서비스들의 건강 상태를 실시간으로 지켜보고, 문제가 생기면 알려주는 감시자” 입니다.</strong></h3>
<hr />
<h2 id="2️⃣-cloudwatch의-주요-기능">2️⃣ CloudWatch의 주요 기능</h2>
<h3 id="📈-메트릭metrics">📈 메트릭(Metrics)</h3>
<p>CPU, 메모리, 네트워크, 디스크 사용량 등 지표 수집</p>
<h3 id="📋-로그log-수집-및-관리">📋 로그(Log) 수집 및 관리</h3>
<p>애플리케이션 로그, 시스템 로그를 중앙에서 관리</p>
<h3 id="🔔-알람alarms">🔔 알람(Alarms)</h3>
<p>특정 조건 발생 시 알림 (예: CPU &gt; 80% → Slack/Email로 알람)</p>
<h3 id="📊-대시보드dashboards">📊 대시보드(Dashboards)</h3>
<p>지표와 로그를 시각적으로 모니터링</p>
<h3 id="⚡-이벤트events">⚡ 이벤트(Events)</h3>
<p>AWS 리소스에서 발생하는 이벤트를 감지하고 자동으로 대응 (예: Auto Scaling 트리거)</p>
<hr />
<h2 id="3️⃣-cloudwatch-아키텍처-개념도">3️⃣ CloudWatch 아키텍처 개념도</h2>
<img align="left" src="https://velog.velcdn.com/images/yjshin/post/f5c3f3c7-e24b-49ef-9c86-6c464962aec0/image.png" width="400" />

<hr />
<h2 id="4️⃣-cloudwatch-사용-예시">4️⃣ CloudWatch 사용 예시</h2>
<p>EC2 CPU 사용률이 80% 초과 시 알람 전송</p>
<p>RDS 스토리지가 가득 차기 전 경고 발생</p>
<p>Lambda 함수 오류율이 일정 기준 이상일 때 Slack/이메일 알림</p>
<p>S3 버킷 접근 로그를 중앙 집중형 분석</p>
<p>Auto Scaling과 연동 → 트래픽 급증 시 서버 자동 확장</p>
<hr />
<h2 id="5️⃣-현업에서의-활용">5️⃣ 현업에서의 활용</h2>
<p>현업에서는 CloudWatch를 다음과 같이 적극적으로 활용합니다.</p>
<h3 id="🛠-운영-모니터링">🛠 운영 모니터링</h3>
<p>서버 상태, DB 성능, API 응답 시간 등을 실시간 모니터링</p>
<h3 id="🔔-알림-자동화">🔔 알림 자동화</h3>
<p>CloudWatch Alarms + SNS → 장애 발생 시 Slack, Teams, PagerDuty로 알림 전송</p>
<h3 id="⚡-자동-대응">⚡ 자동 대응</h3>
<p>CloudWatch Events → 특정 조건 충족 시 Lambda 실행</p>
<p>예) CPU 90% 이상 → Auto Scaling Group에 새 EC2 추가</p>
<h3 id="📑-비용-관리">📑 비용 관리</h3>
<p>사용량/비용 관련 메트릭 추적 → AWS Budgets와 함께 활용</p>
<h3 id="🧑💻-devops--sre-필수-도구">🧑‍💻 DevOps / SRE 필수 도구</h3>
<p>CI/CD 파이프라인 로그 수집</p>
<p>보안 모니터링(AWS GuardDuty, Config와 함께)</p>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<blockquote>
<p><strong>AWS CloudWatch</strong>는
<strong>모니터링 (Metrics &amp; Logs), 알림 (Alarms &amp; SNS), 자동화 (Events &amp; Lambda 연동)</strong>
등을 통해 <strong>운영 안정성과 가용성</strong>을 높여주는 핵심 서비스입니다.</p>
</blockquote>
<h3 id="👉-한마디로-aws의-cctv--알람-시스템-이라고-이해하면-가장-쉽습니다">👉 한마디로, “AWS의 CCTV + 알람 시스템” 이라고 이해하면 가장 쉽습니다.</h3>