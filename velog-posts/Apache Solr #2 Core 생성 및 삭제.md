<ol>
<li>Apache Solr Core 생성</li>
</ol>
<p>CMD 실행 후 Apache Solr가 설치되어 있는 디렉토리로 이동 후 Core 생성</p>
<ul>
<li>solr create -c corename</li>
</ul>
<pre><code>cd C:\dev\apachesolr\solr-8.11.2\bin
solr create -c test_core
</code></pre><p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/023876fe-b235-46f9-9c27-0381e92260d3/image.png" /></p>
<ol start="2">
<li>Apache Solr Admin Page 좌측에서 생성한 core name 확인</li>
</ol>
<ul>
<li>웹 브라우저 실행 후 localhost:8983 입력</li>
</ul>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/4b238296-29d7-4685-9eba-5c932d96117c/image.png" /></p>
<ol start="3">
<li>Apache Solr 설치 경로에서 server\solr\로 이동</li>
</ol>
<blockquote>
<ul>
<li>제가 설정한 Apache Solr 디렉토리
C:\dev\apachesolr\solr-8.11.2\server\solr</li>
</ul>
</blockquote>
<ul>
<li>아래 캡쳐화면과 같이 ..\server\solr\ 디렉토리에 생성한 core 폴더가 생성된 것을 확인 할 수 있습니다.</li>
</ul>
<p><img alt="" src="https://velog.velcdn.com/images/yjshin/post/5313a920-c877-4c72-8201-27404545f145/image.png" /></p>
<ol start="4">
<li>Apache Solr Core 삭제</li>
</ol>
<blockquote>
<ol>
<li>CMD 실행</li>
<li>Solr 설치된 경로\bin으로 디렉토리 이동</li>
<li>solr stop -all 명령어 실행</li>
<li>윈도우 탐색기 실행하여 삭제하려는 core 폴더를 삭제</li>
<li>solr start 명령어 실행하여 Solr를 활성화</li>
<li>Solr Admin Page에서 해당 Core 삭제 여부 확인</li>
</ol>
</blockquote>
<p>4-1 ~ 4-3. CMD 실행 → Solr 설치된 경로\bin으로 디렉토리 이동 →
solr stop -all 명령어 실행
<img alt="" src="https://velog.velcdn.com/images/yjshin/post/02454108-5011-4e51-bccc-5b6415d69a07/image.png" /></p>
<p>4-4. 윈도우 탐색기 실행하여 삭제하려는 core 폴더를 삭제
<img alt="" src="https://velog.velcdn.com/images/yjshin/post/3c498d14-1b75-49c7-be4b-6256cd6e277c/image.png" /></p>
<p>4-5. solr start 명령어 실행하여 Solr를 활성화
<img alt="" src="https://velog.velcdn.com/images/yjshin/post/923659be-a46e-4e65-a057-5eb0742e4f1b/image.png" /></p>
<p>※ Apache Solr Core 생성 및 삭제 참고 블로그 링크 : <a href="https://blog.naver.com/statp_r/222035412885">https://blog.naver.com/statp_r/222035412885</a></p>