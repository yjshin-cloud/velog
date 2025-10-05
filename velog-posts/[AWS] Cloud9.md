<h1 id="💻-aws-cloud9-정리">💻 AWS Cloud9 정리</h1>
<hr />
<h2 id="1️⃣-aws-cloud9이란">1️⃣ AWS Cloud9이란?</h2>
<p>AWS Cloud9은
브라우저 기반의 클라우드 통합 개발 환경(IDE, Integrated Development Environment) 입니다.</p>
<p>👉 쉽게 말해,
“AWS에서 제공하는 웹 기반 코딩 환경 — 내 컴퓨터에 아무것도 설치하지 않고, 브라우저만으로 개발 가능한 도구” 입니다.</p>
<hr />
<h2 id="2️⃣-주요-특징">2️⃣ 주요 특징</h2>
<h3 id="☁️-클라우드-기반-개발-환경">☁️ 클라우드 기반 개발 환경</h3>
<p>로컬 환경 설정 없이, AWS 클라우드에서 바로 코딩 가능</p>
<h3 id="🧑💻-언어-지원">🧑‍💻 언어 지원</h3>
<p>Python, Node.js, Java, Go, C++, PHP 등 다양한 언어 지원</p>
<h3 id="🧰-통합-터미널-제공">🧰 통합 터미널 제공</h3>
<p>리눅스 쉘 + AWS CLI + Git 내장</p>
<h3 id="🪄-실시간-협업collaboration">🪄 실시간 협업(Collaboration)</h3>
<p>여러 개발자가 동시에 같은 코드 편집 가능</p>
<h3 id="🔗-aws-서비스-통합">🔗 AWS 서비스 통합</h3>
<p>EC2, Lambda, S3 등과 바로 연결 가능</p>
<hr />
<h2 id="3️⃣-아키텍처-시각화">3️⃣ 아키텍처 시각화</h2>
<hr />
<pre><code class="language-mermaid">flowchart TD
    A[&quot;개발자 (웹 브라우저)&quot;] --&gt; B[&quot;AWS Cloud9 IDE&quot;]
    B --&gt; C[&quot;Amazon EC2 Instance (개발 환경 실행)&quot;]
    B --&gt; D[&quot;AWS Lambda / S3 / DynamoDB (연동)&quot;]
    C --&gt; E[&quot;GitHub / CodeCommit (소스코드 관리)&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/b1c67756-c856-4e6a-9756-bdab38b6a9a2/image.png" /></p>
<hr />
<h2 id="4️⃣-장점">4️⃣ 장점</h2>
<h3 id="🧑💻-로컬-환경-의존성-제거">🧑‍💻 로컬 환경 의존성 제거</h3>
<p>환경 설정 충돌 없이 즉시 개발 가능</p>
<hr />
<h2 id="🔄-anywhere-anytime">🔄 Anywhere, Anytime</h2>
<p>인터넷만 있으면 어디서든 접속 가능</p>
<h3 id="⚙️-서버리스-및-인프라-개발에-최적화">⚙️ 서버리스 및 인프라 개발에 최적화</h3>
<p>Lambda 함수나 IaC (CloudFormation, CDK) 코드 작성에 용이</p>
<h3 id="💰-비용-효율성">💰 비용 효율성</h3>
<p>EC2를 중지하면 과금 중단</p>
<hr />
<h2 id="5️⃣-현업-활용-사례">5️⃣ 현업 활용 사례</h2>
<h3 id="🏗️-devops--클라우드-인프라-자동화">🏗️ DevOps &amp; 클라우드 인프라 자동화</h3>
<p>CloudFormation, Terraform, CDK 코드 작성</p>
<h3 id="🧪-교육--실습-환경">🧪 교육 &amp; 실습 환경</h3>
<p>개발자 교육, 부트캠프에서 빠른 환경 구성</p>
<h3 id="🧠-lambda-함수-개발">🧠 Lambda 함수 개발</h3>
<p>서버리스 함수 코드 작성 및 디버깅</p>
<h3 id="👥-원격-협업-개발">👥 원격 협업 개발</h3>
<p>개발자 간 실시간 코드 협업</p>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<p>AWS Cloud9 = 브라우저 기반 클라우드 개발 환경(IDE)</p>
<p>EC2 또는 Cloud9 환경에서 실행</p>
<p>다양한 언어 지원 + Git, AWS CLI 내장</p>
<p>현업에서는 서버리스 개발, 교육, DevOps 자동화, 협업 개발에 활용</p>
<p>👉 한마디로, “어디서든 접근 가능한 AWS의 클라우드 개발 IDE” 입니다.</p>