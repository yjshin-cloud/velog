<h1 id="☎️-amazon-connect-정리">☎️ Amazon Connect 정리</h1>
<hr />
<h2 id="1️⃣-amazon-connect란">1️⃣ Amazon Connect란?</h2>
<p>Amazon Connect는
AWS에서 제공하는 클라우드 기반 컨택센터(Contact Center) 서비스입니다.</p>
<p>👉 쉽게 말해,
“콜센터를 AWS 클라우드에서 바로 구축·운영할 수 있는 서비스” 입니다.</p>
<p>전화 시스템(IVR), 채팅, 고객 상담 이력 관리, AI 챗봇 등
기존 온프레미스 콜센터 인프라 없이 웹 브라우저만으로 구축 가능합니다.</p>
<hr />
<h2 id="2️⃣-주요-특징">2️⃣ 주요 특징</h2>
<table>
<thead>
<tr>
<th>기능</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>☁️ <strong>클라우드 기반 콜센터</strong></td>
<td>서버 설치 없이 웹 환경에서 바로 컨택센터 개설</td>
</tr>
<tr>
<td>📞 <strong>다중 채널 지원</strong></td>
<td>음성 통화, 실시간 채팅, 이메일, 메시징 통합 지원</td>
</tr>
<tr>
<td>🧠 <strong>AI 통합 (Lex, Polly, Comprehend)</strong></td>
<td>음성 인식, 챗봇, 감정 분석 기능 내장</td>
</tr>
<tr>
<td>🔄 <strong>자동 라우팅 (Routing)</strong></td>
<td>고객 문의 유형에 따라 상담원 자동 연결</td>
</tr>
<tr>
<td>🔍 <strong>실시간 모니터링 &amp; 분석</strong></td>
<td>상담 통계, 대기 시간, 고객 만족도 분석</td>
</tr>
<tr>
<td>💰 <strong>사용량 기반 요금제 (Pay-as-you-go)</strong></td>
<td>사용한 통화 시간/상담 세션만큼만 과금</td>
</tr>
<tr>
<td>🔒 <strong>보안 및 통합 관리</strong></td>
<td>IAM, KMS, CloudWatch, CloudTrail 완전 연동</td>
</tr>
</tbody></table>
<hr />
<h2 id="3️⃣-아키텍처-시각화">3️⃣ 아키텍처 시각화</h2>
<pre><code class="language-mermaid">flowchart TD
    A[&quot;📞 고객 (전화/채팅)&quot;] --&gt; B[&quot;Amazon Connect (Contact Center)&quot;]
    B --&gt; C[&quot;👩‍💼 상담원 (Agent / Web Interface)&quot;]
    B --&gt; D[&quot;🤖 Amazon Lex (AI 챗봇)&quot;]
    B --&gt; E[&quot;🧠 Amazon Comprehend (감정/의도 분석)&quot;]
    B --&gt; F[&quot;🗂️ Amazon S3 (통화 녹음 / 로그 저장)&quot;]
    B --&gt; G[&quot;📊 Amazon QuickSight (리포트 시각화)&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/5b0d5d1c-8675-478e-a4f6-16b327942d2f/image.png" /></p>
<p>🧠 설명:</p>
<p>고객이 전화 또는 웹 채팅을 시작하면 Amazon Connect가 요청을 수신</p>
<p>IVR(음성 응답) 또는 AI 챗봇(Lex)으로 초기 응대</p>
<p>적절한 상담원에게 자동 연결 (Routing Profile 기반)</p>
<p>대화 내용은 S3에 녹음/저장되고, 분석은 Comprehend와 QuickSight로 시각화</p>
<hr />
<h2 id="4️⃣-주요-구성-요소">4️⃣ 주요 구성 요소</h2>
<table>
<thead>
<tr>
<th>구성 요소</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td><strong>Contact Flow</strong></td>
<td>고객 응대 흐름(IVR) 설계 도구 (드래그 앤 드롭 방식)</td>
</tr>
<tr>
<td><strong>Routing Profile</strong></td>
<td>고객 유형·우선순위에 따른 상담원 연결 정책</td>
</tr>
<tr>
<td><strong>Queue</strong></td>
<td>고객 대기열 관리 및 대기 시간 제어</td>
</tr>
<tr>
<td><strong>Agent Workspace</strong></td>
<td>상담원이 사용하는 웹 인터페이스 (콜 수신/채팅/고객정보 조회)</td>
</tr>
<tr>
<td><strong>Contact Lens</strong></td>
<td>통화 녹취 분석 서비스 (음성 → 텍스트 변환, 감정 분석)</td>
</tr>
<tr>
<td><strong>Integration</strong></td>
<td>S3, Lambda, DynamoDB, QuickSight 등과 연동 가능</td>
</tr>
</tbody></table>
<hr />
<h2 id="5️⃣-amazon-connect-contact-flow">5️⃣ Amazon Connect Contact Flow</h2>
<pre><code class="language-mermaid">graph TD
    A[&quot;📞 고객 전화&quot;] --&gt; B[&quot;Welcome 메시지 재생&quot;]
    B --&gt; C{&quot;고객 입력 (1~3번) 선택&quot;}
    C --&gt;|1번| D[&quot;청구 관련 상담원 연결&quot;]
    C --&gt;|2번| E[&quot;기술 지원 상담원 연결&quot;]
    C --&gt;|3번| F[&quot;음성 인식 챗봇 (Amazon Lex)&quot;]
    F --&gt; G[&quot;필요 시 상담원 전환&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/3c900fe9-9923-40cb-b250-e02f5d7d14d6/image.png" /></p>
<p>🧠 설명:</p>
<p>Amazon Connect에서는 Flow Builder로
콜센터 흐름(음성 안내, 메뉴 선택, 상담 연결)을 GUI 방식으로 설계할 수 있습니다.</p>
<hr />
<h2 id="6️⃣-ai-서비스-통합">6️⃣ AI 서비스 통합</h2>
<table>
<thead>
<tr>
<th>서비스</th>
<th>역할</th>
</tr>
</thead>
<tbody><tr>
<td>🤖 <strong>Amazon Lex</strong></td>
<td>자연어 처리 기반 챗봇, 고객의 질문 자동 이해</td>
</tr>
<tr>
<td>🧠 <strong>Amazon Comprehend</strong></td>
<td>대화 중 감정 분석 및 의도 파악</td>
</tr>
<tr>
<td>🔊 <strong>Amazon Polly</strong></td>
<td>자연스러운 음성 안내 (TTS: Text-to-Speech)</td>
</tr>
<tr>
<td>🔍 <strong>Contact Lens</strong></td>
<td>통화 내용 텍스트 변환 + 감정 분석 + 키워드 추출</td>
</tr>
</tbody></table>
<hr />
<h2 id="7️⃣-현업-활용-사례">7️⃣ 현업 활용 사례</h2>
<table>
<thead>
<tr>
<th>산업</th>
<th>활용 예시</th>
</tr>
</thead>
<tbody><tr>
<td>🏦 <strong>금융기관</strong></td>
<td>IVR + AI 챗봇을 통한 대출 문의 자동 응답</td>
</tr>
<tr>
<td>🏥 <strong>의료기관</strong></td>
<td>병원 예약 시스템 자동화 및 상담원 연결</td>
</tr>
<tr>
<td>🏢 <strong>기업 고객센터</strong></td>
<td>클라우드 기반 상담센터 구축 (재택 상담 가능)</td>
</tr>
<tr>
<td>🧠 <strong>교육 기관</strong></td>
<td>등록 문의 및 챗봇 상담 기능 구축</td>
</tr>
<tr>
<td>🛒 <strong>이커머스</strong></td>
<td>주문/배송 문의 자동화, 불만 접수 자동 분류</td>
</tr>
</tbody></table>
<hr />
<h2 id="8️⃣-통합-분석-및-리포팅">8️⃣ 통합 분석 및 리포팅</h2>
<pre><code class="language-mermaid">flowchart TD
    A[&quot;Amazon Connect 통화 로그&quot;] --&gt; B[&quot;Amazon S3 저장&quot;]
    B --&gt; C[&quot;AWS Lambda (전처리)&quot;]
    C --&gt; D[&quot;Amazon Comprehend (감정 분석)&quot;]
    D --&gt; E[&quot;Amazon QuickSight (리포트 대시보드)&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/fb83191f-d2d9-46d0-a28f-d978c836b309/image.png" /></p>
<h3 id="📊-활용-예시">📊 활용 예시:</h3>
<p>고객의 감정(긍정/부정/중립) 분석</p>
<p>상담원별 평균 통화 시간, 대기 시간 리포트</p>
<p>AI 기반 만족도 예측</p>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<p>Amazon Connect = 클라우드 기반 컨택센터 서비스</p>
<h3 id="주요-특징">주요 특징:</h3>
<p>음성/채팅 통합, AI 챗봇, 감정 분석, 자동 라우팅</p>
<h3 id="완전관리형">완전관리형:</h3>
<p>서버·PBX·CTI 시스템 불필요, 웹 기반 운영</p>
<h3 id="연동-서비스">연동 서비스:</h3>
<p>Lex (챗봇), Polly (음성), Comprehend (분석), QuickSight (리포트)</p>
<h3 id="현업-활용">현업 활용:</h3>
<p>고객 상담 자동화, 콜센터 운영 효율화, 고객 경험 개선</p>
<p>👉 한마디로,
“Amazon Connect는 AI와 음성 분석을 결합한 클라우드 콜센터 솔루션” 입니다.</p>