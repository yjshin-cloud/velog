<h1 id="☸️-aws-eks-elastic-kubernetes-service-정리">☸️ AWS EKS (Elastic Kubernetes Service) 정리</h1>
<hr />
<h2 id="1️⃣-aws-eks란">1️⃣ AWS EKS란?</h2>
<p>Amazon EKS (Elastic Kubernetes Service) 는
AWS에서 제공하는 완전관리형 쿠버네티스(Kubernetes) 서비스입니다.</p>
<p>👉 쉽게 말해,
“쿠버네티스를 직접 설치·운영하지 않고, AWS가 대신 관리해주는 서비스” 입니다.</p>
<hr />
<h2 id="2️⃣-주요-특징">2️⃣ 주요 특징</h2>
<p>🚀 완전 관리형</p>
<p>Kubernetes Control Plane(마스터 노드)을 AWS가 운영 → 사용자는 워커 노드와 애플리케이션만 관리</p>
<hr />
<h2 id="🔄-유연한-실행">🔄 유연한 실행</h2>
<p>EC2 인스턴스 위에서 실행 가능</p>
<p>AWS Fargate 위에서 서버리스 실행 가능</p>
<h3 id="🔒-보안--iam-통합">🔒 보안 &amp; IAM 통합</h3>
<p>IAM, VPC, Security Group과 통합</p>
<h3 id="🌐-멀티-클러스터멀티-리전-지원">🌐 멀티 클러스터/멀티 리전 지원</h3>
<p>대규모 글로벌 애플리케이션 운영 가능</p>
<h3 id="⚡-네이티브-쿠버네티스-호환성">⚡ 네이티브 쿠버네티스 호환성</h3>
<p>Helm Chart, kubectl, CRD 등 표준 쿠버네티스 도구 그대로 사용</p>
<hr />
<h2 id="3️⃣-eks-아키텍처-시각화">3️⃣ EKS 아키텍처 시각화</h2>
<pre><code class="language-mermaid">flowchart TD
    A[&quot;개발자 (kubectl, Helm)&quot;] --&gt; B[&quot;Amazon EKS Control Plane (AWS 관리)&quot;]
    B --&gt; C[&quot;Worker Nodes (EC2)&quot;]
    B --&gt; D[&quot;Fargate (Serverless Pods)&quot;]
    C --&gt; E[&quot;컨테이너 애플리케이션&quot;]
    D --&gt; E
    E --&gt; F[&quot;사용자 요청 처리 (via ALB/NLB)&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/fd8f624e-5583-4cf9-93a6-afb3783439e4/image.png" /></p>
<hr />
<h2 id="4️⃣-ecs-vs-eks-비교">4️⃣ ECS vs EKS 비교</h2>
<hr />
<table>
<thead>
<tr>
<th>구분</th>
<th><strong>ECS</strong></th>
<th><strong>EKS</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>컨테이너 오케스트레이션</strong></td>
<td>AWS 독자 서비스</td>
<td>오픈소스 Kubernetes 기반</td>
</tr>
<tr>
<td><strong>학습 곡선</strong></td>
<td>쉬움 (AWS 전용)</td>
<td>다소 높음 (쿠버네티스 지식 필요)</td>
</tr>
<tr>
<td><strong>커뮤니티/생태계</strong></td>
<td>제한적 (AWS 중심)</td>
<td>넓음 (Kubernetes 표준 활용)</td>
</tr>
<tr>
<td><strong>실행 방식</strong></td>
<td>EC2, Fargate</td>
<td>EC2, Fargate</td>
</tr>
<tr>
<td><strong>운영 부담</strong></td>
<td>상대적으로 적음</td>
<td>쿠버네티스 아키텍처 학습 필요</td>
</tr>
</tbody></table>
<hr />
<h2 id="5️⃣-현업-활용-사례">5️⃣ 현업 활용 사례</h2>
<h3 id="🏢-엔터프라이즈-환경">🏢 엔터프라이즈 환경</h3>
<p>멀티 클라우드/온프레미스 + AWS 환경 통합 운영</p>
<h3 id="🧩-마이크로서비스-아키텍처">🧩 마이크로서비스 아키텍처</h3>
<p>대규모 서비스들을 Kubernetes로 통합 관리</p>
<h3 id="📊-데이터ai-플랫폼">📊 데이터/AI 플랫폼</h3>
<p>Kubeflow, Spark on Kubernetes 같은 워크로드 실행</p>
<h3 id="🌍-글로벌-서비스">🌍 글로벌 서비스</h3>
<p>여러 리전에 걸쳐 동일한 쿠버네티스 환경 배포</p>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<p>EKS = AWS 관리형 Kubernetes 서비스</p>
<p>장점: 보안/IAM 통합, Fargate 지원, 표준 K8s 호환성</p>
<p>ECS와 달리 Kubernetes 표준 생태계 활용 가능</p>
<p>현업에서는 마이크로서비스, 데이터/AI 플랫폼, 멀티클라우드 운영에 많이 사용</p>
<p>👉 한마디로, “AWS에서 쿠버네티스를 쉽게 쓰도록 만든 서비스” 입니다.</p>