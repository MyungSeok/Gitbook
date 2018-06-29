---
description: Docker Command Line Interface
---

# CLI

## Info

### Version

```bash
$ docker version
$ docker --version
$ docker version
```

### Info

```bash
$ docker info
```

## Image

### Search

```bash
$ docker search IMAGE
```

### Pull

```bash
$ docker pull IMAGE[:VERION]
```

### List

```bash
$ docker image ls
```

## Container

### Create

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
* `--name` 옵션을 사용하여 ubuntu\_container 로 이름을 지정 
* `-i`\(interactive\) `-t`\(Pseudo-tty\) 옵션을 사용하며 `/bin/bash` 쉘을 이용하여 입출력을 할 수 있다.
{% endtab %}
{% endtabs %}

### List

```bash
$ docker container ls [option]       # running
$ docker container ls --all          # all
$ docker container ls -aq            # all and quite mode 
```



