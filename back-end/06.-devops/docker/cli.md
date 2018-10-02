---
description: Docker Command Line Interface
---

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

```bash
$ docker run -it --name ubuntu_container ubuntu /bin/bash
```

ubuntu 이미지를 컨테이너로 생성

* ubuntu 이미지를 컨테이너로 생성 
* `--name` 옵션을 사용하여 ubuntu\_container 로 이름을 지정 
* `-i`\(interactive\) `-t`\(Pseudo-tty\) 옵션을 사용하며 `/bin/bash` 쉘을 이용하여 입출력을 할 수 있다.

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

### 컨테이너 삭제 

```bash
$ docker rm CONTAINER
```

