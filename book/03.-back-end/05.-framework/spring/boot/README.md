# Spring Boot

## Spring Boot 기동

### Linux Deploy Shell Script

리눅스 환경에서 쉽게 관리를 위해 _**Shell Script**_ 형태로 만들어 두어 관리한다.

#### start.sh

앱을 시작하고 해당 _**PID**_ 를 파일에 저장한다.

```bash
#!/bin/bash
java -jar myapp.jar & echo $! > ./pid.file &
```

#### stop.sh

저장된 _**PID**_ 를 사용하여 앱을 중지 한다.

```bash
#!/bin/bash
kill $(cat ./pid.file)
```

> Reference
>
> [https://code.i-harness.com/ko/q/195154c](https://code.i-harness.com/ko/q/195154c)

#### Gradle 로 Spring Boot 기동

```bash
# gradle bootRun
```

> Reference
> <http://isstory83.tistory.com/m/91>