# Linux

## nslookup

nslookup 명령어는 _**네임 서버 관련 조회**_를 할 수 있는 명령어이다.  
_**서버의 네트워크가 살아있는지 확인하는 용도**_로 사용한다.

```bash
$ nslookup IP
```

```bash
$ nslookup DOMAIN
```

## telnet

_**서버 네트워크가 살아있는지 확인하는 용도로 많이 사용**_ 한다.

```bash
$ telnet IP [PORT]
```

```bash
$ telnet DOMAIN [PORT]
```

## service

리눅스 상에 서비스로 등록되어 있는 목록을 가져온다.

```bash
# service --status-all
```

리눅스 상에 서비스를 기동 혹은 중지 시킨다.

```bash
# service SERVICE_NAME start
```

```bash
# service SERVICE_NAME restart
```

```bash
# service SERVICE_NAME stop
```

