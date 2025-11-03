<p>⭐️⭐️⭐️⭐️⭐️</p>
<blockquote>
<p><a href="https://www.examtopics.com/discussions/amazon/view/84973-exam-aws-certified-solutions-architect-associate-saa-c03/">https://www.examtopics.com/discussions/amazon/view/84973-exam-aws-certified-solutions-architect-associate-saa-c03/</a>
Q0001
회사는 여러 대륙에 걸쳐 도시의 온도, 습도 및 대기압에 대한 데이터를 수집합니다. 회사가 매일 각 사이트에서 수집하는 데이터의 평균 볼륨은 500GB 입니다. 각 사이트에는 고속 인터넷 연결이 있습니다. </p>
<p>이 회사는 이러한 모든 글로벌 사이트의 데이터를 단일 Amazon S3 버킷에 최대한 빨리 집계하려고 합니다. 솔루션은 운영 복잡성을 최소화해야 합니다. </p>
<p>어떤 솔루션이 이러한 요구 사항을 충족합니까?</p>
</blockquote>
<p>(O) 
대상 S3 버킷에서 <strong>S3 Transfer Acceleration</strong> 을 켭니다. 
멀티파트 업로드를 사용하여 사이트 데이터를 <strong>대상 S3 버킷에 직접 업로드</strong>합니다.</p>
<p>설명: 
여러 글로벌 사이트의 데이터를 단일 Amazon S3 버킷에 최대한 빨리 집계하는 동시에 운영 복잡성을 최소화하려면 가장 적합한 솔루션은 옵션 A: 대상 S3 버킷에서 S3 전송 가속화를 설정하고 멀티파트 업로드를 사용하여 사이트 데이터를 대상 S3 버킷에 직접 업로드하는 것입니다. </p>
<p>요약하면 옵션 A는 여러 글로벌 사이트의 데이터를 단일 Amazon S3 버킷으로 신속하게 집계하는 가장 효율적이고 운영상 간단한 솔루션을 제공합니다. 
S3 Transfer Acceleration 및 멀티파트 업로드를 활용하여 회사는 복잡성을 최소화하면서 빠른 데이터 수집을 달성할 수 있습니다.</p>
<pre><code>A company collects data for temperature, humidity, and atmospheric pressure in cities across 
multiple continents. The average volume of data that the company collects from each site daily is 
500 GB. Each site has a high-speed Internet connection. 
The company wants to aggregate the data from all these global sites as quickly as possible in a 
single Amazon S3 bucket. The solution must minimize operational complexity. 
Which solution meets these requirements? 

A. Turn on S3 Transfer Acceleration on the destination S3 bucket. Use multipart uploads to directly 
upload site data to the destination S3 bucket. 
B. Upload the data from each site to an S3 bucket in the closest Region. Use S3 Cross-Region 
Replication to copy objects to the destination S3 bucket. Then remove the data from the origin S3 
bucket. 
C. Schedule AWS Snowball Edge Storage Optimized device jobs daily to transfer data from each 
site to the closest Region. Use S3 Cross-Region Replication to copy objects to the destination S3 
bucket. 
D. Upload the data from each site to an Amazon EC2 instance in the closest Region. Store the 
data in an Amazon Elastic Block Store (Amazon EBS) volume. At regular intervals, take an EBS 
snapshot and copy it to the Region that contains the destination S3 bucket. Restore the EBS volume 
in that Region. 
Answer: A </code></pre><hr />
<blockquote>
<p><a href="https://www.examtopics.com/discussions/amazon/view/84848-exam-aws-certified-solutions-architect-associate-saa-c03/">https://www.examtopics.com/discussions/amazon/view/84848-exam-aws-certified-solutions-architect-associate-saa-c03/</a>
Q0002 
회사는 독점 애플리케이션의 로그 파일을 분석할 수 있는 능력이 필요합니다. 
로그는 Amazon S3 버킷에 JSON 형식으로 저장됩니다. 
쿼리는 간단하고 주문형으로 실행됩니다. </p>
<p>솔루션 설계자는 기존 아키텍처에 대한 최소한의 변경으로 분석을 수행해야 합니다. 
솔루션 설계자는 최소한의 운영 오버헤드로 이러한 요구 사항을 충족하기 위해 무엇을 해야 합니까? </p>
</blockquote>
<p>(O) 
Amazon S3와 함께 Amazon Athena를 직접 사용하여 필요에 따라 쿼리를 실행합니다.</p>
<p>설명:
S3 에 쿼리하는 건 Athena. 
Athena 가 사용 가능한 모든 리전에서 Amazon Athena 를 사용하여 표준 SQL 로 Amazon S3 인벤토리를 쿼리할 수 있습니다.<br />Athena 로 JSON 쿼리 가능. 
Amazon Athena 를 사용하면 JSON 인코딩 값을 구문 분석하고, JSON 에서 데이터를 추출하고, 값을 검색하고, JSON 배열의 길이와 크기를 찾을 수 있습니다.</p>
<pre><code>A company needs the ability to analyze the log files of its proprietary application. The logs are 
stored in JSON format in an Amazon S3 bucket. Queries will be simple and will run on-demand. A 
solutions architect needs to perform the analysis with minimal changes to the existing architecture. 
What should the solutions architect do to meet these requirements with the LEAST amount of operational overhead? 

