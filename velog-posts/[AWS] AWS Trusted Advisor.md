<h1 id="🌟-aws-trusted-advisor-정리">🌟 AWS Trusted Advisor 정리</h1>
<h2 id="📌-aws-trusted-advisor란">📌 AWS Trusted Advisor란?</h2>
<p>AWS Trusted Advisor는 클라우드 환경을 점검해 주는 온라인 도우미 서비스입니다.
비용 절감, 성능 최적화, 보안 강화, 내결함성 확보, 서비스 제한 확인 등의 <strong>모범 사례(Best Practices)</strong>를 기반으로 리소스를 분석하고 개선 방안을 제안해 줍니다.</p>
<p>즉, AWS 계정과 리소스 상태를 진단해주는 헬스체크 서비스라고 이해하면 됩니다. 🩺</p>
<h2 id="✅-주요-점검-항목-5가지-카테고리">✅ 주요 점검 항목 (5가지 카테고리)</h2>
<h3 id="💰-비용-최적화-cost-optimization">💰 비용 최적화 (Cost Optimization)</h3>
<p>사용하지 않는 EC2 인스턴스</p>
<p>미사용 Elastic IP</p>
<p>낮은 활용도의 RDS 인스턴스
→ 비용을 줄일 수 있는 리소스 추천</p>
<h3 id="⚡-성능-performance">⚡ 성능 (Performance)</h3>
<p>서비스 지연이나 병목을 줄이기 위한 권장사항</p>
<p>Auto Scaling 그룹, 로드 밸런서 설정 검토</p>
<h3 id="🔒-보안-security">🔒 보안 (Security)</h3>
<p>S3 버킷 퍼블릭 접근 여부</p>
<p>IAM Root 계정 MFA 적용 여부</p>
<p>보안 그룹의 과도한 접근 허용 규칙 확인</p>
<h3 id="🛠️-내결함성-fault-tolerance">🛠️ 내결함성 (Fault Tolerance)</h3>
<p>백업 및 복구 설정 검토</p>
<p>여러 AZ에 걸쳐 있는지 확인</p>
<p>Elastic Load Balancer 설정 점검</p>
<h3 id="📊-서비스-제한-service-limits">📊 서비스 제한 (Service Limits)</h3>
<p>EC2 인스턴스, EIP, VPC, RDS 등 서비스별 한도(Quota) 초과 여부 알림</p>
<h2 id="🎨-시각화-mermaid-다이어그램">🎨 시각화 (Mermaid 다이어그램)</h2>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/229b6a63-0665-4c74-abfd-75a55e6c16fe/image.png" /></p>
<h2 id="💼-현업-활용-사례">💼 현업 활용 사례</h2>
<p>비용 관리팀: 미사용 리소스를 찾아 클라우드 비용 절감</p>
<p>보안팀: IAM, S3, 보안 그룹 등을 보안 모범사례에 맞게 관리</p>
<p>운영팀/인프라팀: Auto Scaling, 멀티 AZ 배포 여부 등을 확인해 가용성 강화</p>
<p>클라우드 거버넌스: 서비스 한도 초과로 인한 장애 방지</p>
<p>특히 Enterprise Support를 사용하면 더 많은 세부 항목의 Trusted Advisor 점검을 받을 수 있습니다.</p>
<h2 id="📖-정리">📖 정리</h2>
<p>AWS Trusted Advisor = 클라우드 환경 헬스체크 도구</p>
<p>5대 카테고리: 💰 비용, ⚡ 성능, 🔒 보안, 🛠️ 내결함성, 📊 서비스 제한</p>
<p>현업에서는 비용 절감·보안 강화·가용성 확보 목적으로 가장 많이 활용</p>