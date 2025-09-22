<h1 id="🐳-aws-fargate-정리">🐳 AWS Fargate 정리</h1>
<hr />
<h2 id="1️⃣-aws-fargate란">1️⃣ AWS Fargate란?</h2>
<p>AWS Fargate는 컨테이너를 실행하기 위한 서버리스 컴퓨팅 엔진입니다.
사용자가 서버(EC2)를 직접 관리하지 않고도, ECS(Elastic Container Service) 또는 EKS(Elastic Kubernetes Service) 에서 컨테이너를 실행할 수 있게 해줍니다.</p>
<p>👉 쉽게 말해,
“도커 컨테이너를 실행하는데 서버 관리가 필요 없는 서비스” 입니다.</p>
<hr />
<h2 id="2️⃣-주요-특징">2️⃣ 주요 특징</h2>
<h3 id="🚀-서버리스container-전용">🚀 서버리스(Container 전용)</h3>
<p>인프라(EC2 클러스터) 관리 불필요</p>
<h3 id="📈-자동-확장">📈 자동 확장</h3>
<p>워크로드에 따라 컨테이너 리소스 자동 할당</p>
<h3 id="💰-비용-효율성">💰 비용 효율성</h3>
<p>CPU/메모리 사용량 기준으로 과금 (Pay-as-you-go)</p>
<h3 id="🛡️-보안-격리">🛡️ 보안 격리</h3>
<p>컨테이너 단위의 격리 환경 제공</p>
<h3 id="⚡-ecseks-통합">⚡ ECS/EKS 통합</h3>
<p>ECS 태스크 정의 또는 EKS 파드(Pod)로 실행</p>
<hr />
<h2 id="3️⃣-아키텍처-시각화">3️⃣ 아키텍처 시각화</h2>
<pre><code class="language-mermaid">flowchart TD
    A[&quot;개발자 (Docker Image Push)&quot;] --&gt; B[&quot;Amazon ECR (이미지 저장소)&quot;]
    B --&gt; C[&quot;ECS/EKS (오케스트레이션)&quot;]
    C --&gt; D[&quot;AWS Fargate (서버리스 컨테이너 실행)&quot;]
    D --&gt; E[&quot;컨테이너 애플리케이션 실행&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/a304d062-66f5-40bc-95fd-2fc9e69dd6b1/image.png" /></p>
<hr />
<h2 id="4️⃣-fargate-vs-ec2-기반-컨테이너">4️⃣ Fargate vs EC2 기반 컨테이너</h2>
<p>구분    EC2 기반    Fargate 기반
서버 관리    직접 관리 필요 (EC2 프로비저닝, 패치 등)    관리 불필요 (서버리스)
확장성    Auto Scaling 필요    자동 확장
과금 방식    EC2 인스턴스 단위    CPU/메모리 단위
보안    EC2 보안 패치 책임    AWS가 인프라 보안 관리</p>
<hr />
<h2 id="5️⃣-현업-활용-사례">5️⃣ 현업 활용 사례</h2>
<h3 id="🏢-마이크로서비스-아키텍처">🏢 마이크로서비스 아키텍처</h3>
<p>서비스별 컨테이너를 독립적으로 실행하고 확장</p>
<h3 id="📊-데이터-처리-파이프라인">📊 데이터 처리 파이프라인</h3>
<p>배치 잡, ETL 처리, 로그 수집</p>
<h3 id="🌐-웹-애플리케이션">🌐 웹 애플리케이션</h3>
<p>API 서버, 백엔드 컨테이너 실행</p>
<h3 id="🧪-개발테스트-환경">🧪 개발/테스트 환경</h3>
<p>빠르게 컨테이너 실행 후 종료 (테스트 자동화)</p>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<p>AWS Fargate = 서버리스 컨테이너 실행 엔진</p>
<p>ECS/EKS와 함께 사용 → EC2 관리 없이 컨테이너 실행 가능</p>
<p>장점: 자동 확장, 보안 강화, 비용 효율성</p>
<p>현업 활용: 마이크로서비스, 데이터 처리, 웹서비스, 테스트 환경</p>
<h3 id="👉-한마디로-컨테이너-전용-서버리스-컴퓨팅-서비스-입니다">👉 한마디로, “컨테이너 전용 서버리스 컴퓨팅 서비스” 입니다.</h3>