A. Use Amazon Redshift to load all the content into one place and run the SQL queries as needed. 
B. Use Amazon CloudWatch Logs to store the logs. Run SQL queries as needed from the Amazon 
CloudWatch console. 
C. Use Amazon Athena directly with Amazon S3 to run the queries as needed. 
D. Use AWS Glue to catalog the logs. Use a transient Apache Spark cluster on Amazon EMR to run 
the SQL queries as needed. 

Answer: C </code></pre><hr />
<blockquote>
<p><a href="https://www.examtopics.com/discussions/amazon/view/84838-exam-aws-certified-solutions-architect-associate-saa-c03/">https://www.examtopics.com/discussions/amazon/view/84838-exam-aws-certified-solutions-architect-associate-saa-c03/</a> 
Q0003 
회사는 AWS Organizations 를 사용하여 여러 부서의 여러 AWS 계정을 관리합니다. 관리 계정에는 프로젝트 보고서가 포함된 Amazon S3 버킷이 있습니다. 
회사는 이 S3 버킷에 대한 액세스를 AWS Organizations 의 조직 내 계정 사용자로만 제한하려고 합니다. 
최소한의 운영 오버헤드로 이러한 요구 사항을 충족하는 솔루션은 무엇입니까?</p>
</blockquote>
<p>(O) 
조직 ID에 대한 참조와 함께 aws PrincipalOrgID 전역 조건 키를 S3 버킷 정책에 추가합니다.</p>
<p>설명:
A(O) : aws:PrincipalOrgID 라는 새로운 조건 키를 권한 정책에 사용하여 조직 내의 계정에 해당하는 IAM 보안 주체(사용자 및 역할)만 리소스에 액세스할 수 있도록 합니다.</p>
<pre><code>A company uses AWS Organizations to manage multiple AWS accounts for different departments. 
The management account has an Amazon S3 bucket that contains project reports. The company 
wants to limit access to this S3 bucket to only users of accounts within the organization in AWS 
Organizations. 
Which solution meets these requirements with the LEAST amount of operational overhead? 
A. Add the aws PrincipalOrgID global condition key with a reference to the organization ID to the 
S3 bucket policy. 
B. Create an organizational unit (OU) for each department. Add the aws:PrincipalOrgPaths global 
condition key to the S3 bucket policy. 
C. Use AWS CloudTrail to monitor the CreateAccount, InviteAccountToOrganization, 
LeaveOrganization, and RemoveAccountFromOrganization events. Update the S3 bucket policy 
accordingly. 
D. Tag each user that needs access to the S3 bucket. Add the aws:PrincipalTag global condition 
key to the S3 bucket policy. 
Answer: A</code></pre><hr />
<blockquote>
<p><a href="https://www.examtopics.com/discussions/amazon/view/84980-exam-aws-certified-solutions-architect-associate-saa-c03/">https://www.examtopics.com/discussions/amazon/view/84980-exam-aws-certified-solutions-architect-associate-saa-c03/</a>
Q0004 
애플리케이션은 VPC 의 Amazon EC2 인스턴스에서 실행됩니다. 애플리케이션은 Amazon S3 버킷에 저장된 로그를 처리합니다. EC2 인스턴스는 인터넷 연결 없이 S3 버킷에 액세스해야 합니다. 
Amazon S3에 대한 프라이빗 네트워크 연결을 제공하는 솔루션은 무엇입니까?</p>
</blockquote>
<p>(O)
S3 버킷에 대한 게이트웨이 VPC 엔드포인트를 생성합니다.</p>
<p>설명1:
VPC-S3 간 인터넷을 통하지 않는 연결 = S3 VPC Gateway Endpoint. 정답은 A. 
설명2: 
VPC 종단점을 사용하면 공용 인터넷을 사용하는 대신 사설 네트워크를 사용하여 AWS 서비스에 연결할 수 있습니다.</p>
<pre><code>An application runs on an Amazon EC2 instance in a VPC. The application processes logs that are 
stored in an Amazon S3 bucket. The EC2 instance needs to access the S3 bucket without connectivity to the internet. 
Which solution will provide private network connectivity to Amazon S3? 
A. Create a gateway VPC endpoint to the S3 bucket. 
B. Stream the logs to Amazon CloudWatch Logs. Export the logs to the S3 bucket. 
C. Create an instance profile on Amazon EC2 to allow S3 access. 
D. Create an Amazon API Gateway API with a private link to access the S3 endpoint. 
Answer: A </code></pre><hr />
<blockquote>
<p><a href="https://www.examtopics.com/discussions/amazon/view/84981-exam-aws-certified-solutions-architect-associate-saa-c03/">https://www.examtopics.com/discussions/amazon/view/84981-exam-aws-certified-solutions-architect-associate-saa-c03/</a>
Q0005 
회사는 사용자 업로드 문서를 Amazon EBS 볼륨에 저장하는 단일 Amazon EC2 인스턴스를 사용하여 AWS 에서 웹 애플리케이션을 호스팅하고 있습니다. 더 나은 확장성과 가용성을 위해 이 회사는 아키텍처를 복제하고 다른 가용 영역에 두 번째 EC2 인스턴스와 EBS 볼륨을 생성하여 Application Load Balancer 뒤에 배치했습니다. 이 변경을 완료한 후 사용자는 웹 사이트를 새로 고칠 때마다 문서의 일부 또는 다른 하위 집합을 볼 수 있지만 모든 문서를 동시에 볼 수는 없다고 보고했습니다. 
솔루션 설계자는 사용자가 모든 문서를 한 번에 볼 수 있도록 무엇을 제안해야 합니까?</p>
</blockquote>
<p>(O)
두 EBS 볼륨의 데이터를 Amazon EFS 로 복사합니다. 새 문서를 Amazon EFS 에 저장하도록 
애플리케이션을 수정합니다. </p>
<p>설명1:・ 
EBS 와 EFS의 가장 큰 차이점 중 하나는 EBS는 단일 AZ안에서만 접근이 가능한 저장소인 반면, EFS 는 다중 AZ 안에서도 접근이 가능한 저장소라는 점입니다. 위 문제에서는 초기 단일 AZ 에서 운영하던 EC2 및 EBS를 복제한뒤 AZ를 2중화하여 멀티 EC2 및 EBS 시스템으로 구성하였지만, 각 AZ 내에서 공유되지 않는 EBS 저장소를 별도로 운영하였기때문에 고객들에게 일관성있는 데이터를 제공할 수 없었던 것으로 보입니다. 이는 각 AZ 의 EC2 인스턴스가 동일한 저장소를 공유하도록 함으로써 해결할 수 있을 것 같습니다. 초기 EBS 에 저장되어있던 데이터들을 일관성있게 보정하여 EFS 로 일회성 마이그레이션을 수행한뒤 EC2 어플리케이션 서버 인스턴스가 EBS가 아닌 EFS에 데이터를 저장하도록 변경하는 것이 바람직해보입니다. </p>
<p>설명2: 
Amazon EFS 는 AWS 클라우드에서 파일 스토리지를 제공합니다. Amazon EFS 를 사용하면 파일 시스템을 생성하고 파일 시스템을 Amazon EC2 인스턴스에 탑재한 다음 파일 시스템에서 
데이터를 읽고 쓸 수 있습니다. Network File System 버전 4.0 및 4.1(NFSv4) 프로토콜을 통해 VPC에 Amazon EFS 파일 시스템을 탑재할 수 있습니다. Amazon EFS Mount Helper와 함께 최신 Amazon Linux, Redhat 및 Ubuntu AMI에 있는 것과 같은 현재 세대 Linux NFSv4.1 클라이언트를 사용하는 것이 좋습니다. 지침은 amazon-efs-utils 도구 사용 단원을 참조하십시오. </p>
<p>이 프로토콜을 지원하는 Amazon EC2 Linux Amazon 머신 이미지(AMI) 목록은 NFS 지원을 
참조하십시오. 일부 AMI 의 경우 파일 시스템을 Amazon EC2 인스턴스에 탑재하려면 NFS 
클라이언트를 설치해야 합니다. 지침은 NFS 클라이언트 설치를 참조하십시오. 
여러 NFS 클라이언트에서 동시에 Amazon EFS 파일 시스템에 액세스할 수 있으므로 단일 연결 
이상으로 확장되는 애플리케이션이 파일 시스템에 액세스할 수 있습니다. 동일한 AWS 리전 내의 여러 가용 영역에서 실행되는 Amazon EC2 인스턴스는 파일 시스템에 액세스할 수 있으므로 많은 사용자가 공통 데이터 원본에 액세스하고 공유할 수 있습니다. </p>
<pre><code>A company is hosting a web application on AWS using a single Amazon EC2 instance that stores user-uploaded documents in an Amazon EBS volume. For better scalability and availability, the company duplicated the architecture and created a second EC2 instance and EBS volume in 
another Availability Zone, placing both behind an Application Load Balancer. After completing this change, users reported that, each time they refreshed the website, they could see one subset of their documents or the other, but never all of the documents at the same time. 
What should a solutions architect propose to ensure users see all of their documents at once? 

