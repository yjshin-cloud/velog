<h1 id="⚖️-aws-elastic-load-balancing-elb-완벽-가이드">⚖️ AWS Elastic Load Balancing (ELB) 완벽 가이드</h1>
<h2 id="1️⃣-elb란">1️⃣ ELB란?</h2>
<p>Elastic Load Balancing (ELB) 는
AWS에서 제공하는 트래픽 분산 서비스입니다.</p>
<p>👉 쉽게 말해,
“많은 손님이 한 가게로 몰렸을 때, 여러 점원에게 손님을 나눠주는 매니저” 같은 역할을 합니다.</p>
<p>사용자가 몰려도 서버가 버틸 수 있도록 요청을 분산</p>
<p>서버에 장애가 발생하면 정상 서버로만 트래픽 전달</p>
<p>EC2, 컨테이너(ECS/EKS), Lambda 등 다양한 서비스와 연동 가능</p>
<h2 id="2️⃣-elb의-종류">2️⃣ ELB의 종류</h2>
<p>🟢 1. ALB (Application Load Balancer)</p>
<p>OSI 7계층 (Application Layer)</p>
<p>HTTP, HTTPS, WebSocket 지원</p>
<p>URL 경로나 호스트 기반 라우팅 가능 (예: /api → API 서버, /img → 이미지 서버)</p>
<p>웹 애플리케이션에 최적화</p>
<p>🔵 2. NLB (Network Load Balancer)</p>
<p>OSI 4계층 (Transport Layer)</p>
<p>TCP, UDP, TLS 지원</p>
<p>고성능, 초저지연 네트워크 트래픽 처리 가능</p>
<p>수백만 요청/초 처리 가능 → 금융, 게임, 실시간 서비스에 적합</p>
<p>🟠 3. CLB (Classic Load Balancer) 구형</p>
<p>OSI 4 &amp; 7 계층 지원 (하이브리드)</p>
<p>이전 세대 로드밸런서 → 현재는 ALB/NLB 사용 권장</p>
<h2 id="3️⃣-elb-아키텍처-개념도">3️⃣ ELB 아키텍처 개념도</h2>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/062060bf-e040-491c-b936-acea0b9c4732/image.png" /></p>
<h2 id="4️⃣-elb의-장점">4️⃣ ELB의 장점</h2>
<p>📈 확장성 → 사용량이 늘어나도 자동으로 서버 분산</p>
<p>🛡️ 고가용성 → 일부 서버 다운돼도 서비스 지속 가능</p>
<p>🌍 글로벌 서비스 지원 → 여러 리전/가용 영역(AZ)에서 트래픽 분산</p>
<p>⚡ 보안 통합 → AWS WAF, ACM(SSL 인증서) 등과 연동</p>
<h2 id="5️⃣-실제-활용-사례">5️⃣ 실제 활용 사례</h2>
<p>🌐 웹 애플리케이션 → ALB로 /api, /static 경로 분리</p>
<p>🎮 게임 서버 → NLB로 TCP 기반 실시간 트래픽 분산</p>
<p>🏦 금융 거래 시스템 → NLB로 안정적인 네트워크 처리</p>
<p>🕰️ 레거시 애플리케이션 → CLB로 기존 시스템 운영</p>
<h2 id="✅-정리">✅ 정리</h2>
<p>AWS ELB는 트래픽을 자동으로 분산하여</p>
<p>서버 과부하 방지</p>
<p>고가용성 확보</p>
<p>보안 및 확장성 강화</p>
<p>👉 현재는 ALB (웹 애플리케이션), NLB (네트워크 고성능 트래픽) 를 주로 사용하고,
CLB는 점차 대체되는 추세입니다.</p>