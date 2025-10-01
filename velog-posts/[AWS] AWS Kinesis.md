<h1 id="📡-aws-kinesis-정리">📡 AWS Kinesis 정리</h1>
<hr />
<h2 id="1️⃣-aws-kinesis란">1️⃣ AWS Kinesis란?</h2>
<p>Amazon Kinesis는 AWS에서 제공하는 실시간 데이터 스트리밍 서비스입니다.
대규모의 데이터를 실시간으로 수집·처리·분석할 수 있습니다.</p>
<p>👉 쉽게 말해,
“들어오는 데이터를 실시간으로 흘려보내고 가공할 수 있는 파이프라인” 입니다.</p>
<hr />
<h2 id="2️⃣-kinesis-구성-요소">2️⃣ Kinesis 구성 요소</h2>
<h3 id="kinesis-data-streams">Kinesis Data Streams</h3>
<p>초당 TB급 데이터 스트리밍 수집 가능</p>
<p>IoT 센서, 로그, 클릭스트림 등 이벤트 수집</p>
<h3 id="kinesis-data-firehose">Kinesis Data Firehose</h3>
<p>스트리밍 데이터를 자동으로 S3, Redshift, OpenSearch 등에 저장</p>
<p>실시간 데이터 → 저장소 연계</p>
<h3 id="kinesis-data-analytics">Kinesis Data Analytics</h3>
<p>SQL 기반 실시간 데이터 분석</p>
<p>품질 이상 탐지, 알람 처리 가능</p>
<h3 id="kinesis-video-streams">Kinesis Video Streams</h3>
<p>실시간 비디오 스트리밍 수집/처리</p>
<hr />
<h2 id="3️⃣-자동화-공장-품질-예측-시나리오">3️⃣ 자동화 공장 품질 예측 시나리오</h2>
<p>시나리오:
공장의 카메라/센서 데이터를 Kinesis로 수집하고, 실시간 분석을 통해 불량품 발생을 예측합니다.</p>
<p>공장 센서 → Kinesis Data Streams → Lambda/SageMaker → 품질 예측 → 알람/DB 저장</p>
<hr />
<h2 id="4️⃣-아키텍처-다이어그램-mermaid">4️⃣ 아키텍처 다이어그램 (Mermaid)</h2>
<pre><code class="language-mermaid">flowchart TD
    A[&quot;🏭 공장 센서/카메라&quot;] --&gt; B[&quot;Kinesis Data Streams (실시간 수집)&quot;]
    B --&gt; C[&quot;Kinesis Data Analytics (실시간 분석)&quot;]
    C --&gt; D[&quot;Amazon SageMaker (품질 예측 모델)&quot;]
    C --&gt; E[&quot;AWS Lambda (이벤트 처리)&quot;]

    E --&gt; F[&quot;DynamoDB (실시간 품질 로그 저장)&quot;]
    E --&gt; G[&quot;SNS/Slack (불량 알림)&quot;]
    D --&gt; H[&quot;S3 (학습/예측 데이터 저장)&quot;]</code></pre>
<h3 id="kinesis--lambda-실시간-이벤트-기반-처리">Kinesis + Lambda (실시간 이벤트 기반 처리)</h3>
<p>4️⃣-1️⃣ Kinesis + Lambda 아키텍처</p>
<pre><code class="language-mermaid">flowchart TD
    subgraph Factory[&quot;🏭 공장 설비&quot;]
        CAM[📷 센서/카메라] --&gt; GW[🌐 게이트웨이 서버]
    end

    GW --&gt; KIN[🚀 Amazon Kinesis Data Stream]

    subgraph Processing[&quot;⚡ 실시간 처리&quot;]
        KIN --&gt; LBD[🟢 AWS Lambda 함수]
        LBD --&gt; DDB[(🗄️ DynamoDB - 품질 이벤트 저장)]
        LBD --&gt; SNS[📢 Amazon SNS 알림]
    end

    subgraph User[&quot;👨‍💼 관리자/엔지니어&quot;]
        DDB --&gt; Dash[📊 웹 대시보드]
        SNS --&gt; Noti[📱 모바일/알림]
    end</code></pre>
