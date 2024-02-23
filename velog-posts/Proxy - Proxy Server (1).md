<blockquote>
<h2 id="proxy-or-proxy-server">Proxy Or Proxy Server</h2>
</blockquote>
<ul>
<li><span style="background-color: yellow;"><strong>Proxy</strong></span> : <span style="color: green;"><strong>대리(행위)</strong></span>를 의미하는 단어</li>
<li><span style="background-color: yellow;"><strong>Proxy Server</strong></span> : 클라이언트(Client)와 서버(Server) 관점에서 <span style="color: green;">중간에 대신 요청을 처리</span>한다하여 <span style="color: green;"><strong>클라이언트(Client)와 서버(Server)의 중계자 역할을 갖는 것</strong></span>을 의미한다.
<img alt="" src="https://velog.velcdn.com/images/gayeong39/post/320c5331-2617-4b87-bc5b-23348d14fb7c/image.png" /></li>
</ul>
<blockquote>
<h2 id="proxy-server을-사용하면-좋은-점">Proxy Server을 사용하면 좋은 점</h2>
</blockquote>
<h3 id="1-보안">1. 보안</h3>
<ul>
<li>클라이언트에서 <span style="color: green;">서버의 IP주소를 숨길 수 있기 때문에(=서버의 익명성) 프록시 서버로 통한 보안 향상</span>된다.
<img alt="" src="https://velog.velcdn.com/images/gayeong39/post/eab8cad8-b06b-4a9e-afed-540ead4d203a/image.png" /></li>
</ul>
<p><img alt="" src="https://velog.velcdn.com/images/gayeong39/post/361dc827-b7ba-441e-b318-726fd020a297/image.png" /></p>
<ul>
<li>위의 그림처럼 client가 특정 서버에 요청을 할 때 자신의 IP주소도 같이 전달이 되게 되는데, proxy server를 사용하면 자신 IP주소 대신 proxy server 주소가 요청을 보내는 것처럼 보이므로 자신의 IP주소를 외부에서 볼 수 없게 된다.</li>
</ul>
<h3 id="2-캐시-사용으로-빠른-속도">2. 캐시 사용으로 빠른 속도</h3>
<ul>
<li>proxy server은 <span style="color: green;">요청된 내용을 cache에 저장</span>한다.</li>
<li>cache에 존재하는 요청 내용이라면, 서버를 거치는 시간이 절약되기 때문에 <span style="color: green;">전송 시간이 빨라진다.</span></li>
<li>불필요한 외부와의 연결을 하지 않아도 됨으로 <span style="color: green;">외부와의 트래픽도 줄일 수 있게 된다.</span>
<img alt="" src="https://velog.velcdn.com/images/gayeong39/post/bf978a79-3d9b-44b7-bdbe-10a544c18c90/image.png" /></li>
</ul>
<h3 id="3-접속-우회">3. 접속 우회</h3>
<ul>
<li>1.보안 측면에서 말한 것과 같이 자신의 IP를 숨길 수 있기 때문에 <span style="color: green;">IP를 통해 접속을 감지하는 사이트를 프록시 서버를 통해 우회</span>할 수 있다. (client의 IP를 숨기기 위해 여러 proxy server를 계속 경유할 수도 있음)
<img alt="" src="https://velog.velcdn.com/images/gayeong39/post/2ed02a7b-a1b6-4836-b4c3-2e88aacb9d9a/image.png" /></li>
</ul>
<h3 id="4-로그-기록-관리">4. 로그 기록 관리</h3>
<ul>
<li>proxy server를 통해 client 기록을 관리할 수 있다. (<span style="color: green;">연결된 client 정보를 제어</span>)</li>
<li>요청할 server에게는 proxy server을 통해 IP를 숨겼음으로 개인정보 보호가 된다.</li>
<li>proxy server에겐 <span style="color: green;">client 정보가 남아있다.</span> (client가 proxy server에게 요청을 보냈으니까 &quot;어디 서버로 보내줘&quot;)</li>
<li>proxy server가 가진 client 정보로는 해당 client가 <span style="color: green;">&quot;어디에 얼마나 오래 접속했는가?&quot;</span></li>
<li>proxy server는 <span style="color: green;">방문할 수 있는 웹사이트를 제한</span>할 수 있다.</li>
</ul>
<blockquote>
<h2 id="forward-proxy">Forward Proxy</h2>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/gayeong39/post/9e1ca901-5632-4605-8081-b0194c0b27fe/image.png" /></p>
<ul>
<li>Forward Proxy는 <span style="color: green;">클라이언트들 앞에 위치</span>하며, 클라이언트로부터의 요청을 <span style="color: green;">Proxy Server가 대신 요청을 전달하고, 인터넷을 통해 외부 Server로 부터 데이터를 가져온다.</span></li>
<li>Proxy Server에 바로 연결하기 보단 <span style="color: green;">VPN</span>을 사용해 악위적인 Proxy Server에 연결되어 정보를 탈취하는 것을 막아 <span style="color: green;">가상 네트워크로 정보를 모두 암호화하여 전달</span>하기도 한다.</li>
<li><span style="color: green;">Forward Proxy는 클라이언트 대신 Server에 요청을 전달해주기 때문에 요청받는 Server는 실제 클라이언트가 누군지 알 수 없다.</span></li>
</ul>
<blockquote>
<h2 id="reverse-proxy">Reverse Proxy</h2>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/gayeong39/post/86563c75-5c6e-44a2-ab8f-e840f6176084/image.png" /></p>
<ul>
<li>Reverse Proxy는 <span style="color: green;"> Web Server/WAS 앞에 위치</span>하며, 내부망에서 <span style="color: green;">Proxy Server와 내부망 Server가 통신하여 인터넷을 통해 요청이 들어오면 Proxy Server가 받아 요청/응답처리</span>를 해준다.</li>
<li><span style="color: green;">클라이언트가 요청을 할 때 해당 Web Server에 요청하는 것이 아니라 Proxy Server에 요청하기 때문에 클라이언트는 Web Server의 정보를 알 수가 없다.</span></li>
<li>Reverse Proxy는 클라이언트로부터의 요청들을 어느 Server에 보낼지 결정하는 <span style="color: green;">라우팅 기능</span>과 한 Server에 부하가 오지 않도록 요청을 분산시켜주는 <span style="color: green;">로드밸런싱</span>
기능도 제공한다.</li>
<li>특히, 기업에서의 네트워크 환경은 <span style="color: green;">내부 네트워크(WAS, DBMS)</span>와 외부 네트워크 사이에 존재하는 <span style="color: green;">DMZ</span>라고 불리는 구간이 존재한다.</li>
<li>DMZ에서 Mail Server, Web Server 등 외부 서비스를 제공하는 Server가 위치하게 되는데, 실제 Reverse Proxy는 DMZ에 두고 실제 서비스 Server는 내부망에 위치시킨다.
<img alt="" src="https://velog.velcdn.com/images/gayeong39/post/bb5a41bd-714d-4af3-a2d8-a34162b7a2d8/image.png" /></li>
</ul>
<ol>
<li>Web Server은 클라이언트로부터 HTTP 요청 받음 </li>
<li>Web server은 클라이언트 요청을 WAS(내부망)에 보냄 </li>
<li>WAS는 관련된 Servelt을 메모리에 올려 Web.xml의 정보를 참조하여 Thread를 생성 </li>
<li>HttpServletRequest, HttpServletResponse 객체를 생성하여 Servlet에게 전달 </li>
<li>해당 Thread는 Servlet의 Service() 호출 </li>
<li>Service()는 doGet() or doPost() 호출 -&gt; 데이터 조회 </li>
<li>doGet() or doPost()는 파라미터에 맞게 생성된 동적 페이지를 Response 객체에 담아 WAS에 전달 </li>
<li>WAS는 Response 객체를 HttpResponse 형태로 바꿔서 Web Server에 전달  9. 해당 Thread는 종료 </li>
<li>HttpServletRequest, HttpServletResponse 객체 제거</li>
</ol>
<blockquote>
<h3 id="정리">정리</h3>
<p>&quot;일단, 정리를 하긴 했는데 부족한 부분이나 빠진 부분이 존재할지도 모른다. (더 정리해야하는 부분은 추후에 보완 예정) 또, 이 내용을 작성하면서 WEB SERVER와 WAS이 무엇이고, 어떻게 다른지도 정리해야겠다는 생각이 들었다. 다음 이론 포스트는 WEB SERVER와 WAS에 다룰 예정이다.&quot;</p>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/gayeong39/post/7ca1ca2e-8eed-4e32-8132-86cffec50180/image.png" />
  
<span style="font-size: 8pt;">이미지 출처 : <a href="https://m.post.naver.com/viewer/postView.naver?volumeNo=34803973&amp;memberNo=2953261">https://m.post.naver.com/viewer/postView.naver?volumeNo=34803973&amp;memberNo=2953261</a></span></p>
