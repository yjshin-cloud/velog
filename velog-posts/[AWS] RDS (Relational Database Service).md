<h1 id="🗄️-amazon-rds-relational-database-service-이해하기">🗄️ Amazon RDS (Relational Database Service) 이해하기</h1>
<h2 id="1️⃣-rds란">1️⃣ RDS란?</h2>
<p>Amazon RDS는 AWS에서 제공하는 관리형(Relational) 데이터베이스 서비스입니다.
즉, 직접 서버를 설치하고 DB를 운영할 필요 없이, 클릭 몇 번으로 데이터베이스를 생성하고 운영할 수 있습니다.</p>
<h3 id="👉-쉽게-말해-aws가-대신-설치·백업·패치·운영까지-해주는-데이터베이스-서버-라고-생각하면-됩니다">👉 쉽게 말해, “AWS가 대신 설치·백업·패치·운영까지 해주는 데이터베이스 서버” 라고 생각하면 됩니다.</h3>
<h2 id="2️⃣-지원하는-데이터베이스-엔진">2️⃣ 지원하는 데이터베이스 엔진</h2>
<p>RDS는 다양한 오픈소스 및 상용 DB 엔진을 지원합니다.</p>
<p>MySQL</p>
<p>PostgreSQL</p>
<p>MariaDB</p>
<p>Oracle (상용 라이선스 필요)</p>
<p>Microsoft SQL Server</p>
<p>Amazon Aurora (AWS가 자체 개발한 고성능 DB, MySQL/PostgreSQL 호환)</p>
<h2 id="3️⃣-rds의-주요-특징">3️⃣ RDS의 주요 특징</h2>
<p>⚡ 자동화</p>
<p>백업, 스냅샷, 패치, 장애 복구를 자동 처리</p>
<p>🛡️ 보안</p>
<p>VPC 내부 배치, 보안 그룹/네트워크 ACL, KMS 암호화 지원</p>
<p>📈 확장성</p>
<p>읽기 전용 복제(Read Replica)로 트래픽 분산</p>
<p>스토리지와 인스턴스 크기 확장 가능</p>
<p>🔄 고가용성 (Multi-AZ)</p>
<p>장애 시 자동으로 대기 인스턴스로 Failover</p>
<p>💸 비용 효율성</p>
<p>사용한 만큼 과금 (On-Demand, Reserved Instances)</p>
<h2 id="4️⃣-rds-아키텍처-개념도">4️⃣ RDS 아키텍처 개념도</h2>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/defab8af-20ff-46fe-8dea-be35bfbe2ec2/image.png" /></p>
<h2 id="5️⃣-rds-활용-사례">5️⃣ RDS 활용 사례</h2>
<p>🛒 쇼핑몰/웹서비스의 트랜잭션 데이터 관리</p>
<p>📊 데이터 분석용 저장소 (BI, 리포팅)</p>
<p>🧪 테스트/개발 환경에서 빠르게 DB 생성</p>
<p>🌍 글로벌 서비스에서 읽기 전용 Replica 로 다중 리전 분산</p>
<h2 id="6️⃣-rds를-시작하려면">6️⃣ RDS를 시작하려면?</h2>
<p>RDS 콘솔 → DB 인스턴스 생성</p>
<p>엔진(MySQL, PostgreSQL 등) 선택</p>
<p>버전, 인스턴스 타입, 스토리지 설정</p>
<p>VPC/Subnet 그룹 선택</p>
<p>DB를 퍼블릭/프라이빗 서브넷 중 어디에 둘지 결정</p>
<p>보안 그룹 설정</p>
<p>EC2(Web/App 서버)에서만 접근 가능하도록 인바운드 규칙 설정</p>
<p>백업/고가용성 설정</p>
<p>자동 백업 주기, Multi-AZ 여부 선택</p>
<p>애플리케이션에서 연결</p>
<p>RDS 엔드포인트 주소 + 포트 + 계정 정보 사용</p>
<h2 id="✅-정리">✅ 정리</h2>
<p>Amazon RDS는 운영 부담을 최소화하면서,</p>
<p>안정적이고 확장 가능한 관계형 데이터베이스를 제공하는 서비스입니다.</p>
<h3 id="👉-즉-개발자는-db-설치운영에-신경-쓰지-않고-비즈니스-로직-개발에만-집중할-수-있습니다">👉 즉, 개발자는 DB 설치/운영에 신경 쓰지 않고 비즈니스 로직 개발에만 집중할 수 있습니다.</h3>