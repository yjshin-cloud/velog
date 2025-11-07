<h1 id="💧-aws-lake-formation-정리">💧 AWS Lake Formation 정리</h1>
<hr />
<h2 id="1️⃣-aws-lake-formation이란">1️⃣ AWS Lake Formation이란?</h2>
<p>AWS Lake Formation은
기업이 데이터를 중앙 집중형 데이터 레이크(Data Lake) 로 손쉽게 구축·관리할 수 있도록
데이터 수집, 정제, 카탈로그 등록, 권한 제어를 자동화해주는 완전관리형 서비스입니다.</p>
<p>👉 쉽게 말해,
“AWS에서 클릭 몇 번으로 안전하고 체계적인 데이터 레이크를 만드는 서비스” 입니다.</p>
<hr />
<h2 id="2️⃣-데이터-레이크data-lake란">2️⃣ 데이터 레이크(Data Lake)란?</h2>
<p>여러 출처(데이터베이스, 로그, IoT 등)의 원시 데이터를 그대로 저장하는 중앙 저장소</p>
<p>형식 있는 데이터(Structured) + 비정형 데이터(Unstructured)를 함께 저장</p>
<p>나중에 ETL, 분석, 머신러닝, BI 용도로 활용</p>
<p>🧠 즉,
데이터 웨어하우스(Redshift)가 “정제된 데이터 분석용”이라면,
데이터 레이크는 “모든 데이터를 한 곳에 저장해 나중에 가공 가능한 원천 저장소”입니다.</p>
<hr />
<h2 id="3️⃣-주요-기능">3️⃣ 주요 기능</h2>
<table>
<thead>
<tr>
<th>기능</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>☁️ <strong>데이터 레이크 구축 자동화</strong></td>
<td>S3 기반 데이터 레이크를 자동으로 생성 및 구성</td>
</tr>
<tr>
<td>🧭 <strong>데이터 카탈로그 통합</strong></td>
<td>Glue Data Catalog와 통합되어 메타데이터 관리</td>
</tr>
<tr>
<td>🔒 <strong>보안 및 권한 관리 (Fine-grained Access Control)</strong></td>
<td>사용자별·테이블별 접근 제어</td>
</tr>
<tr>
<td>🧹 <strong>데이터 정제(ETL) 자동화</strong></td>
<td>Glue ETL과 연동하여 데이터 변환 및 준비 작업 수행</td>
</tr>
<tr>
<td>📊 <strong>다양한 분석 서비스 통합</strong></td>
<td>Athena, Redshift Spectrum, QuickSight 등과 연동</td>
</tr>
<tr>
<td>⚙️ <strong>거버넌스 및 감사</strong></td>
<td>CloudTrail, IAM과 통합된 접근 로그 및 정책 관리</td>
</tr>
</tbody></table>
<hr />
<h2 id="4️⃣-아키텍처-시각화">4️⃣ 아키텍처 시각화</h2>
<pre><code class="language-mermaid">flowchart TD
    A[📥 데이터 소스 ⤵️  
    🗄️ RDS / ⚡ DynamoDB / 🏠 On-Premise / 🌐 IoT / 📜 Logs] --&gt; B[🧩 AWS Lake Formation ⤵️  
    데이터 수집·통합·권한 관리]
    B --&gt; C[💧 Amazon S3 ⤵️  
    Data Lake Storage]
    B --&gt; D[🧠 AWS Glue ⤵️  
    Data Catalog · ETL 변환]
    D --&gt; E[📊 Amazon Athena · 🧮 Redshift Spectrum · 🔥 EMR · 📈 QuickSight]
    B --&gt; F[🛡️ Fine-Grained Access Control ⤵️  
    보안 · 권한 관리]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/8de818c1-20ff-4f79-b8f0-c481be69d803/image.png" /></p>