<h3 id="특징">특징</h3>
<p>Lambda가 Kinesis 스트림을 실시간으로 읽고 품질 이벤트를 빠르게 가공</p>
<p>단순 규칙 기반 품질 판정, 알림 발송에 적합</p>
<p>지연 시간이 매우 낮음 (ms~초 단위)</p>
<hr />
<h3 id="kinesis--sagemaker-실시간배치-ai-모델-추론">Kinesis + SageMaker (실시간/배치 AI 모델 추론)</h3>
<p>4️⃣-2️⃣ Kinesis + SageMaker 아키텍처</p>
<pre><code class="language-mermaid">flowchart TD
    subgraph Factory[&quot;🏭 공장 설비&quot;]
        CAM[📷 센서/카메라] --&gt; GW[🌐 게이트웨이 서버]
    end

    GW --&gt; KIN[🚀 Amazon Kinesis Data Stream]

    subgraph AI[&quot;🤖 품질 예측 AI&quot;]
        KIN --&gt; SGM[🟣 Amazon SageMaker Endpoint]
        SGM --&gt;|추론 결과| RDS[(📂 Amazon Aurora 품질 DB)]
        SGM --&gt; S3[🗃️ Amazon S3 데이터 레이크]
    end

    subgraph User[&quot;👨‍💼 관리자/엔지니어&quot;]
        RDS --&gt; Dash[📊 웹 대시보드]
        Dash --&gt; Noti[📱 품질 이상 알림]
    end</code></pre>
<h3 id="특징-1">특징</h3>
<p>SageMaker Endpoint에서 실시간 추론 수행 → 고급 AI 품질 예측</p>
<p>RDS(Aurora) 및 S3에 결과 저장 → 통계/이력 관리</p>
<p>지연 시간은 Lambda보다 길지만 정밀한 예측 모델 활용 가능</p>
<hr />
<h3 id="🔎-비교-정리">🔎 비교 정리</h3>
<table>
<thead>
<tr>
<th>항목</th>
<th>Kinesis + Lambda</th>
<th>Kinesis + SageMaker</th>
</tr>
</thead>
<tbody><tr>
<td><strong>처리 속도</strong></td>
<td>매우 빠름 (ms~초)</td>
<td>상대적으로 느림 (초 단위)</td>
</tr>
<tr>
<td><strong>주요 목적</strong></td>
<td>단순 규칙 기반 알림, 이벤트 필터링</td>
<td>AI 기반 고급 품질 예측</td>
</tr>
<tr>
<td><strong>확장성</strong></td>
<td>이벤트 폭주 대응에 적합</td>
<td>대규모 AI 추론 확장 가능</td>
</tr>
<tr>
<td><strong>사용 사례</strong></td>
<td>즉시 알림, 라인 중지 트리거</td>
<td>품질 이상 예측, 통계 분석</td>
</tr>
</tbody></table>
<hr />
<h2 id="5️⃣-현업-활용-포인트">5️⃣ 현업 활용 포인트</h2>
<p>📡 센서 데이터 수집 → Kinesis Data Streams</p>
<p>⚡ 실시간 분석/이상 감지 → Kinesis Data Analytics</p>
<p>🤖 AI 예측 모델 적용 → SageMaker</p>
<p>📂 데이터 저장/백업 → S3, DynamoDB</p>
<p>🔔 불량품 알림 → SNS/Slack</p>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<p>AWS Kinesis = 실시간 데이터 스트리밍 플랫폼</p>
<p>Data Streams / Firehose / Analytics / Video Streams 네 가지 구성 요소</p>
<p>자동화 공장 시나리오에서 실시간 데이터 수집 → AI 분석 → 불량품 예측 → 알림까지 가능</p>
<p>👉 한마디로, “데이터를 실시간으로 모아 분석하는 AWS의 파이프라인” 입니다.</p>