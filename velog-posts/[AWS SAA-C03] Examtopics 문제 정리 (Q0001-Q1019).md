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