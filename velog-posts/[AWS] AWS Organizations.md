<h1 id="🌐-aws-organizations-정리">🌐 AWS Organizations 정리</h1>
<hr />
<h2 id="1️⃣-aws-organizations란">1️⃣ AWS Organizations란?</h2>
<p>AWS Organizations는 여러 AWS 계정을 중앙에서 관리할 수 있는 서비스예요.
조직 내의 모든 계정을 통합 관리하여 보안, 비용, 정책 적용을 손쉽게 할 수 있습니다.</p>
<p>👉 쉽게 말해, 회사에서 여러 부서/팀이 각각 AWS 계정을 쓰더라도, 본사는 한 곳에서 통제할 수 있게 해주는 서비스입니다.</p>
<hr />
<h2 id="2️⃣-주요-기능">2️⃣ 주요 기능</h2>
<ul>
<li>👥 멀티 계정 관리 → 여러 AWS 계정을 하나의 조직 단위로 묶어서 관리</li>
<li>🛡️ 서비스 제어 정책(SCP) → 특정 서비스·리전 사용 제한</li>
<li>💰 통합 청구(Consolidated Billing) → 모든 계정 비용을 한 번에 관리</li>
<li>🗂️ OU(Organizational Unit) → 계정을 그룹화해 정책을 계층적으로 적용</li>
<li>🔒 보안 강화 → 루트 계정 최소화 + IAM 결합으로 안전한 운영</li>
</ul>
<hr />
<h2 id="3️⃣-아키텍처-시각화">3️⃣ 아키텍처 시각화</h2>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/e37e2b11-9f0f-424f-a1cd-a39c9b595972/image.png" /></p>
<p>Management Account: 조직 전체를 관리하는 최상위 계정</p>
<p>OU (Organizational Unit): 부서/팀 단위 그룹</p>
<p>Member Accounts: 실제로 리소스를 운영하는 계정들</p>
<hr />
<p>4️⃣ 예시 정책 (SCP, Service Control Policy)</p>
<pre><code class="language-json">{
  &quot;Version&quot;: &quot;2012-10-17&quot;,
  &quot;Statement&quot;: [
    {
      &quot;Effect&quot;: &quot;Deny&quot;, 
      &quot;Action&quot;: &quot;ec2:RunInstances&quot;,   // EC2 인스턴스 생성 제한
      &quot;Resource&quot;: &quot;*&quot;,
      &quot;Condition&quot;: {
        &quot;StringNotEquals&quot;: {
          &quot;aws:RequestedRegion&quot;: &quot;ap-northeast-2&quot; // 서울 리전만 허용
        }
      }
    }
  ]
}</code></pre>
<p>*<em>### *</em>➡️ 위 정책은 서울 리전(ap-northeast-2) 외에서는 EC2 인스턴스를 생성할 수 없도록 차단합니다.</p>
<hr />
<h2 id="5️⃣-현업-활용-사례">5️⃣ 현업 활용 사례</h2>
<ul>
<li>🛡️ 보안팀 → 특정 리전만 사용하도록 강제 (예: GDPR 때문에 EU 리전만 허용)</li>
<li>💰 재무팀 → 모든 계정 비용을 통합 청구로 관리 + 부서별 비용 태깅</li>
<li>⚙️ 운영팀 → 신규 계정 생성 시 보안 설정, IAM Role, CloudTrail 자동 적용</li>
<li>🚀 Control Tower 연계 → 멀티 계정 환경에서 표준 보안·거버넌스 체계 구축</li>
</ul>
<hr />
<h2 id="6️⃣-정리">6️⃣ 정리</h2>
<h3 id="aws-organizations는-멀티-계정-환경에서-중앙-관리를-가능하게-해주는-핵심-서비스">AWS Organizations는 멀티 계정 환경에서 중앙 관리를 가능하게 해주는 핵심 서비스</h3>
<p>SCP를 통해 강력한 보안 통제 가능</p>
<p>통합 청구로 비용 최적화</p>
<h3 id="현업에서는-보안·비용·운영-효율성을-높이기-위해-반드시-사용됨">현업에서는 보안·비용·운영 효율성을 높이기 위해 반드시 사용됨</h3>
<hr />
<h2 id="✅-요약">✅ 요약</h2>
<p>AWS Organizations는 멀티 계정 환경에서 보안, 비용, 거버넌스를 한 번에 관리할 수 있는 핵심 서비스입니다.</p>
<ul>
<li>🔒 보안 강화 (SCP 정책)</li>
<li>💰 비용 최적화 (Consolidated Billing)</li>
<li>🛠️ 운영 효율성 (OU 구조로 계정 관리)<h3 id="👉-현업에서는-aws-control-tower와-함께-쓰여서-기업-단위-클라우드-운영의-표준이-됩니다">👉 현업에서는 AWS Control Tower와 함께 쓰여서 기업 단위 클라우드 운영의 표준이 됩니다.</h3>
</li>
</ul>