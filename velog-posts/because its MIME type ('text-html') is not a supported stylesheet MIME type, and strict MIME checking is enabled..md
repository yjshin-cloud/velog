<blockquote>
<p>Failed to load resource: the server responded with a status of 404 () </p>
</blockquote>
<blockquote>
<p>because its MIME type ('text/html') is not a supported stylesheet MIME type, and strict MIME checking is enabled.</p>
</blockquote>
<p>css와 js를 제대로 적용이 안되는 현상 발생</p>
<p>Django Terminal에서도 아래와 같은 메시지 발생</p>
<blockquote>
<p>Not Found: /Project_App/static/css/test.css
Not Found: /Project_App/static/js/test.js</p>
</blockquote>
<p>아래와 같이 링크를 넣어서 Error 발생</p>
<pre><code>&lt;link rel=&quot;stylesheet&quot; href=&quot;static/css/test.css&quot;&gt;
&lt;script src=&quot;static/js/test.js&quot;&gt;&lt;/script&gt;</code></pre><p>경로 지정이 잘못되어 생기는 Error로 아래와 같이 설정하면
정상적으로 인식</p>
<pre><code>&lt;link rel=&quot;stylesheet&quot; href=&quot;/static/css/test.css&quot;&gt;
&lt;script src=&quot;/static/js/test.js&quot;&gt;&lt;/script&gt;</code></pre><ul>
<li>참고 블로그 링크 : <a href="https://csy7792.tistory.com/244">https://csy7792.tistory.com/244</a></li>
</ul>