A. Copy the data so both EBS volumes contain all the documents． 
B. Configure the Application Load Balancer to direct a user to the server with the documents． 
C. Copy the data from both EBS volumes to Amazon EFS. Modify the application to save new documents to Amazon EFS． 
D. Configure the Application Load Balancer to send the request to both servers. Return each document from the correct server． 

Answer: C </code></pre><hr />
<blockquote>
<p><a href="https://www.examtopics.com/discussions/amazon/view/84875-exam-aws-certified-solutions-architect-associate-saa-c03/">https://www.examtopics.com/discussions/amazon/view/84875-exam-aws-certified-solutions-architect-associate-saa-c03/</a>
Q0006 
회사는 NFS 를 사용하여 온프레미스 네트워크 연결 스토리지에 대용량 비디오 파일을 저장합니다. 
각 비디오 파일의 크기 범위는 1MB 에서 500GB 입니다. 총 스토리지는 70TB 이며 더 이상 
증가하지 않습니다. 회사는 비디오 파일을 Amazon S3 로 마이그레이션하기로 결정합니다. 회사는 가능한 한 최소한의 네트워크 대역폭을 사용하면서 가능한 한 빨리 비디오 파일을 
마이그레이션해야 합니다. 
어떤 솔루션이 이러한 요구 사항을 충족합니까?</p>
</blockquote>
<p>(O)
AWS Snowball Edge 작업을 생성합니다. 온프레미스에서 Snowball Edge 장치를 받습니다. 
Snowball Edge 클라이언트를 사용하여 장치로 데이터를 전송합니다. AWS 가 데이터를 Amazon S3 로 가져올 수 있도록 디바이스를 반환합니다. </p>
<p>설명1:
가능한 한 최소한의 네트워크 대역폭을 사용하라 했으니 아예 오프라인에서 Snowball Edge 로 
올리는 게 맞음. 
AWS Snowball 및 AWS Snowball Edge 는 기존 저장소에서 네트워크 대역폭이 충분하지 않을 때, 
대용량 데이터 세트를 클라우드로 이전하는데 도움이 됩니다. 
Snowball 장치는 80TB, Snowball Edge 는 100TB 까지 한번에 이동 가능합니다.</p>
<p>설명2: 
Snowball 과 Snowball Edge 의 기본적인 차이점은 제공하는 용량입니다. Snowball은 총 50TB 또는 
80TB 를 제공하며 그 중 42TB 또는 72TB를 사용할 수 있고 Amazon Snowball Edge는 100TB를 
제공하며 그 중 83TB를 사용할 수 있습니다.</p>
<pre><code>A company uses NFS to store large video files in on-premises network attached storage. Each 
video file ranges in size from 1 MB to 500 GB. The total storage is 70 TB and is no longer growing. 
The company decides to migrate the video files to Amazon S3. The company must migrate the 
video files as soon as possible while using the least possible network bandwidth. 
Which solution will meet these requirements? 
A. Create an S3 bucket. Create an IAM role that has permissions to write to the S3 bucket. Use the 
AWS CLI to copy all files locally to the S3 bucket. 
B. Create an AWS Snowball Edge job. Receive a Snowball Edge device on premises. Use the 
Snowball Edge client to transfer data to the device. Return the device so that AWS can import the 
data into Amazon S3. 
C. Deploy an S3 File Gateway on premises. Create a public service endpoint to connect to the S3 
File Gateway. Create an S3 bucket. Create a new NFS file share on the S3 File Gateway. Point the 
new file share to the S3 bucket. Transfer the data from the existing NFS file share to the S3 File 
Gateway. 
D. Set up an AWS Direct Connect connection between the on-premises network and AWS. Deploy 
an S3 File Gateway on premises. Create a public virtual interface (VIF) to connect to the S3 File 
Gateway. Create an S3 bucket. Create a new NFS file share on the S3 File Gateway. Point the new 
file share to the S3 bucket. Transfer the data from the existing NFS file share to the S3 File Gateway. 
Answer: B</code></pre><hr />