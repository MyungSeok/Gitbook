# 03. Network

## 다이제스트 (Digest)

과거에 DB 에 저장되어 있는 비밀번호와 사용자가 입력한 값을 직접 비교하는 프로세스가 일반적이였으나 보안이슈로 인하여 사용자의 비밀번호를 암호화하는 대표적인 방법으로 암호화 해시 함수 (Cryptographic Hash Function) 가 있다.

일반적으로 사용자가 입력한 비밀번호는 암호화 해시 함수를 거쳐 다이제스트 (Digest) 형태로 저장된다.

_**다이제스트 (Digest) 란 해시 함수라는 수학적인 연산을 통해 암호화된 메시지를 의미한다.**_

암호화 해시 함수의 특징은 _**단방향**_ 이라서 역으로 추적이 거의 불가능하다.

대표적인 해시 함수는 `MD5` `SHA-1` `SHA-256` 등이 있다.

> ### 참고자료
> <http://www.itworld.co.kr/news/94202>

## TCP/UDP 포트 목록

기본적으로 권고되는 기본포트는 다음과 같으며 이는 IANA 의 권고안으로 구성된다.  
자주 사용되는 포트는 다음과 같다.

| PORT | 설명 | TCP | UDP |
| :--- | :--- | :--- | :--- |
| 20 | FTP \(파일 전송 프로토콜\) - 데이터 포트 | O |  |
| 21 | FTP - 제어포트 | O |  |
| 22 | SSH \(다른 FTP 프로그램의 의해서 SFTP의 기본 포트로 설정되는 경우가 있어 충돌이 난다\) | O |  |
| 23 | Telnet  | O |  |
| 25 | SMTP - 이메일 전송에 사용 | O |  |
| 80 | HTTP - 웹 페이지 전송 | O |  |
| 443 | HTTPS - SSL 위의 HTTP의 암호화 전송 | O |  |
| 990 | SSL 위의 FTP의 암호화 전송 | O |  |

## OSI 7 Layer

![OSI 7 계층](/img/A040.png)

|계층|이름|장비|대표 프로토콜|설명|
|--|--|--|--|--|
|7계층|서비스 제공|DHCP, DNS, FTP, HTTP|응용 계층 (Application)|사용자와 상호작용 하는 응용 프로그램 이다.<br>Chrome, FF, Safari 등과 같은 응용프로그램이 대표적이다.|
|6계층|표현 계층 (Presentation)|포맷 변환|JPEG, MPEG, SMB, AFP|데이터를 안전하게 보호하기 위하여 암호화 및 복호화를 하는 계층|
|5계층|세션 계층 (Session)|규칙 제어|SSH, TLS|세션을 만들고 설정하는 기능을 담당|
|4계층|전송 계층 (Transport)|게이트웨이|TCP, UDP, ARP|데이터의 전송을 조율하며 용량과 속도 및 목적지 등을 처리한다.<br>대표적으로는 전송 제어 프로토콜(TCP) 이 인터넷 프로토콜 (IP) 위에 구축이 되는데 이를 TCP/IP 라고 한다.|
|3계층|네트워크 계층 (Network)|라우터|IP, ICMP, IGMP|라우팅 기능을 제공하는 계층<br>IP가 여기서 작동한다.|
|2계층|데이터 링크 계층 (Data Link)|브릿지, 스위치|MAC, PPP|매체 접근 제어 (MAC) 계층으로 대부분의 스위치가 이 계층에서 동작된다. |
|1계층|물리 계층 (Physical)|허브, 리피터|Ethernet, RS-232C|시스템의 전기적, 물리적 표현을 나타내는 계층<br>케이블의 연결 혹은 플러그 상태를 점검 가능하다.|

![네트워크 계층 동작](/img/A041.png)

> ### 참고자료
> <https://kimdongwook.tistory.com/entry/OSI-7계층>  
> <http://www.ciokorea.com/news/36536>  
> <http://blog.naver.com/PostView.nhn?blogId=hostinggodo&logNo=220708841767>  
> <http://blog.naver.com/PostView.nhn?blogId=demonicws&logNo=40117378644>

## 네트워크 스위치 (NetWork Switch)

|Switch|기능|
|:--|:--|
|L2|MAC Address 를 읽어 스위칭 작업을 한다. <br> 라우팅이 불가능 하다.|
|L3|IP 정보를 읽어 스위칭을 한다.|
|L4|Port 번호 (TCP / UDP) 를 보고 스위칭을 한다. <br> HTTP : 80 <br> HTTPS : 444 <br> FTP : 21, 22|
|L7|어플리케이션 경로를 보고 스위칭을 한다. (도메인 이후 경로)|

> 각 스위치 장비는 자기보다 낮은 스위치의 기능까지 소화가 가능하다. (L7은 L4, L3, L2 영역까지 커버 가능)

## 가상 네트워크 (virtual Network)

Virtual Box, VM Ware 같은 가상머신 프로그램을 이용하여 Host (로컬 PC) 내에 가상 네트워크를 구성할 수 있다.

구성 가능한 가상 네트워크의 종류는 다음과 같다.

![가상 네트워크 구성](/img/A022.png)

## Host-Only

* 외부와 단절된 내부 네트워크를 구축하는 것
* _**구성된 가상머신들끼리만 통신이 가능**_

## NAT (Network Address Translation)

* _**Host PC 로부터 IP를 할당받아 가상머신 프로그램이 자체 DHCP 서버를 띄워 내부 네트워크 대역 할당 및 통신을 한다.**_
* Host PC 를 통해 외부 네트워크와 통신이 가능하다.

## Bridge

* _**공유기로부터 IP 를 할당 받아 호스트와 동일한 네트워크 대역의 IP 를 갖게 된다.**_
* 공유기를 통해 외부 네트워크와 통신이 가능하다.

> ### 참고자료
> <http://developerin.tistory.com/18>

## DHCP (Dynamic Host Configuration Protocal) 서버

Host PC 에서 보유하고 있는 IP 를 유동적으로 관리하는 프로토콜이다.  
_**IP 자동 할당과 분배의 기능**_을 담당한다.

## 프록시 환경 (Proxy) 환경

프록시 서버 (Proxy Server) 란 _**중계서버**_ 이다.

### 순방향 프록시 (Forward Proxy)

* 내부에서 외부로 접근
* Proxy Server 에서 IN/OUT 바운드 패킷에 대한 보안정책 (Content Filtering) 을 적용할 수 있다.
* Proxy Server 내부에 Cache 를 유지하며 이미 한번 통신한 외부 서버의 이미지, 파일, 그 외정보들을 저장할 수 있다.
  * Cache 용도로 사용한다.

![순방향 프록시](/img/A023.png)

### 역방향 프록시 (Reverse Proxy)

* 외부에서 내부로 접근
* 외부 사용자는 내부망에 대한 서버의 존재를 모르기 때문에 Reverse Proxy 서버에 들어오는 모든 접속은 Reverse Proxy 에 매핑되는 내부 서버의 정보를 알고 요청을 넘겨준다.
* Proxy 서버가 내부 서버의 정보를 알고 있으므로 로드 밸런싱을 통해 부하 여부에 따라 요청을 분배할 수 있다.

![역방향 프록시](/img/A024.png)

대부분 `nginx` 와 같은 Web Server 에서 설정한다.

> ### 참고자료
> <https://medium.com/sjk5766/nginx-reverse-proxy-사용하기-e11e18fcf843>