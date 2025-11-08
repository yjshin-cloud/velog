<h1 id="📊-amazon-quicksight-정리">📊 Amazon QuickSight 정리</h1>
<hr />
<h2 id="1️⃣-amazon-quicksight란">1️⃣ Amazon QuickSight란?</h2>
<p>Amazon QuickSight는
AWS에서 제공하는 클라우드 기반 비즈니스 인텔리전스(BI) 서비스입니다.</p>
<p>👉 쉽게 말해,
“데이터를 예쁘게 시각화하고, 분석 리포트를 자동으로 만들어주는 AWS의 BI 도구” 입니다.</p>
<p>QuickSight는 Excel처럼 데이터를 표와 그래프로 시각화하면서도,
AWS의 S3·Redshift·RDS·Athena 등과 직접 연결되어 자동 분석 및 대시보드 생성이 가능합니다.</p>
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
<td>📈 <strong>대시보드 시각화</strong></td>
<td>차트, 그래프, KPI 지표, 지도 시각화 등 다양한 시각화 기능</td>
</tr>
<tr>
<td>🧠 <strong>ML Insights (AI 분석)</strong></td>
<td>머신러닝 기반 이상 탐지, 자동 예측, KPI 트렌드 분석</td>
</tr>
<tr>
<td>☁️ <strong>서버리스 / 완전관리형</strong></td>
<td>인프라 구축 없이 바로 사용 가능 (SaaS형 BI 서비스)</td>
</tr>
<tr>
<td>🔗 <strong>다양한 데이터 소스 연동</strong></td>
<td>RDS, Redshift, Athena, S3, Salesforce, Excel 등</td>
</tr>
<tr>
<td>🧩 <strong>SPICE 엔진</strong></td>
<td>인메모리 캐싱 기반 초고속 쿼리 처리 엔진</td>
</tr>
<tr>
<td>🔒 <strong>IAM 기반 보안</strong></td>
<td>IAM, VPC, KMS 통합 보안 제어</td>
</tr>
<tr>
<td>💰 <strong>사용량 기반 요금제 (Pay-per-session)</strong></td>
<td>사용자 로그인 수에 따라 요금 과금</td>
</tr>
</tbody></table>
<hr />
<h2 id="3️⃣-아키텍처-시각화">3️⃣ 아키텍처 시각화</h2>
<pre><code class="language-mermaid">flowchart TD
    A[&quot;💾 데이터 소스 (S3 / RDS / Redshift / Athena / Excel 등)&quot;] --&gt; B[&quot;AWS Glue / Lake Formation (데이터 정제 및 카탈로그)&quot;]
    B --&gt; C[&quot;Amazon QuickSight&quot;]
    C --&gt; D[&quot;📊 대시보드 / 리포트 / KPI 시각화&quot;]
    C --&gt; E[&quot;🤖 ML Insights (이상 탐지 / 예측)&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/db737f3d-1ef5-46c9-940f-3cec7604ba1d/image.png" /></p>
<p>🧠 설명:</p>
<p>QuickSight는 AWS 내 다양한 데이터 소스와 직접 연결</p>
<p>Glue/Lake Formation과 통합되어 데이터 정제 및 접근 제어</p>
<p>SPICE 인메모리 엔진을 사용해 빠른 쿼리와 시각화 지원</p>
<hr />
<h2 id="4️⃣-spice란">4️⃣ SPICE란?</h2>
<p>SPICE (Super-fast, Parallel, In-memory Calculation Engine)</p>
<table>
<thead>
<tr>
<th>항목</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>역할</td>
<td>QuickSight의 내부 인메모리 엔진</td>
</tr>
<tr>
<td>특징</td>
<td>데이터 쿼리 없이 즉시 분석 가능</td>
</tr>
<tr>
<td>장점</td>
<td>빠른 쿼리 속도, 사용자당 대시보드 응답 지연 최소화</td>
</tr>
<tr>
<td>비유</td>
<td>“QuickSight 전용 캐시 메모리”</td>
</tr>
</tbody></table>
<hr />
<h2 id="5️⃣-quicksight의-구성요소">5️⃣ QuickSight의 구성요소</h2>
<table>
<thead>
<tr>
<th>구성 요소</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td><strong>Dataset</strong></td>
<td>데이터 소스 연결 및 변환된 데이터 세트</td>
</tr>
<tr>
<td><strong>Analysis</strong></td>
<td>데이터 시각화 및 차트 생성 화면</td>
</tr>
<tr>
<td><strong>Dashboard</strong></td>
<td>공유 가능한 BI 리포트</td>
</tr>
<tr>
<td><strong>ML Insights</strong></td>
<td>머신러닝 기반 이상 탐지 및 예측</td>
</tr>
<tr>
<td><strong>SPICE</strong></td>
<td>인메모리 캐시 엔진</td>
</tr>
</tbody></table>
<hr />
<h2 id="6️⃣-주요-기능-요약">6️⃣ 주요 기능 요약</h2>
<table>
<thead>
<tr>
<th>기능</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>📊 <strong>시각화(Visualization)</strong></td>
<td>차트, 테이블, 지도, KPI 위젯 등</td>
</tr>
<tr>
<td>🔎 <strong>드릴다운 분석</strong></td>
<td>클릭으로 데이터 세부 항목 탐색</td>
</tr>
<tr>
<td>🧠 <strong>AI 분석 (ML Insights)</strong></td>
<td>매출 예측, 이상 탐지, 트렌드 분석</td>
</tr>
<tr>
<td>🤝 <strong>공유 기능</strong></td>
<td>대시보드를 이메일, 링크, 임베딩 형태로 공유</td>
</tr>
<tr>
<td>🔐 <strong>보안 및 거버넌스</strong></td>
<td>IAM, KMS, VPC, CloudTrail 통합</td>
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
<td>🏦 <strong>금융권</strong></td>
<td>고객 거래 내역 분석 및 대시보드 리포트</td>
</tr>
<tr>
<td>🏭 <strong>제조 / IoT</strong></td>
<td>센서 데이터의 실시간 생산 현황 모니터링</td>
</tr>
<tr>
<td>🛒 <strong>이커머스</strong></td>
<td>매출 트렌드, 인기 상품, 방문자 로그 시각화</td>
</tr>
<tr>
<td>🧠 <strong>데이터 분석 조직</strong></td>
<td>S3 + Athena 기반 데이터 분석 및 공유</td>
</tr>
<tr>
<td>🧩 <strong>경영진 리포트 자동화</strong></td>
<td>매출/비용 지표를 매일 자동 업데이트하여 시각화</td>
</tr>
</tbody></table>
<hr />
<h2 id="8️⃣-quicksight--aws-데이터-분석-파이프라인">8️⃣ QuickSight + AWS 데이터 분석 파이프라인</h2>
<pre><code class="language-mermaid">flowchart TD
    A[&quot;💾 RDS / 🧩 DynamoDB / 📜 Logs / 🔌 IoT&quot;] --&gt; B[&quot;⚙️ AWS Glue (ETL 변환)&quot;]
    B --&gt; C[&quot;☁️ Amazon S3 (Data Lake)&quot;]
    C --&gt; D[&quot;🔍 Amazon Athena (쿼리 분석)&quot;]
    D --&gt; E[&quot;📊 Amazon QuickSight (시각화 / BI 리포트)&quot;]
    E --&gt; F[&quot;📱 대시보드 공유 (🌐 웹 / 📱 모바일 / 🧭 임베드)&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/561628b9-f6c1-4dd5-a0ab-a2664731f2a9/image.png" /></p>
<p>🧠 설명:
Glue로 데이터를 정제 → S3에 저장 → Athena로 쿼리 → QuickSight에서 시각화 및 리포트 생성</p>
<hr />
<h2 id="9️⃣-quicksight-vs-tableau--power-bi-비교">9️⃣ QuickSight vs Tableau / Power BI 비교</h2>
<table>
<thead>
<tr>
<th>항목</th>
<th><strong>QuickSight</strong></th>
<th><strong>Tableau</strong></th>
<th><strong>Power BI</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>플랫폼</strong></td>
<td>AWS 클라우드 (SaaS형)</td>
<td>온프레미스 + 클라우드</td>
<td>Microsoft 클라우드</td>
</tr>
<tr>
<td><strong>요금제</strong></td>
<td>세션당 과금 (저렴)</td>
<td>사용자당 라이선스</td>
<td>사용자당 라이선스</td>
</tr>
<tr>
<td><strong>확장성</strong></td>
<td>AWS 서비스와 완전 통합</td>
<td>별도 설정 필요</td>
<td>Azure 서비스와 연동</td>
</tr>
<tr>
<td><strong>ML 기능</strong></td>
<td>내장형 ML Insights</td>
<td>별도 AI 연동 필요</td>
<td>Azure ML 연동</td>
</tr>
<tr>
<td><strong>데이터 소스</strong></td>
<td>AWS 기반 (S3, Athena, RDS 등)</td>
<td>다양한 외부 연동</td>
<td>MS SQL / Excel 중심</td>
</tr>
</tbody></table>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<p>Amazon QuickSight = 클라우드 기반 BI 시각화 서비스</p>
<p>특징:</p>
<p>서버리스 + AI 내장 분석 + SPICE 인메모리 처리</p>
<p>데이터 소스: S3, Athena, Redshift, RDS, Excel 등</p>
<p>현업 활용: 대시보드 자동화, 이상 탐지, 데이터 기반 의사결정</p>
<p>👉 한마디로,
“Amazon QuickSight는 AWS 환경의 데이터를 한눈에 보여주는 클라우드 BI 플랫폼” 입니다.</p>