<p>🧠 설명:</p>
<p>S3가 데이터 저장소 역할</p>
<p>Glue가 데이터 탐색 및 정제(ETL) 담당</p>
<p>Lake Formation이 보안/거버넌스/권한 관리 통합</p>
<p>Athena·Redshift·QuickSight에서 분석 및 시각화 수행</p>
<hr />
<h2 id="5️⃣-lake-formation-구성-요소">5️⃣ Lake Formation 구성 요소</h2>
<table>
<thead>
<tr>
<th>구성 요소</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td><strong>Data Lake Storage (S3)</strong></td>
<td>모든 데이터의 중앙 저장소</td>
</tr>
<tr>
<td><strong>Data Catalog (Glue)</strong></td>
<td>데이터 메타데이터를 저장 (테이블 구조, 경로, 스키마 등)</td>
</tr>
<tr>
<td><strong>Data Access Policies</strong></td>
<td>사용자 및 IAM 역할별 세분화된 접근 제어</td>
</tr>
<tr>
<td><strong>Blueprints</strong></td>
<td>데이터 파이프라인 생성 자동화 템플릿</td>
</tr>
<tr>
<td><strong>Data Filter / Tagging</strong></td>
<td>데이터 자산 분류 및 검색 용이성 향상</td>
</tr>
</tbody></table>
<hr />
<h2 id="6️⃣-lake-formation과-glue의-관계">6️⃣ Lake Formation과 Glue의 관계</h2>
<table>
<thead>
<tr>
<th align="left">구분</th>
<th align="left">🧠 <strong>AWS Glue</strong></th>
<th align="left">🧩 <strong>AWS Lake Formation</strong></th>
</tr>
</thead>
<tbody><tr>
<td align="left"><strong>주요 역할</strong></td>
<td align="left">데이터 탐색, ETL, 카탈로그 관리</td>
<td align="left">데이터 보안, 권한, 거버넌스 관리</td>
</tr>
<tr>
<td align="left"><strong>데이터 저장소</strong></td>
<td align="left">💧 S3 (Data Lake)</td>
<td align="left">💧 S3 (Glue와 공유)</td>
</tr>
<tr>
<td align="left"><strong>ETL 작업</strong></td>
<td align="left">⚙️ Glue Job, 🧭 Crawler</td>
<td align="left">🔄 Glue 기반으로 자동 실행</td>
</tr>
<tr>
<td align="left"><strong>보안 모델</strong></td>
<td align="left">🔐 IAM 정책 기반</td>
<td align="left">🛡️ Row / Column 수준 세밀한 접근 제어</td>
</tr>
<tr>
<td align="left"><strong>통합 서비스</strong></td>
<td align="left">📊 Athena, 🧮 Redshift, 📈 QuickSight</td>
<td align="left">🤝 Glue, IAM, CloudTrail, S3 등</td>
</tr>
</tbody></table>
<p>✅ 요약</p>
<p>Glue → 데이터의 탐색·정제·변환(ETL) 및 Data Catalog 관리 담당</p>
<p>Lake Formation → Glue의 기능을 확장하여 보안·거버넌스 중심으로 관리</p>
<p>Glue가 데이터 처리 엔진, Lake Formation이 통합 관리 허브 역할</p>
<p>📌 정리:
Lake Formation은 Glue를 포함한 상위 개념의 데이터 레이크 통합 플랫폼입니다.</p>
<hr />
<h2 id="7️⃣-데이터-레이크-구축-단계">7️⃣ 데이터 레이크 구축 단계</h2>
<pre><code class="language-mermaid">sequenceDiagram
    participant Source as 📥 데이터 소스  
    participant Lake as 🧩 AWS Lake Formation  
    participant S3 as 💧 Amazon S3 (Data Lake)  
    participant Glue as 🧠 AWS Glue  
    participant Athena as 📊 Athena / 🧮 Redshift / 📈 QuickSight  

    Source-&gt;&gt;Lake: 📤 데이터 등록 및 🔐 접근 권한 설정  
    Lake-&gt;&gt;S3: 📦 원본 데이터 수집 및 저장  
    Lake-&gt;&gt;Glue: 🧭 Crawler 실행 (스키마 자동 탐색)  
    Glue--&gt;&gt;Lake: 🗂️ Data Catalog 업데이트  
    Lake-&gt;&gt;Athena: 🔎 쿼리 및 분석 요청  </code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/a3770cb1-1aaf-4ced-b7bf-aacb3423e7f2/image.png" /></p>
<hr />
<h2 id="8️⃣-현업-활용-사례">8️⃣ 현업 활용 사례</h2>
<table>
<thead>
<tr>
<th>산업</th>
<th>활용 예시</th>
</tr>
</thead>
<tbody><tr>
<td>🏦 <strong>금융기관</strong></td>
<td>거래 로그, 고객 데이터 통합 저장 → BI 분석 자동화</td>
</tr>
<tr>
<td>🏭 <strong>제조 / IoT</strong></td>
<td>센서 데이터 레이크 구축 → Glue ETL → SageMaker 예측 모델 학습</td>
</tr>
<tr>
<td>🧠 <strong>데이터 분석 조직</strong></td>
<td>부서별 접근 권한 제어, Athena로 쿼리 분석</td>
</tr>
<tr>
<td>🛒 <strong>이커머스 / 마케팅</strong></td>
<td>웹 로그 + CRM 데이터 통합 → QuickSight 대시보드 시각화</td>
</tr>
</tbody></table>
<hr />
<h2 id="9️⃣-lake-formation-기반-데이터-분석-파이프라인">9️⃣ Lake Formation 기반 데이터 분석 파이프라인</h2>
<pre><code class="language-mermaid">flowchart TD
    A[🏠 On-Premise · 🗄️ RDS · 📜 Logs] --&gt; B[⚙️ AWS DMS · 🌊 Kinesis · 🧭 Glue Crawler]
    B --&gt; C[🧩 Lake Formation 🪣 S3 + 📚 Catalog + 🛡️ Policy]
    C --&gt; D[🧠 AWS Glue ETL 🔄 정제 및 변환]
    D --&gt; E[📊 Athena · 🧮 Redshift · 🔥 EMR]
    E --&gt; F[📈 QuickSight 💡 시각화 및 BI 분석]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/71f817ae-444e-495e-b462-e7029a950d22/image.png" /></p>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<p>AWS Lake Formation = 데이터 레이크 구축, 관리, 보안 자동화 서비스</p>
<p>구성요소: S3, Glue, IAM, Data Catalog</p>
<p>핵심기능:</p>
<p>데이터 수집/정제 자동화</p>
<p>접근 제어 및 거버넌스</p>
<p>Glue 통합 및 Athena 분석 지원</p>
<p>현업활용:</p>
<p>데이터 분석 파이프라인, BI 시각화, 머신러닝 학습 데이터 관리</p>
<p>👉 한마디로,
“AWS Lake Formation은 AWS의 데이터 관리 플랫폼의 중심 —
데이터 레이크 구축부터 보안·분석까지 한 번에 해결하는 서비스” 입니다.</p>