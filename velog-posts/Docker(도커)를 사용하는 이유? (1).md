<blockquote>
<p>Docker(도커)에 대한 이야기는 익히 자주 들어서 '공부해야지..!' 매번 다짐했지만 미루고 미루다가 이제서야 정리할 기회가 와서 정리해봅니다:) </p>
</blockquote>
<blockquote>
<h2 id="docker란">Docker란?</h2>
</blockquote>
<ul>
<li><span style="background-color: yellow;">컨테이너</span>라고 부르는 운영체제 수준의 <span style="background-color: yellow;">가상화 방식으로 소프트웨어를 배포</span>하는 방식을 사용하는 PaaS 제품이다.</li>
<li><h3 id="paasplatform-as-a-service-란-">PaaS(Platform as a Service) 란 ?</h3>
<ul>
<li><span style="border-bottom: 2px solid green;">애플리케이션, 데이터 단계만 사용자가 관리하는 서비스</span>를 의미한다.</li>
<li><span style="background-color: yellow;">도커</span>를 사용하면 <span style="border-bottom: 2px solid green;">다양한 개발 환경에서 컨테이너를 이용해 소프트웨어를 편하게 배포</span>할 수 있다.
<img alt="" src="https://velog.velcdn.com/images/gayeong39/post/99363290-900a-437e-8400-cdd068dafb28/image.png" /></li>
</ul>
</li>
</ul>
<blockquote>
<h2 id="docker을-사용하면-어떤-점이-좋을까">Docker을 사용하면 어떤 점이 좋을까?</h2>
</blockquote>
<ul>
<li><p>소프트웨어를 배포할 때 <span style="background-color: yellow;">&quot;배포의 어려움&quot;</span>이 존재한다.
<img alt="" src="https://velog.velcdn.com/images/gayeong39/post/8ffb6a58-bd49-4f67-97b7-7392e0d241d6/image.png" /></p>
</li>
<li><p>위의 그림과 같이 만약 소프트웨어A가 소프트웨어0 환경 버전이 3.0일때 작동하고, 소프트웨어B는 소프트웨어0 환경버전이 5.0일때 작동한다고 치자.</p>
</li>
<li><p>그렇게 되면 각각의 서버A/B에서는 소프트웨어A/B를 둘다 작동시킬 수 없을 것이다. (작동되는 환경 버전이 다르기 때문!)</p>
</li>
<li><p>위의 문제점을 해결할 수 있는게 바로 <span style="background-color: yellow;">Docker</span> 이다!
<img alt="" src="https://velog.velcdn.com/images/gayeong39/post/dfb22c8e-2c84-47a6-9830-1170216e566b/image.png" /></p>
</li>
</ul>
<blockquote>
<h2 id="container은-무엇일까">Container은 무엇일까?</h2>
</blockquote>
<ul>
<li>소프트웨어를 배포할 때 <span style="background-color: yellow;">필요한 코드, 라이브러리, 환경 설정 파일들을 한곳에 모아 격리시킨 후 실행 가능한 패키지로 만든 것</span>이다.</li>
<li>서로 격리되어 있기 때문에 충돌이 나지 않는다.</li>
<li>Container가 <span style="background-color: yellow;">동일한 운영체제 위에서 작동</span>하기 때문에 <span style="background-color: yellow;">격리된 서로 다른 Container들끼리 통신</span>을 주고받을 수 있다.</li>
<li>컨테이너가 동일한 운영체제 위에서 작동하면 <span style="background-color: yellow;">가상머신에 비해 리소스 소모량이 적으므로 더 효율적인 리소스 관리</span>가 가능하다.</li>
</ul>
<blockquote>
<h2 id="가상머신에-비해-리소스-소모량이-적은-이유는-무엇일까">가상머신에 비해 리소스 소모량이 적은 이유는 무엇일까?</h2>
</blockquote>
<h3 id="1-커널을-공유">1. 커널을 공유</h3>
<ul>
<li><h4 id="span-stylebackground-coloryellow컨테이너span"><span style="background-color: yellow;">컨테이너</span></h4>
<ul>
<li>컨테이너는 호스트 운영체제의 <span style="color: green;"> 커널을 공유(=추가적인 운영체제를 실행할 필요가 없다는 것을 의미)</span>한다.</li>
<li>커널을 위한 메모리와 CPU 리소스가 절약된다.</li>
</ul>
</li>
<li><h4 id="span-stylebackground-coloryellow가상머신span"><span style="background-color: yellow;">가상머신</span></h4>
<ul>
<li>가상머신은 각각 <span style="color: green;"> 자체 운영체제와 커널을 포함한 전체 시스템을 실행</span>해야 한다. </li>
<li>더 많은 메모리와 CPU 리소스를 소모하게 만듭니다.</li>
</ul>
</li>
</ul>
<h3 id="2-경량화된-가상화-계층">2. 경량화된 가상화 계층</h3>
<ul>
<li><h4 id="span-stylebackground-coloryellow컨테이너span-1"><span style="background-color: yellow;">컨테이너</span></h4>
<ul>
<li>운영체제 수준의 가상화를 사용하여 애플리케이션을 격리한다.</li>
<li><strong>경량화된 가상화 기술</strong>을 사용하여<span style="color: green;"> 더 적은 오버헤드를 발생</span>시킨다.</li>
</ul>
</li>
<li><h4 id="span-stylebackground-coloryellow가상머신span-1"><span style="background-color: yellow;">가상머신</span></h4>
<ul>
<li>하드웨어 수준의 가상화를 사용하여 전체 운영체제를 격리한다.</li>
<li><strong>하이퍼바이저</strong>와 같은 추가 계층이 필요하기 때문에 <span style="color: green;"> 더 많은 오버헤드가 발생</span>한다.</li>
</ul>
</li>
</ul>
<h3 id="3-빠른-시작종료-시간">3. 빠른 시작/종료 시간</h3>
<ul>
<li><h4 id="span-stylebackground-coloryellow컨테이너span-2"><span style="background-color: yellow;">컨테이너</span></h4>
<ul>
<li>매우 빠르게 시작되고 종료될 수 있다.</li>
<li><span style="color: green;"> 시스템 리소스를 더 효율적으로 사용</span>할 수 있게 해준다.</li>
</ul>
</li>
<li><h4 id="span-stylebackground-coloryellow가상머신span-2"><span style="background-color: yellow;">가상머신</span></h4>
<ul>
<li><span style="color: green;">전체 운영체제를 부팅하고 종료해야 하기 때문에</span> 시작 및 종료 시간이 컨테이너 방식에 비해 길다. </li>
<li>그렇기 때문에 <span style="color: green;">비효율적인 리소스 사용이 발생</span>할 수 있다.</li>
</ul>
</li>
</ul>
<h3 id="4-파일-시스템-및-이미지-관리">4. 파일 시스템 및 이미지 관리</h3>
<ul>
<li><h4 id="span-stylebackground-coloryellow컨테이너span-3"><span style="background-color: yellow;">컨테이너</span></h4>
<ul>
<li>계층화된 파일 시스템을 사용하여 이미지를 관리한다. </li>
<li><span style="color: green;">동일한 기본 이미지를 여러 컨테이너에서 공유하여 저장 공간을 절약</span>할 수 있다.</li>
</ul>
</li>
<li><h4 id="span-stylebackground-coloryellow가상머신span-3"><span style="background-color: yellow;">가상머신</span></h4>
<ul>
<li><span style="color: green;">각각 독립된 디스크 이미지를 사용해야 하기 때문에 저장 공간의 낭비</span>를 초래할 수 있다.</li>
</ul>
</li>
</ul>
<h3 id="5-네트워크-및-io-효율성">5. 네트워크 및 I/O 효율성</h3>
<ul>
<li><h4 id="span-stylebackground-coloryellow컨테이너span-4"><span style="background-color: yellow;">컨테이너</span></h4>
<ul>
<li><span style="color: green;">네트워크 및 I/O를 호스트 운영체제와 직접적으로 공유할 수 있어 효율적</span>이다. </li>
</ul>
</li>
<li><h4 id="span-stylebackground-coloryellow가상머신span-4"><span style="background-color: yellow;">가상머신</span></h4>
<ul>
<li><span style="color: green;">가상 네트워크 인터페이스와 가상 디스크를 사용해야 하기 때문에 추가적인 오버헤드를 발생</span>시킨다.</li>
</ul>
</li>
</ul>
<blockquote>
<h2 id="가상화에는-무엇이-있을까">가상화에는 무엇이 있을까?</h2>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/gayeong39/post/ccf08075-2130-479c-873a-7319733325db/image.png" /></p>
<h3 id="①-host호스트-가상화">① HOST(호스트) 가상화</h3>
<ul>
<li><span style="color: green;">운영체제를 설치한 후 hypervisor를 통해 가상머신을 만들고</span> <span style="background-color: yellow;">각 가상머신 내부에는 Guest OS가 설치</span>된다. <ul>
<li><span style="background-color: yellow;">Hypervisor</span> : 단일 물리 머신에서 다수의 가상 머신을 실행할때 활용하는 소프트웨어<ul>
<li>ex. 버츄얼 박스, VM WARE 등</li>
</ul>
</li>
</ul>
</li>
</ul>
<h3 id="②-hypervisor하이퍼바이저-가상화">② Hypervisor(하이퍼바이저) 가상화</h3>
<ul>
<li>호스트 가상화와 달리 <span style="background-color: yellow;">HOST OS를 필요로 하지 않은 방식</span>에 해당한다.</li>
<li>운영체제가 존재하지 않기 때문에 부팅시 가상머신을 선택하여 들어간다.</li>
<li><span style="background-color: yellow;">성능이 우수하지만, 초기설정이 복잡하고 관리가 어렵다.</span></li>
</ul>
<h3 id="③-container컨테이너-가상화">③ Container(컨테이너) 가상화</h3>
<ul>
<li>운영체제 위에 Container를 운영하기 위해 <span style="background-color: yellow;">필요한 Docker를 설치</span>한 후 다수의 Container를 통해 application을 실행한다.</li>
<li><span style="color: green;">Docker, Kubernetes(쿠버네티스)</span>는 Container 가상화 방식을 활용하는 소프트웨어이다.</li>
<li>Container간 격리가 되기 대문에 <span style="background-color: yellow;">다른 application에 영향을 주지 않고, 서로 다른 컴퓨팅 환경에서 application을 실행하는데 용이</span>하다.</li>
</ul>
<blockquote>
<h2 id="docker는-어떻게-구성되어-있지">Docker는 어떻게 구성되어 있지?</h2>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/gayeong39/post/83da9b67-134b-4b10-a589-614b24ffe7a6/image.png" /></p>
<h3 id="docker-cli도커-클라이언트">docker-cli(도커 클라이언트)</h3>
<ul>
<li>터미널같이 명령어 행으로 <span style="background-color: yellow;">dockerd API를 활용해 build, run, pull과 같은 명령을 작성</span>하는 곳이다.</li>
<li><span style="background-color: yellow;">dockerd와 통신</span>한다.</li>
</ul>
<h3 id="dockerd도커-데몬">dockerd(도커 데몬)</h3>
<ul>
<li><span style="background-color: yellow;">백그라운드에서 실행되는 데몬 프로세스</span>를 말한다.</li>
<li><span style="background-color: yellow;">docker API 요청을 수신하고 Docker 이미지, Container 등과 같은 Docker 관련 객체를 관리</span>한다.</li>
<li><span style="color: green;"><strong>데몬(demon)</strong></span><ul>
<li>운영체제에서 백그라운드에서 실행되는 프로그램(사용자와 직접 상호작용X)</li>
</ul>
</li>
</ul>
<h3 id="containerd컨테이너-런타임">containerd(컨테이너 런타임)</h3>
<ul>
<li><span style="background-color: yellow;">Container 실행과 관리에 필요한 기능을 수행</span>한다.</li>
<li>Container의 생명 주기를 모두 관리한다. <ul>
<li><span style="color: green;"><strong>생명 주기</strong></span> =&gt; Docker 이미지 전송, Container 실행, 스토리지, 네트워크를 포함.</li>
</ul>
</li>
<li>Container 실행만 담당하는 runc과 다른 역할을 하며 <span style="background-color: yellow;">고수준 Container Runtime</span>에 해당한다.</li>
</ul>
<h3 id="container-shim">container-shim</h3>
<ul>
<li><span style="background-color: yellow;">containerd와 runc 사이에 작동하는 중간 프로세스</span>이며, <span style="background-color: yellow;">중개자 역할</span>을 한다.</li>
<li><span style="background-color: yellow;">Container 실행을 조정</span>하는 역할을 한다.(-&gt; contianerd는 runc와 통신함으로 Container을 실행)</li>
</ul>
<h3 id="runc">runc</h3>
<ul>
<li><span style="background-color: yellow;">Container 실행과 관련된 작업</span>을 수행하는 <span style="background-color: yellow;">저수준 Container Runtime</span>이다.</li>
</ul>