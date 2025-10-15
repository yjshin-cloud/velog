<h1 id="🌐-amazon-route-53-정리">🌐 Amazon Route 53 정리</h1>
<hr />
<h2 id="1️⃣-amazon-route-53이란">1️⃣ Amazon Route 53이란?</h2>
<p>Amazon Route 53은 AWS에서 제공하는 DNS(도메인 네임 시스템) 관리 서비스입니다.
도메인 이름(예: <a href="http://www.example.com)%EC%9D%84">www.example.com)을</a> IP 주소(예: 192.168.0.1)로 변환해주는 역할을 합니다.</p>
<p>👉 쉽게 말해,
“사람이 기억하기 쉬운 도메인 주소를 컴퓨터가 이해할 수 있는 IP로 바꿔주는 AWS의 전화번호부 서비스” 입니다.</p>
<h2 id="2️⃣-주요-기능">2️⃣ 주요 기능</h2>
<hr />
<table>
<thead>
<tr>
<th>기능</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>🌍 <strong>도메인 등록 (Domain Registration)</strong></td>
<td>AWS 콘솔에서 직접 도메인을 구입/등록 가능</td>
</tr>
<tr>
<td>🔁 <strong>DNS 라우팅 (DNS Routing)</strong></td>
<td>사용자의 요청을 가장 적절한 서버나 리전으로 전달</td>
</tr>
<tr>
<td>🧭 <strong>헬스체크 (Health Check)</strong></td>
<td>서버 상태를 모니터링하고, 비정상 서버로의 트래픽 자동 우회</td>
</tr>
<tr>
<td>🌎 <strong>트래픽 정책 관리 (Traffic Policy)</strong></td>
<td>지리적 위치, 지연 시간, 가중치 기반의 트래픽 분배 가능</td>
</tr>
<tr>
<td>🧱 <strong>통합성 (Integration)</strong></td>
<td>ALB, S3, CloudFront, API Gateway 등과 통합 사용 가능</td>
</tr>
</tbody></table>
<hr />
<h2 id="3️⃣-route-53-아키텍처-시각화">3️⃣ Route 53 아키텍처 시각화</h2>
<hr />
<pre><code class="language-mermaid">flowchart TD
    A[&quot;👩‍💻 사용자 (www.example.com)&quot;] --&gt; B[&quot;Amazon Route 53 (DNS Resolver)&quot;]
    B --&gt;|도메인 조회| C[&quot;Public Hosted Zone&quot;]
    C --&gt; D[&quot;Application Load Balancer&quot;]
    D --&gt; E[&quot;ECS / EC2 / S3 등 Backend 서비스&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/251159ed-5564-4664-9044-70f471dfadf5/image.png" /></p>
<h2 id="4️⃣-라우팅-정책-유형">4️⃣ 라우팅 정책 유형</h2>
<hr />
<table>
<thead>
<tr>
<th>라우팅 정책</th>
<th>설명</th>
<th>예시</th>
</tr>
</thead>
<tbody><tr>
<td><strong>단순(Simple)</strong></td>
<td>한 도메인 → 한 IP 매핑</td>
<td>example.com → 1.1.1.1</td>
</tr>
<tr>
<td><strong>가중치(Weighted)</strong></td>
<td>여러 서버에 비율로 트래픽 분배</td>
<td>A서버 70%, B서버 30%</td>
</tr>
<tr>
<td><strong>지연 시간(Latency)</strong></td>
<td>사용자의 지리적 위치 기준으로 가장 빠른 리전에 연결</td>
<td>서울 사용자 → ap-northeast-2</td>
</tr>
<tr>
<td><strong>장애 조치(Failover)</strong></td>
<td>1차 서버 다운 시 2차 서버로 자동 전환</td>
<td>Active-Passive 구성</td>
</tr>
<tr>
<td><strong>지리적(Geolocation)</strong></td>
<td>사용자의 지역별로 다른 리전으로 연결</td>
<td>일본 → 도쿄 리전, 한국 → 서울 리전</td>
</tr>
<tr>
<td><strong>멀티 밸류 응답(Multi-Value Answer)</strong></td>
<td>여러 IP 반환, 헬스체크 기반 자동 장애조치</td>
<td>다중 서버 운영</td>
</tr>
</tbody></table>
<h2 id="5️⃣-헬스체크health-check">5️⃣ 헬스체크(Health Check)</h2>
<p>HTTP/HTTPS/TCP 기반으로 주기적으로 서버 상태 확인</p>
<p>응답 실패 시 비정상 서버로의 트래픽 차단</p>
<p>CloudWatch와 연동하여 장애 알림 자동화 가능</p>
<h2 id="6️⃣-현업-활용-사례">6️⃣ 현업 활용 사례</h2>
<h3 id="🌐-글로벌-서비스-도메인-운영">🌐 글로벌 서비스 도메인 운영</h3>
<p>Route 53 + CloudFront 조합으로 전 세계 사용자에게 빠른 DNS 응답 제공</p>
<h3 id="🏢-멀티-리전-구성-active-passive">🏢 멀티 리전 구성 (Active-Passive)</h3>
<p>서울 리전 장애 시 도쿄 리전으로 자동 전환</p>
<h3 id="📦-s3-정적-웹사이트-호스팅">📦 S3 정적 웹사이트 호스팅</h3>
<p>Route 53에서 S3 버킷을 웹사이트 엔드포인트로 연결</p>
<h3 id="📊-모니터링-자동화">📊 모니터링 자동화</h3>
<p>헬스체크 + CloudWatch로 서버 상태 자동 감시</p>
<h2 id="✅-정리">✅ 정리</h2>
<p>Amazon Route 53 = AWS의 DNS 관리 서비스</p>
<p>주요 기능: 도메인 등록, DNS 라우팅, 헬스체크, 트래픽 분배</p>
<p>라우팅 정책: 단순 / 가중치 / 지연 시간 / 장애 조치 / 지리적 / 멀티밸류</p>
<p>현업 활용: 글로벌 서비스 트래픽 분산, 멀티 리전 장애조치, 도메인 관리</p>
<p>👉 한마디로,
“Route 53은 사용자의 요청을 가장 빠르고 안전한 경로로 안내하는 AWS의 인터넷 내비게이터” 입니다.</p>