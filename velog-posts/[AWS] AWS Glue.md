<h1 id="🧩-aws-glue-정리">🧩 AWS Glue 정리</h1>
<hr />
<h2 id="1️⃣-aws-glue란">1️⃣ AWS Glue란?</h2>
<p>AWS Glue는
데이터를 수집, 정제, 변환, 통합(ETL) 하는 과정을 자동화해주는
서버리스 데이터 통합 서비스 (Serverless ETL Service) 입니다.</p>
<p>👉 쉽게 말해,
“S3, RDS, Redshift 등에 흩어진 데이터를 자동으로 정리해주는 AWS의 데이터 파이프라인 도우미” 입니다.</p>
<hr />
<h2 id="2️⃣-주요-기능">2️⃣ 주요 기능</h2>
<table>
<thead>
<tr>
<th>기능</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>📦 <strong>ETL (Extract, Transform, Load)</strong></td>
<td>데이터를 추출 → 변환 → 대상 저장소로 로드</td>
</tr>
<tr>
<td>🧠 <strong>데이터 카탈로그 (Glue Data Catalog)</strong></td>
<td>데이터의 메타데이터(스키마, 테이블 구조) 자동 관리</td>
</tr>
<tr>
<td>🔄 <strong>Glue Crawler</strong></td>
<td>S3, RDS, DynamoDB 등의 데이터 소스를 자동 스캔하여 스키마 생성</td>
</tr>
<tr>
<td>⚙️ <strong>서버리스 실행</strong></td>
<td>인프라 관리 없이 자동 확장되는 Spark 기반 클러스터로 처리</td>
</tr>
<tr>
<td>🧱 <strong>Job / Trigger 관리</strong></td>
<td>정기 실행, 조건부 실행, 이벤트 기반 자동 실행 가능</td>
</tr>
<tr>
<td>🔍 <strong>Glue Studio / DataBrew</strong></td>
<td>GUI 기반 데이터 시각화 및 정제 도구 (비개발자도 사용 가능)</td>
</tr>
</tbody></table>
<hr />
<h2 id="3️⃣-아키텍처-시각화">3️⃣ 아키텍처 시각화</h2>
<hr />
<pre><code class="language-mermaid">flowchart TD
    A[&quot;데이터 소스 (S3, RDS, DynamoDB, On-Premise)&quot;] --&gt; B[&quot;Glue Crawler (스키마 자동 탐색)&quot;]
    B --&gt; C[&quot;Glue Data Catalog (메타데이터 저장소)&quot;]
    C --&gt; D[&quot;Glue ETL Job (Spark 기반 변환 작업)&quot;]
    D --&gt; E[&quot;대상 저장소 (S3, Redshift, Athena 등)&quot;]
    E --&gt; F[&quot;Amazon Athena / QuickSight (분석 및 시각화)&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/20bdc38f-fb06-40bd-bac2-1d0581e47fa6/image.png" /></p>
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
<td><strong>Glue Data Catalog</strong></td>
<td>데이터베이스와 테이블 메타데이터를 저장하는 중앙 저장소</td>
</tr>
<tr>
<td><strong>Glue Crawler</strong></td>
<td>원본 데이터를 스캔해 자동으로 카탈로그 생성</td>
</tr>
<tr>
<td><strong>Glue Job</strong></td>
<td>ETL 스크립트를 실행하는 단위 (Python / PySpark 기반)</td>
</tr>
<tr>
<td><strong>Trigger</strong></td>
<td>Job을 예약 실행하거나 이벤트 기반으로 실행</td>
</tr>
<tr>
<td><strong>Glue Studio</strong></td>
<td>GUI 기반 ETL 설계 도구</td>
</tr>
<tr>
<td><strong>Glue DataBrew</strong></td>
<td>코드 없이 시각적으로 데이터 정제 및 분석 준비</td>
</tr>
</tbody></table>
<hr />
<h2 id="5️⃣-glue-동작-과정-etl-프로세스">5️⃣ Glue 동작 과정 (ETL 프로세스)</h2>
<pre><code class="language-mermaid">sequenceDiagram
    participant Source as 데이터 소스(S3, RDS 등)
    participant Crawler as Glue Crawler
    participant Catalog as Glue Data Catalog
    participant Job as Glue ETL Job
    participant Target as 대상 저장소(S3/Redshift)

    Source-&gt;&gt;Crawler: 데이터 스캔 요청
    Crawler-&gt;&gt;Catalog: 메타데이터 생성/업데이트
    Job-&gt;&gt;Source: 원본 데이터 추출 (Extract)
    Job-&gt;&gt;Job: 데이터 변환 (Transform)
    Job-&gt;&gt;Target: 결과 저장 (Load)</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/ae4219bf-4d05-47b6-96cc-0a2a543d723b/image.png" /></p>
<hr />
<h2 id="6️⃣-현업-활용-사례">6️⃣ 현업 활용 사례</h2>
<table>
<thead>
<tr>
<th>산업</th>
<th>활용 예시</th>
</tr>
</thead>
<tbody><tr>
<td>🏦 <strong>금융</strong></td>
<td>거래 로그 정제 및 Redshift 분석용 데이터로 변환</td>
</tr>
<tr>
<td>🏭 <strong>제조/IoT</strong></td>
<td>공장 센서 데이터 정제 후 S3에 저장 → Athena 분석</td>
</tr>
<tr>
<td>🛒 <strong>이커머스</strong></td>
<td>고객 행동 로그 → 분석용 테이블 자동 생성</td>
</tr>
<tr>
<td>🧠 <strong>데이터 분석팀</strong></td>
<td>Glue DataBrew로 데이터 전처리 후 SageMaker 학습에 활용</td>
</tr>
</tbody></table>
<hr />
<h2 id="7️⃣-glue와-관련-서비스-비교">7️⃣ Glue와 관련 서비스 비교</h2>
<table>
<thead>
<tr>
<th>서비스</th>
<th>주요 기능</th>
<th>특징</th>
</tr>
</thead>
<tbody><tr>
<td><strong>AWS Glue</strong></td>
<td>ETL 자동화</td>
<td>서버리스, Spark 기반, 대규모 데이터 처리</td>
</tr>
<tr>
<td><strong>AWS Data Pipeline</strong></td>
<td>배치 워크플로우</td>
<td>EC2 기반, 관리형 스케줄러</td>
</tr>
<tr>
<td><strong>AWS Lambda</strong></td>
<td>실시간 처리</td>
<td>이벤트 기반 데이터 변환 (소규모)</td>
</tr>
<tr>
<td><strong>AWS Step Functions</strong></td>
<td>워크플로우 관리</td>
<td>Glue Job 간 순서 제어 및 상태 관리</td>
</tr>
</tbody></table>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<p>AWS Glue = 서버리스 데이터 ETL 서비스</p>
<p>구성요소: Crawler, Data Catalog, Job, Trigger, DataBrew</p>
<p>핵심기능: 데이터 정제·통합·자동화</p>
<p>현업활용: 로그 분석, 데이터 파이프라인 구축, 머신러닝 데이터 준비</p>
<p>👉 한마디로,
“AWS Glue는 데이터를 자동으로 정리해주는 클라우드 기반 데이터 청소기” 입니다.</p>