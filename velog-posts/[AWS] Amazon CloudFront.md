<h1 id="🌍-amazon-cloudfront-정리">🌍 Amazon CloudFront 정리</h1>
<hr />
<h2 id="1️⃣-amazon-cloudfront란">1️⃣ Amazon CloudFront란?</h2>
<p>Amazon CloudFront는
AWS에서 제공하는 글로벌 콘텐츠 전송 네트워크(CDN, Content Delivery Network) 서비스입니다.</p>
<p>👉 쉽게 말해,
“전 세계 사용자에게 웹사이트·영상·이미지를 빠르고 안전하게 전달하는 서비스” 입니다.</p>
<p>CloudFront는 AWS의 전 세계 엣지 로케이션(Edge Location) 에 콘텐츠를 캐싱하여
사용자와 가장 가까운 지점에서 데이터를 전송하므로, 지연 시간(latency) 을 최소화하고 성능을 극대화합니다.</p>
<h2 id="2️⃣-주요-특징">2️⃣ 주요 특징</h2>
<table>
<thead>
<tr>
<th>특징</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>⚡ <strong>저지연 전송 (Low Latency)</strong></td>
<td>사용자와 가까운 엣지 서버에서 콘텐츠 제공</td>
</tr>
<tr>
<td>🧱 <strong>글로벌 네트워크</strong></td>
<td>100개국 이상, 수백 개의 Edge Location 운영</td>
</tr>
<tr>
<td>🔒 <strong>보안 강화</strong></td>
<td>AWS WAF, Shield, ACM과 연동 (DDoS·SSL 보호)</td>
</tr>
<tr>
<td>💾 <strong>캐싱 (Caching)</strong></td>
<td>정적/동적 콘텐츠를 엣지 서버에 저장해 성능 향상</td>
</tr>
<tr>
<td>📦 <strong>통합 관리</strong></td>
<td>S3, EC2, ALB, API Gateway 등과 직접 통합 가능</td>
</tr>
<tr>
<td>💰 <strong>비용 효율성</strong></td>
<td>사용량 기반 과금 (전송량·요청 수 기준)</td>
</tr>
</tbody></table>
<h2 id="3️⃣-cloudfront-아키텍처-시각화">3️⃣ CloudFront 아키텍처 시각화</h2>
<pre><code class="language-mermaid">flowchart TD
    A[&quot;👩‍💻 사용자 (Web/App)&quot;] --&gt; B[&quot;🌍 CloudFront Edge Location (캐시 서버)&quot;]
    B --&gt;|Cache Hit| A
    B --&gt;|Cache Miss| C[&quot;S3 / EC2 / ALB / API Gateway (Origin Server)&quot;]
    C --&gt; B
    B --&gt; D[&quot;📊 CloudWatch (모니터링)&quot;]
    B --&gt; E[&quot;🧱 AWS WAF / Shield (보안 방어)&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/983e9e4a-bb42-440a-aed2-0f60781e5fd1/image.png" /></p>
<p>🧠 설명:</p>
<p>Cache Hit: 엣지 서버에 캐싱된 데이터 즉시 전달 (빠름)</p>
<p>Cache Miss: 원본 서버(Origin)에서 가져와 캐시에 저장 후 전달</p>
<p>AWS 보안 서비스와 통합되어 성능 + 보안 + 가용성 동시 확보</p>
<h2 id="4️⃣-주요-구성-요소">4️⃣ 주요 구성 요소</h2>
<table>
<thead>
<tr>
<th>구성 요소</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td><strong>Origin (오리진)</strong></td>
<td>원본 콘텐츠가 저장된 서버 (S3, EC2, ALB 등)</td>
</tr>
<tr>
<td><strong>Edge Location</strong></td>
<td>사용자 근처에 위치한 CloudFront 캐시 서버</td>
</tr>
<tr>
<td><strong>Distribution</strong></td>
<td>CloudFront 설정 단위 (배포 구성을 정의)</td>
</tr>
<tr>
<td><strong>Behavior</strong></td>
<td>어떤 요청을 어떤 오리진으로 라우팅할지 규칙 설정</td>
</tr>
<tr>
<td><strong>OAC (Origin Access Control)</strong></td>
<td>S3 접근을 CloudFront만 허용하도록 제어</td>
</tr>
<tr>
<td><strong>TTL (Time to Live)</strong></td>
<td>캐싱된 콘텐츠의 만료 시간</td>
</tr>
</tbody></table>
<h2 id="5️⃣-cloudfront-동작-과정">5️⃣ CloudFront 동작 과정</h2>
<pre><code class="language-mermaid">sequenceDiagram
    participant User as 👤 사용자
    participant Edge as 🌍 CloudFront Edge
    participant Origin as 🗂️ S3 / EC2 (Origin)

    User-&gt;&gt;Edge: 콘텐츠 요청
    Edge--&gt;&gt;User: 캐시 존재 시 즉시 응답 (Cache Hit)
    Edge-&gt;&gt;Origin: 캐시 없음 → 원본에서 요청 (Cache Miss)
    Origin--&gt;&gt;Edge: 콘텐츠 반환 및 캐싱
    Edge--&gt;&gt;User: 최종 응답 전송</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/cc7347e3-f752-4c6b-b275-c73d1c5e44da/image.png" /></p>
<h2 id="6️⃣-주요-통합-서비스">6️⃣ 주요 통합 서비스</h2>
<table>
<thead>
<tr>
<th>서비스</th>
<th>역할</th>
</tr>
</thead>
<tbody><tr>
<td><strong>S3</strong></td>
<td>정적 웹사이트 호스팅 및 콘텐츠 원본 저장소</td>
</tr>
<tr>
<td><strong>ALB / EC2</strong></td>
<td>동적 콘텐츠 전달용 백엔드 서버</td>
</tr>
<tr>
<td><strong>AWS WAF</strong></td>
<td>웹 공격 차단 (SQL Injection, XSS 등)</td>
</tr>
<tr>
<td><strong>AWS Shield</strong></td>
<td>DDoS 공격 방어</td>
</tr>
<tr>
<td><strong>ACM (AWS Certificate Manager)</strong></td>
<td>SSL/TLS 인증서 자동 관리</td>
</tr>
<tr>
<td><strong>Lambda@Edge</strong></td>
<td>엣지 서버에서 사용자 요청/응답 실시간 처리 (Header 조작, 리디렉션 등)</td>
</tr>
</tbody></table>
<h2 id="7️⃣-cloudfront-캐싱-전략-요약">7️⃣ CloudFront 캐싱 전략 요약</h2>
<table>
<thead>
<tr>
<th>전략</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td><strong>TTL (Cache-Control)</strong></td>
<td>콘텐츠 만료 시간 설정</td>
</tr>
<tr>
<td><strong>Cache Invalidation</strong></td>
<td>캐시 삭제 요청 (업데이트 시)</td>
</tr>
<tr>
<td><strong>Versioned URL</strong></td>
<td>파일 버전 관리 (<code>style_v2.css</code>)로 캐시 무효화 최소화</td>
</tr>
<tr>
<td><strong>Compression &amp; GZIP</strong></td>
<td>전송량 감소 및 응답속도 향상</td>
</tr>
</tbody></table>
<h2 id="8️⃣-현업-활용-사례">8️⃣ 현업 활용 사례</h2>
<table>
<thead>
<tr>
<th>산업</th>
<th>활용 예시</th>
</tr>
</thead>
<tbody><tr>
<td>🛒 <strong>이커머스</strong></td>
<td>정적 이미지·CSS·JS 캐싱 → 웹사이트 로딩 속도 개선</td>
</tr>
<tr>
<td>🎥 <strong>미디어 스트리밍</strong></td>
<td>HLS/DASH 기반 동영상 콘텐츠 전송</td>
</tr>
<tr>
<td>🏢 <strong>기업 포털 / SaaS</strong></td>
<td>글로벌 사용자에게 빠른 응답 제공</td>
</tr>
<tr>
<td>🧠 <strong>AI/데이터 분석 서비스</strong></td>
<td>Lambda@Edge로 사용자별 맞춤 데이터 처리</td>
</tr>
<tr>
<td>🏦 <strong>금융 / 공공기관</strong></td>
<td>WAF·Shield와 통합하여 안전한 대외 서비스 운영</td>
</tr>
</tbody></table>
<h2 id="9️⃣-s3--cloudfront-정적-웹사이트-배포">9️⃣ S3 + CloudFront 정적 웹사이트 배포</h2>
<pre><code class="language-mermaid">flowchart TD
    A[&quot;👩‍💻 사용자&quot;] --&gt; B[&quot;🌍 CloudFront Distribution&quot;]
    B --&gt; C[&quot;🪣 S3 Bucket (Static Website)&quot;]
    B --&gt; D[&quot;🧱 AWS WAF (보안 정책)&quot;]
    B --&gt; E[&quot;🔒 ACM (SSL 인증서)&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/f5c9073e-0c26-464b-b7bd-933a86f986ba/image.png" /></p>
<p>🧱 설명:</p>
<p>S3에 정적 웹사이트 파일 업로드</p>
<p>CloudFront로 전 세계 배포</p>
<p>HTTPS 인증서(ACM) + WAF로 보안 강화</p>
<h2 id="✅-정리">✅ 정리</h2>
<h3 id="amazon-cloudfront--글로벌-콘텐츠-전송-네트워크-cdn">Amazon CloudFront = 글로벌 콘텐츠 전송 네트워크 (CDN)</h3>
<h3 id="주요-역할-콘텐츠-캐싱-트래픽-가속-보안-강화">주요 역할: 콘텐츠 캐싱, 트래픽 가속, 보안 강화</h3>
<h3 id="통합-서비스-s3-alb-api-gateway-waf-shield-lambdaedge">통합 서비스: S3, ALB, API Gateway, WAF, Shield, Lambda@Edge</h3>
<h3 id="현업-활용-정적-웹사이트-스트리밍-글로벌-saas-보안-강화형-배포">현업 활용: 정적 웹사이트, 스트리밍, 글로벌 SaaS, 보안 강화형 배포</h3>
<p>👉 한마디로,
“CloudFront는 전 세계 사용자에게 빠르고 안전하게 콘텐츠를 배포하는 AWS의 글로벌 CDN 서비스” 입니다.</p>