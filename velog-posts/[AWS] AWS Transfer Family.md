<h1 id="🔁-aws-transfer-family-정리">🔁 AWS Transfer Family 정리</h1>
<hr />
<h2 id="1️⃣-aws-transfer-family란">1️⃣ AWS Transfer Family란?</h2>
<p>AWS Transfer Family는
기존의 SFTP, FTPS, FTP 같은 파일 전송 프로토콜을 AWS 클라우드(S3, EFS) 와 직접 연결해주는 관리형 파일 전송 서비스입니다.</p>
<p>👉 쉽게 말해,
“기존 기업 시스템의 FTP 서버를 AWS로 옮길 수 있게 해주는 서비스” 입니다.</p>
<hr />
<h2 id="2️⃣-주요-특징">2️⃣ 주요 특징</h2>
<table>
<thead>
<tr>
<th>특징</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>☁️ <strong>완전관리형 서비스</strong></td>
<td>FTP 서버 구축, 보안 설정, 네트워킹 관리 불필요</td>
</tr>
<tr>
<td>🔐 <strong>보안 통합</strong></td>
<td>IAM, KMS, VPC, Security Group과 연동 가능</td>
</tr>
<tr>
<td>🧩 <strong>프로토콜 호환성</strong></td>
<td>SFTP(SSH), FTPS(TLS), FTP 지원</td>
</tr>
<tr>
<td>📂 <strong>AWS 스토리지 통합</strong></td>
<td>전송된 파일을 Amazon S3 또는 EFS에 자동 저장</td>
</tr>
<tr>
<td>🕹 <strong>운영 자동화</strong></td>
<td>파일 업로드/다운로드 이벤트 트리거로 Lambda 자동 실행</td>
</tr>
<tr>
<td>💰 <strong>비용 효율적</strong></td>
<td>서버 유지보수 없이 사용량 기반 과금</td>
</tr>
</tbody></table>
<hr />
<h2 id="3️⃣-아키텍처-시각화">3️⃣ 아키텍처 시각화</h2>
<pre><code class="language-mermaid">flowchart TD
    A[&quot;👤 사용자 / 파트너 시스템&quot;] --&gt; B[&quot;AWS Transfer Family (SFTP / FTPS / FTP)&quot;]
    B --&gt; C[&quot;Amazon S3 (파일 저장)&quot;]
    B --&gt; D[&quot;Amazon EFS (파일 시스템 연동)&quot;]
    C --&gt; E[&quot;AWS Lambda (자동 처리 트리거)&quot;]
    E --&gt; F[&quot;Amazon SNS / EventBridge (알림 및 워크플로우)&quot;]</code></pre>
<img alt="image" height="1008" src="https://github.com/user-attachments/assets/0e944ffa-297c-4180-a093-fd2a577d2e67" width="996" />


<p>🧠 설명:
사용자는 기존의 SFTP 클라이언트로 접속하지만,
실제 파일은 AWS 내부의 S3 또는 EFS에 안전하게 저장됩니다.</p>
<hr />
<h2 id="4️⃣-주요-사용-사례">4️⃣ 주요 사용 사례</h2>
<table>
<thead>
<tr>
<th>시나리오</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>🏢 <strong>레거시 시스템 연동</strong></td>
<td>기존 온프레미스 FTP 서버를 AWS로 이전</td>
</tr>
<tr>
<td>📦 <strong>파트너 간 데이터 교환</strong></td>
<td>외부 협력사와 SFTP로 파일 주고받기</td>
</tr>
<tr>
<td>🧾 <strong>회계/금융 데이터 송수신</strong></td>
<td>거래 데이터, 보고서 등 민감한 데이터 전송</td>
</tr>
<tr>
<td>🧠 <strong>자동화된 데이터 파이프라인</strong></td>
<td>S3에 파일 업로드 → Lambda → Glue ETL → Redshift 분석</td>
</tr>
</tbody></table>
<hr />
<h2 id="5️⃣-transfer-family--s3lambda-자동화-흐름">5️⃣ Transfer Family + S3/Lambda 자동화 흐름</h2>
<pre><code class="language-mermaid">sequenceDiagram
    participant User as 외부 사용자
    participant Transfer as AWS Transfer Family
    participant S3 as Amazon S3
    participant Lambda as AWS Lambda
    participant Glue as AWS Glue

    User-&gt;&gt;Transfer: SFTP 파일 업로드
    Transfer-&gt;&gt;S3: 파일 저장
    S3--&gt;&gt;Lambda: S3 이벤트 트리거
    Lambda-&gt;&gt;Glue: ETL 작업 시작
    Glue--&gt;&gt;S3: 변환된 데이터 저장</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/b559436c-0a5d-488b-bc3d-55320ec3567a/image.png" /></p>
<hr />
<h2 id="6️⃣-보안-통합-포인트">6️⃣ 보안 통합 포인트</h2>
<table>
<thead>
<tr>
<th>보안 항목</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td><strong>IAM</strong></td>
<td>사용자 인증 및 접근 제어</td>
</tr>
<tr>
<td><strong>VPC</strong></td>
<td>내부망 전송 구성 (Private Endpoint 지원)</td>
</tr>
<tr>
<td><strong>KMS</strong></td>
<td>데이터 암호화 관리</td>
</tr>
<tr>
<td><strong>CloudWatch Logs</strong></td>
<td>전송 이벤트 로그 및 모니터링</td>
</tr>
<tr>
<td><strong>AWS Secrets Manager</strong></td>
<td>자격 증명(비밀번호, 키) 안전 관리</td>
</tr>
</tbody></table>
<hr />
<h2 id="7️⃣-현업-활용-사례">7️⃣ 현업 활용 사례</h2>
<h3 id="🏦-금융권--공공기관">🏦 금융권 / 공공기관</h3>
<p>내부망 기반 SFTP 서버를 AWS로 이전해 보안성 강화</p>
<h3 id="🏭-제조업--iot-데이터-교환">🏭 제조업 / IoT 데이터 교환</h3>
<p>공장 데이터 로그를 SFTP로 전송 → AWS Glue 분석</p>
<h3 id="🧩-미디어-업로드-파이프라인">🧩 미디어 업로드 파이프라인</h3>
<p>협력사 영상 업로드 → S3 저장 → Lambda로 자동 처리</p>
<hr />
<h2 id="✅-정리">✅ 정리</h2>
<p>AWS Transfer Family = AWS용 관리형 파일 전송 서비스 (SFTP/FTPS/FTP)</p>
<p>저장 대상: Amazon S3 또는 EFS</p>
<p>특징: 보안 통합, 서버 관리 불필요, 이벤트 기반 자동화 지원</p>
<p>현업 활용: 데이터 교환, 자동 파이프라인, 레거시 시스템 마이그레이션</p>
<p>👉 한마디로,
“AWS Transfer Family는 기존 FTP 서버를 AWS 클라우드로 옮겨주는 보안 강화형 파일 전송 서비스” 입니다.</p>