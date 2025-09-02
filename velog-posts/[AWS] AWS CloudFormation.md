<h1 id="🏗️-aws-cloudformation-정리">🏗️ AWS CloudFormation 정리</h1>
<hr />
<h2 id="1️⃣-cloudformation이란">1️⃣ CloudFormation이란?</h2>
<p>AWS CloudFormation 은
인프라(AWS 리소스)를 코드(JSON 또는 YAML)로 정의하고, 자동으로 생성·수정·삭제할 수 있게 해주는 서비스입니다.</p>
<p>👉 쉽게 말해,
“클라우드 리소스를 사람이 클릭해서 만들지 않고, 코드로 선언하면 AWS가 대신 만들어주는 서비스” 입니다.</p>
<h2 id="2️⃣-cloudformation의-주요-특징">2️⃣ CloudFormation의 주요 특징</h2>
<p>📝 Infrastructure as Code (IaC)</p>
<p>인프라를 코드(YAML/JSON)로 관리</p>
<p>🔄 자동화</p>
<p>반복적인 리소스 생성·삭제를 자동 처리</p>
<p>🛡️ 일관성</p>
<p>같은 코드로 여러 환경(개발/테스트/운영)에서 동일한 인프라 생성 가능</p>
<p>⏱️ 시간 절약</p>
<p>클릭 몇 번보다 훨씬 빠르고 실수 없는 인프라 배포</p>
<p>📑 변경 추적(Change Set)</p>
<p>인프라 변경 사항을 사전에 미리 확인 가능</p>
<h2 id="3️⃣-cloudformation-아키텍처-개념도">3️⃣ CloudFormation 아키텍처 개념도</h2>
<p>graph TD
    User[👩‍💻 개발자/운영자] --&gt; Template[&quot;YAML/JSON Template&quot;]
    Template --&gt; CFN[🏗️ CloudFormation]</p>
<pre><code>CFN --&gt; Stack[&quot;Stack (리소스 집합)&quot;]

subgraph AWS Resources
    EC2[EC2 Instances]
    S3[S3 Buckets]
    RDS[RDS Database]
    VPC[VPC Network]
end

Stack --&gt; EC2
Stack --&gt; S3
Stack --&gt; RDS
Stack --&gt; VPC</code></pre><h2 id="4️⃣-cloudformation-동작-방식">4️⃣ CloudFormation 동작 방식</h2>
<p>템플릿 작성</p>
<p>YAML/JSON 형식으로 인프라 정의</p>
<p>예: EC2, VPC, S3, RDS 등</p>
<p>스택(Stack) 생성</p>
<p>CloudFormation이 템플릿을 읽고 리소스를 자동 생성</p>
<p>스택 업데이트</p>
<p>코드 변경 → 기존 인프라 자동 수정</p>
<p>스택 삭제</p>
<p>스택 삭제 시 모든 관련 리소스 자동 삭제</p>
<h2 id="5️⃣-템플릿-예시-yaml">5️⃣ 템플릿 예시 (YAML)</h2>
<p>AWSTemplateFormatVersion: &quot;2010-09-09&quot;
Description: &quot;EC2와 S3를 포함한 간단한 예시&quot;</p>
<p>Resources:
  MyEC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType: t2.micro
      ImageId: ami-0abcd1234efgh5678
  MyS3Bucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: my-til-blog-bucket</p>
<h2 id="📝-코드-설명">📝 코드 설명</h2>
<p>Resources : 생성할 리소스를 정의하는 섹션</p>
<p>MyEC2Instance : EC2 인스턴스 리소스 이름</p>
<p>Type: AWS::EC2::Instance → EC2를 생성</p>
<p>InstanceType: t2.micro → 서버 크기 지정</p>
<p>ImageId → AMI 이미지 ID</p>
<p>MyS3Bucket : S3 버킷 리소스</p>
<p>BucketName → 버킷 이름 지정</p>
<h2 id="6️⃣-현업에서의-활용">6️⃣ 현업에서의 활용</h2>
<p>현업에서는 CloudFormation을 다음과 같이 씁니다.</p>
<p>🛠 인프라 자동 배포</p>
<p>개발/테스트/운영 환경을 동일하게 복제</p>
<p>🚀 CI/CD 파이프라인 통합</p>
<p>CodePipeline, CodeDeploy와 연동 → 앱과 인프라 동시 배포</p>
<p>🛡️ 보안/컴플라이언스 준수</p>
<p>표준 템플릿을 작성해 조직 내 인프라 규칙 강제</p>
<p>📈 비용 관리 및 추적</p>
<p>스택 단위로 리소스 관리 → 불필요한 리소스 쉽게 정리</p>
<h2 id="✅-정리">✅ 정리</h2>
<p>AWS CloudFormation은</p>
<p>인프라를 코드로 관리(IaC) 하고,</p>
<p>자동화·일관성·보안을 강화하며,</p>
<p>시간과 비용을 절약할 수 있는 서비스입니다.</p>
<p>👉 한마디로, “클라우드 인프라 자동 생성기” 입니다.</p>