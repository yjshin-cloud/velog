<h1 id="❄️-aws-snow-family-정리">❄️ AWS Snow Family 정리</h1>
<hr />
<h2 id="1️⃣-aws-snow-family란">1️⃣ AWS Snow Family란?</h2>
<p>AWS Snow Family는
네트워크 대역폭이 부족하거나 오프라인 환경에서도 대용량 데이터를 안전하게 이동할 수 있도록 돕는
물리적 데이터 전송 장치(Edge Device) 시리즈입니다.</p>
<p>👉 쉽게 말해,
“데이터를 인터넷으로 옮길 수 없을 때, AWS가 직접 하드웨어 장비를 보내주는 서비스” 입니다.</p>
<hr />
<h2 id="2️⃣-aws-snow-family의-구성">2️⃣ AWS Snow Family의 구성</h2>
<hr />
<table>
<thead>
<tr>
<th>서비스</th>
<th>설명</th>
<th>용도</th>
</tr>
</thead>
<tbody><tr>
<td><strong>AWS Snowcone</strong></td>
<td>가장 작고 가벼운 장치 (8TB 스토리지, Edge 컴퓨팅 가능)</td>
<td>소규모 데이터 수집, 엣지 디바이스용</td>
</tr>
<tr>
<td><strong>AWS Snowball Edge</strong></td>
<td>중간 크기 (80TB~210TB), 컴퓨팅 기능 포함</td>
<td>대규모 데이터 마이그레이션, 현장 분석</td>
</tr>
<tr>
<td><strong>AWS Snowmobile</strong></td>
<td>초대형 트럭형 스토리지 (100PB까지)</td>
<td>데이터센터 전체 이전(엑사바이트급)</td>
</tr>
</tbody></table>
<hr />
<h2 id="3️⃣-시각적-구성도">3️⃣ 시각적 구성도</h2>
<pre><code class="language-mermaid">flowchart TD
    A[&quot;On-Premise / Factory / IoT Environment&quot;] --&gt; B[&quot;AWS Snowcone (8TB)&quot;]
    A --&gt; C[&quot;AWS Snowball Edge (100TB+)&quot;]
    A --&gt; D[&quot;AWS Snowmobile (100PB Truck)&quot;]

    B --&gt; E[&quot;Data Transfer to AWS Cloud&quot;]
    C --&gt; E
    D --&gt; E
    E --&gt; F[&quot;Amazon S3 / Glacier / EBS 등 저장&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/b1ea0db9-bad7-4c09-8c38-c14450272c42/image.png" /></p>
<hr />
<h2 id="4️⃣-주요-기능">4️⃣ 주요 기능</h2>
<h3 id="🚛-물리적-데이터-마이그레이션">🚛 물리적 데이터 마이그레이션</h3>
<p>AWS가 실제 장치를 고객에게 배송 → 데이터 적재 후 반납 → AWS가 업로드</p>
<h3 id="🧠-edge-컴퓨팅-지원">🧠 Edge 컴퓨팅 지원</h3>
<p>인터넷이 끊긴 환경에서도 Lambda, EC2 인스턴스 로컬 실행 가능</p>
<h3 id="🔐-보안-강화">🔐 보안 강화</h3>
<p>데이터 암호화(AES-256) + KMS 통합 + 하드웨어 보안 모듈 내장</p>
<h3 id="⚙️-내구성과-견고함">⚙️ 내구성과 견고함</h3>
<p>충격, 먼지, 온도 변화 등 극한 환경에서도 사용 가능</p>
<hr />
<h2 id="5️⃣-서비스별-비교">5️⃣ 서비스별 비교</h2>
<hr />
<table>
<thead>
<tr>
<th>항목</th>
<th><strong>Snowcone</strong></th>
<th><strong>Snowball Edge</strong></th>
<th><strong>Snowmobile</strong></th>
</tr>
</thead>
<tbody><tr>
<td>용량</td>
<td>8TB</td>
<td>80TB ~ 210TB</td>
<td>100PB (트럭 단위)</td>
</tr>
<tr>
<td>크기</td>
<td>초소형 (2kg 이하)</td>
<td>휴대용 박스형</td>
<td>트레일러 트럭</td>
</tr>
<tr>
<td>네트워크 연결</td>
<td>Wi-Fi / 이더넷</td>
<td>10Gbps / 40Gbps</td>
<td>전용 연결</td>
</tr>
<tr>
<td>엣지 컴퓨팅</td>
<td>가능 (EC2 / Lambda 지원)</td>
<td>가능</td>
<td>불가능</td>
</tr>
<tr>
<td>사용 시나리오</td>
<td>IoT, 소규모 오프라인 환경</td>
<td>대규모 현장 데이터 처리</td>
<td>데이터센터 전체 이전</td>
</tr>
</tbody></table>
<hr />
<h2 id="6️⃣-현업-활용-사례">6️⃣ 현업 활용 사례</h2>
<h3 id="🏭-스마트-팩토리-공장-자동화">🏭 스마트 팩토리 (공장 자동화)</h3>
<p>Snowcone으로 현장 IoT 센서 데이터를 수집 후 AWS로 업로드</p>
<h3 id="🎥-미디어-산업">🎥 미디어 산업</h3>
<p>고용량 영상 데이터를 Snowball Edge에 저장 → S3 업로드</p>
<h3 id="🏢-기업-데이터센터-이전">🏢 기업 데이터센터 이전</h3>
<p>수백 PB 규모의 데이터 → Snowmobile 트럭으로 물리적 전송</p>
<h3 id="🌍-원격지-분석-환경-군사-광산-해양-등">🌍 원격지 분석 환경 (군사, 광산, 해양 등)</h3>
<p>인터넷이 없는 환경에서 Edge 컴퓨팅 + 로컬 분석 수행</p>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<p>AWS Snow Family = 물리 장비를 통한 데이터 전송 및 엣지 컴퓨팅 서비스</p>
<p>구성 제품: Snowcone, Snowball Edge, Snowmobile</p>
<p>활용 목적:</p>
<h3 id="💾-대규모-데이터-이관">💾 대규모 데이터 이관</h3>
<h3 id="⚙️-오프라인-환경에서의-분석처리">⚙️ 오프라인 환경에서의 분석/처리</h3>
<h3 id="🔒-안전한-물리적-데이터-마이그레이션">🔒 안전한 물리적 데이터 마이그레이션</h3>
<h3 id="👉-한마디로-aws가-직접-하드웨어를-보내서-데이터를-클라우드로-옮겨주는-서비스-입니다">👉 한마디로, “AWS가 직접 하드웨어를 보내서 데이터를 클라우드로 옮겨주는 서비스” 입니다.</h3>