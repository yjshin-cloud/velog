<h1 id="⚡-amazon-dynamodb-정리">⚡ Amazon DynamoDB 정리</h1>
<hr />
<h2 id="1️⃣-amazon-dynamodb란">1️⃣ Amazon DynamoDB란?</h2>
<p>Amazon DynamoDB는
AWS에서 제공하는 완전관리형 NoSQL 데이터베이스 서비스입니다.</p>
<p>👉 쉽게 말해,
“RDS는 관계형(표 구조) 데이터베이스, DynamoDB는 빠르고 유연한 비관계형(키-값) 데이터베이스” 입니다.</p>
<h2 id="2️⃣-주요-특징">2️⃣ 주요 특징</h2>
<hr />
<table>
<thead>
<tr>
<th>특징</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>☁️ <strong>완전관리형</strong></td>
<td>서버 운영, 스케일링, 백업 등 모두 AWS가 자동 관리</td>
</tr>
<tr>
<td>⚡ <strong>고성능 / 저지연</strong></td>
<td>밀리초 단위 응답 속도, SSD 기반 고성능</td>
</tr>
<tr>
<td>📈 <strong>자동 확장성 (Auto Scaling)</strong></td>
<td>트래픽 증가 시 자동으로 처리량 확장</td>
</tr>
<tr>
<td>💾 <strong>무한 확장 테이블</strong></td>
<td>데이터 용량에 제한 없음</td>
</tr>
<tr>
<td>🔄 <strong>멀티 리전 복제 (Global Table)</strong></td>
<td>여러 리전에 데이터 자동 복제</td>
</tr>
<tr>
<td>🧱 <strong>서버리스 아키텍처</strong></td>
<td>인프라 관리 불필요, 사용량 기반 과금</td>
</tr>
<tr>
<td>🛡 <strong>보안 / 백업 / 암호화 내장</strong></td>
<td>KMS, IAM, CloudWatch 통합</td>
</tr>
</tbody></table>
<hr />
<h2 id="3️⃣-데이터-모델-구조">3️⃣ 데이터 모델 구조</h2>
<table>
<thead>
<tr>
<th>구성 요소</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td><strong>Table</strong></td>
<td>데이터가 저장되는 기본 단위</td>
</tr>
<tr>
<td><strong>Item</strong></td>
<td>한 줄(Row)에 해당하는 데이터</td>
</tr>
<tr>
<td><strong>Attribute</strong></td>
<td>Item 내의 필드(Column)</td>
</tr>
<tr>
<td><strong>Primary Key</strong></td>
<td>데이터를 식별하는 고유 키 (Partition Key + Sort Key 조합 가능)</td>
</tr>
<tr>
<td><strong>Index</strong></td>
<td>검색 성능 향상을 위한 보조 인덱스 (GSI, LSI)</td>
</tr>
</tbody></table>
<hr />
<h2 id="4️⃣-아키텍처-시각화">4️⃣ 아키텍처 시각화</h2>
<hr />
<pre><code class="language-mermaid">flowchart TD
    A[&quot;💻 Application / API Gateway&quot;] --&gt; B[&quot;⚡ Amazon DynamoDB&quot;]
    B --&gt; C[&quot;📊 DynamoDB Streams (변경 이벤트 캡처)&quot;]
    C --&gt; D[&quot;⚙️ AWS Lambda (이벤트 기반 처리)&quot;]
    B --&gt; E[&quot;📦 S3 (백업 및 내보내기)&quot;]
    B --&gt; F[&quot;🌍 Global Tables (리전 간 동기화)&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/9daf73a0-2a20-470a-9548-35faa00eed90/image.png" /></p>
<hr />
<h2 id="5️⃣-주요-기능">5️⃣ 주요 기능</h2>
<table>
<thead>
<tr>
<th>기능</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td><strong>On-Demand / Provisioned 모드</strong></td>
<td>트래픽 예측 불가 시 On-Demand, 고정 트래픽이면 Provisioned 선택</td>
</tr>
<tr>
<td><strong>DynamoDB Streams</strong></td>
<td>테이블 데이터 변경 시 실시간 이벤트 감지 가능 (Lambda 트리거용)</td>
</tr>
<tr>
<td><strong>Global Tables</strong></td>
<td>여러 리전에 걸쳐 데이터 자동 동기화</td>
</tr>
<tr>
<td><strong>Time to Live (TTL)</strong></td>
<td>일정 시간이 지나면 자동으로 데이터 삭제</td>
</tr>
<tr>
<td><strong>Backup &amp; Restore</strong></td>
<td>전체 테이블 백업/복구 기능 제공</td>
</tr>
<tr>
<td><strong>DAX (DynamoDB Accelerator)</strong></td>
<td>인메모리 캐시 서비스로 지연 시간 최소화</td>
</tr>
</tbody></table>
<hr />
<h2 id="6️⃣-dynamodb-vs-rds-비교">6️⃣ DynamoDB vs RDS 비교</h2>
<table>
<thead>
<tr>
<th>항목</th>
<th><strong>DynamoDB (NoSQL)</strong></th>
<th><strong>RDS (SQL)</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>데이터 모델</strong></td>
<td>Key-Value, 문서형</td>
<td>테이블, 행, 열 구조</td>
</tr>
<tr>
<td><strong>스키마</strong></td>
<td>자유로운 구조 (스키마리스)</td>
<td>고정된 스키마</td>
</tr>
<tr>
<td><strong>확장성</strong></td>
<td>수평 확장 (Auto Scaling)</td>
<td>수직 확장 중심</td>
</tr>
<tr>
<td><strong>쿼리 방식</strong></td>
<td>Key 기반 조회 (빠름)</td>
<td>SQL 문법 기반</td>
</tr>
<tr>
<td><strong>트랜잭션</strong></td>
<td>제한적 (단일 테이블 중심)</td>
<td>복잡한 트랜잭션 가능</td>
</tr>
<tr>
<td><strong>사용 예시</strong></td>
<td>IoT, 로그, 실시간 채팅, 세션 관리</td>
<td>ERP, 회계, 주문 DB 등</td>
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
<td>🏭 <strong>IoT / 제조</strong></td>
<td>센서 데이터 실시간 저장 및 조회</td>
</tr>
<tr>
<td>🛒 <strong>이커머스 / 게임</strong></td>
<td>사용자 세션, 장바구니, 순위 데이터 관리</td>
</tr>
<tr>
<td>💬 <strong>메신저 / 채팅</strong></td>
<td>빠른 읽기/쓰기 기반의 대화 로그 저장</td>
</tr>
<tr>
<td>📊 <strong>데이터 분석 파이프라인</strong></td>
<td>DynamoDB Streams → Lambda → S3 ETL 파이프라인 구성</td>
</tr>
<tr>
<td>🧠 <strong>서버리스 백엔드</strong></td>
<td>API Gateway + Lambda + DynamoDB 조합으로 완전 서버리스 아키텍처 구성</td>
</tr>
</tbody></table>
<hr />
<h2 id="8️⃣-서버리스-애플리케이션-아키텍처-예시">8️⃣ 서버리스 애플리케이션 아키텍처 예시</h2>
<pre><code class="language-mermaid">flowchart TD
    U[&quot;👤 사용자 요청 (Web/App)&quot;] --&gt; G[&quot;API Gateway&quot;]
    G --&gt; L[&quot;AWS Lambda (비즈니스 로직)&quot;]
    L --&gt; D[&quot;DynamoDB (데이터 저장)&quot;]
    D --&gt; S[&quot;DynamoDB Streams&quot;]
    S --&gt; A[&quot;Lambda (이벤트 처리 / 백업 / 분석 연동)&quot;]</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/33d9ca97-5ef1-46e6-972e-d81a305d75fe/image.png" /></p>
<p>🧠 설명:</p>
<p>사용자가 앱에서 API 호출 → Lambda → DynamoDB에 데이터 저장</p>
<p>DynamoDB Streams를 통해 데이터 변경 이벤트 자동 트리거</p>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<p>Amazon DynamoDB = 완전관리형 NoSQL 데이터베이스</p>
<p>장점: 서버리스, 자동 확장, 고성능, 저지연, 무제한 확장성</p>
<p>구성 요소: Table, Item, Attribute, Index</p>
<p>현업 활용: IoT, 로그 저장, 세션 관리, 실시간 애플리케이션, 서버리스 백엔드</p>
<p>👉 한마디로,
“DynamoDB는 서버 관리가 필요 없는 초고속 NoSQL 데이터베이스” 입니다.</p>