<h1 id="☁️-aws-caf-cloud-adoption-framework-정리">☁️ AWS CAF (Cloud Adoption Framework) 정리</h1>
<hr />
<h2 id="1️⃣-aws-caf란">1️⃣ AWS CAF란?</h2>
<p>AWS Cloud Adoption Framework (CAF) 는
기업이 클라우드 도입(Cloud Adoption) 을 체계적으로 수행할 수 있도록 돕는 전략적 프레임워크입니다.</p>
<p>👉 쉽게 말해,
“기업이 클라우드로 전환할 때 무엇을, 어떻게 준비해야 하는지 알려주는 로드맵” 이라고 할 수 있습니다.</p>
<hr />
<h2 id="2️⃣-aws-caf의-목적">2️⃣ AWS CAF의 목적</h2>
<p>AWS CAF는 다음을 목표로 합니다:</p>
<h3 id="🚀-클라우드-전환-가속화">🚀 클라우드 전환 가속화</h3>
<h3 id="🧭-조직의-it-전략과-비즈니스-목표-정렬">🧭 조직의 IT 전략과 비즈니스 목표 정렬</h3>
<h3 id="🧱-리스크-최소화-및-거버넌스-강화">🧱 리스크 최소화 및 거버넌스 강화</h3>
<h3 id="🔄-조직-전체의-클라우드-역량-향상">🔄 조직 전체의 클라우드 역량 향상</h3>
<hr />
<h2 id="3️⃣-aws-caf의-6가지-관점-perspectives">3️⃣ AWS CAF의 6가지 관점 (Perspectives)</h2>
<hr />
<table>
<thead>
<tr>
<th>관점</th>
<th>주요 초점</th>
<th>담당 부서/역할</th>
</tr>
</thead>
<tbody><tr>
<td><strong>Business (비즈니스)</strong></td>
<td>클라우드가 비즈니스 목표 달성에 어떻게 기여하는가</td>
<td>경영진, 전략팀</td>
</tr>
<tr>
<td><strong>People (인재)</strong></td>
<td>클라우드 운영에 필요한 인력과 기술 역량</td>
<td>HR, 교육팀</td>
</tr>
<tr>
<td><strong>Governance (거버넌스)</strong></td>
<td>위험 관리, 규제 준수, 재무 관리</td>
<td>보안팀, 감사팀</td>
</tr>
<tr>
<td><strong>Platform (플랫폼)</strong></td>
<td>클라우드 인프라 설계 및 운영</td>
<td>IT 인프라팀</td>
</tr>
<tr>
<td><strong>Security (보안)</strong></td>
<td>데이터 보호, 접근 제어, 규정 준수</td>
<td>보안팀, IAM 담당자</td>
</tr>
<tr>
<td><strong>Operations (운영)</strong></td>
<td>서비스 모니터링, 자동화, 지속 개선</td>
<td>DevOps, 운영팀</td>
</tr>
</tbody></table>
<hr />
<h2 id="4️⃣-aws-caf-시각화-다이어그램">4️⃣ AWS CAF 시각화 다이어그램</h2>
<pre><code class="language-mermaid">graph TD
    A[&quot;🏢 AWS Cloud Adoption Framework (CAF)&quot;]
    A --&gt; B[&quot;💼 Business Perspective\n(비즈니스)&quot;]
    A --&gt; C[&quot;👥 People Perspective\n(인재)&quot;]
    A --&gt; D[&quot;⚖️ Governance Perspective\n(거버넌스)&quot;]
    A --&gt; E[&quot;🧱 Platform Perspective\n(플랫폼)&quot;]
    A --&gt; F[&quot;🔒 Security Perspective\n(보안)&quot;]
    A --&gt; G[&quot;⚙️ Operations Perspective\n(운영)&quot;]</code></pre>
<h3 id="💡-구성요소-설명">💡 구성요소 설명</h3>
<hr />
<table>
<thead>
<tr>
<th>관점</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>💼 <strong>Business (비즈니스)</strong></td>
<td>비즈니스 목표, ROI, 가치 실현 전략 수립</td>
</tr>
<tr>
<td>👥 <strong>People (인재)</strong></td>
<td>조직 구조, 역할, 클라우드 역량 강화</td>
</tr>
<tr>
<td>⚖️ <strong>Governance (거버넌스)</strong></td>
<td>정책, 규정, 비용 및 위험 관리 체계 수립</td>
</tr>
<tr>
<td>🧱 <strong>Platform (플랫폼)</strong></td>
<td>클라우드 인프라 설계 및 배포 전략</td>
</tr>
<tr>
<td>🔒 <strong>Security (보안)</strong></td>
<td>보안 정책, IAM, 데이터 보호 및 규정 준수</td>
</tr>
<tr>
<td>⚙️ <strong>Operations (운영)</strong></td>
<td>운영 모니터링, 변경 관리, 자동화 프로세스</td>
</tr>
</tbody></table>
<img alt="image" height="396" src="https://github.com/user-attachments/assets/4828474b-4079-4483-b6d7-46411c75dfbc" width="3316" />


<hr />
<h2 id="5️⃣-각-관점별-주요-질문-예시">5️⃣ 각 관점별 주요 질문 예시</h2>
<hr />
<table>
<thead>
<tr>
<th>관점</th>
<th>핵심 질문</th>
</tr>
</thead>
<tbody><tr>
<td>Business</td>
<td>클라우드 도입이 수익, 비용 절감, 고객 만족도에 어떤 영향을 주는가?</td>
</tr>
<tr>
<td>People</td>
<td>우리 조직의 클라우드 기술 역량은 충분한가? 필요한 교육은 무엇인가?</td>
</tr>
<tr>
<td>Governance</td>
<td>예산, 정책, 위험 관리를 어떻게 표준화할 수 있을까?</td>
</tr>
<tr>
<td>Platform</td>
<td>어떤 인프라 구조로 클라우드를 설계할까? (VPC, EC2, S3 등)</td>
</tr>
<tr>
<td>Security</td>
<td>데이터 보호 및 접근 제어를 어떻게 강화할까?</td>
</tr>
<tr>
<td>Operations</td>
<td>운영 효율화, 자동화, 모니터링 시스템은 어떻게 구축할까?</td>
</tr>
</tbody></table>
<hr />
<h2 id="6️⃣-현업-적용-예시">6️⃣ 현업 적용 예시</h2>
<hr />
<table>
<thead>
<tr>
<th>시나리오</th>
<th>적용 방식</th>
</tr>
</thead>
<tbody><tr>
<td>🏢 <strong>공공기관 클라우드 전환</strong></td>
<td>Governance와 Security 관점 중심으로 보안 정책 정립</td>
</tr>
<tr>
<td>🧑‍💻 <strong>스타트업 인프라 구축</strong></td>
<td>Platform, Operations 중심으로 빠른 배포 자동화</td>
</tr>
<tr>
<td>💰 <strong>금융사 클라우드 도입</strong></td>
<td>Governance + Security + Business 균형 중심으로 운영</td>
</tr>
</tbody></table>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<p>AWS CAF = 클라우드 도입을 위한 체계적 로드맵</p>
<p>6가지 관점: Business, People, Governance, Platform, Security, Operations</p>
<p>목표: 비즈니스 정렬 + 위험 최소화 + 클라우드 전환 가속화</p>
<p>현업에서는 전략 수립, 보안 강화, 인프라 설계, 운영 자동화 등에 활용</p>
<p>👉 한마디로,
“AWS CAF는 기업의 클라우드 여정을 성공으로 이끄는 나침반이다.”</p>