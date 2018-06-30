# CLI

## Version

### 버전 확인

```bash
$ docker version
$ docker --version
$ docker version
```

### 정보 확인

```bash
$ docker info 
```

## Image

### 이미지 찾기

```bash
$ docker search IMAGE
```

### 이미지 다운

```bash
$ docker pull IMAGE[:TAG]
```

### 이미지 목록

```bash
$ docker image ls
```

### 이미지 삭제 

```bash
$ docker rmi IMAGE[:TAG]
```

## Container

### 컨테이너 생성 

```bash
$ docker run [OPTIONS] IMAGE[:TAG|@DIGEST] [COMMAND] [ARG...]
```

{% tabs %}
{% tab title="Case 1" %}
```bash
$ docker run -it --name ubuntu_container ubuntu /bin/bash
```

ubuntu 이미지를 컨테이너로 생성

* ubuntu 이미지를 컨테이너로 생성 
* `--name` 
  * 컨테이너의 이름을 지정 
* `-i`\(interactive\) 
  * 표준 입력\(stdin\)을 활성화 
  * 컨테이너와 연결\(attach\)되어 있지 않더라도 표준 입력을 유지합니다. 
  * 보통 이 옵션을 사용하여 Bash에 명령을 입력합니다.
* `-t`\(Pseudo-tty\) 
  * TTY 모드 
  * Bash Shell 사용하려면 필요한 옵션 
  * 이 옵션을 설정하지 않으면 명령을 입력할 수는 있지만 셸이 표시되지 않습니다.
* `-d` \(detached\) 
  * 데몬 모드 
  * 컨테이너가 백그라운드로 동작 된다
* `/bin/bash` 쉘을 이용하여 입출력을 할 수 있다.
{% endtab %}
{% endtabs %}

### 컨테이너 목록 

```bash
$ docker container ls [option]       # running
$ docker container ls --all          # all
$ docker container ls -aq            # all and quite mode 
```

### 컨테이너 기동 

```bash
$ docker start CONTAINER
```

### 컨테이너 재시작 

```bash
$ docker restart CONTAINER
```

### 컨테이너 접속 

```bash
$ docker attach CONTAINER
```

### 컨테이너 내부 명령 실행 

```bash
$ docker exec CONTAINER COMMAND [ARG...]
```

{% hint style="info" %}
Docker 를 컨테이너로 진입 후 exit 명령어로 컨테이너를 빠져 나오면 컨테이너가 종료되기 때문에 이에 대해 사용한다.
{% endhint %}

{% tabs %}
{% tab title="Case 1" %}
```bash
$ docker exec -it CONTAINER /bin/bash
```

CONTAINER 이름을 가진 컨테이너에 `/bin/bash` 쉘을 사용한다.  
`exit` 명령어로 Shell \(컨테이너\) 을 빠져 나와도 컨테이너가 종료되지 않는다.
{% endtab %}
{% endtabs %}

### 컨테이너 삭제 

```bash
$ docker rm CONTAINER
```

