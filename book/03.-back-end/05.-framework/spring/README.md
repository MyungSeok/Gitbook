# Spring

## Framework vs Library

가장 크게는 제어의 흐름이 다르며  
`Framework` 는 사용자의 코드가 프레임워크에 사용되는 것이고  
`Library` 는 사용자에 코드에 의해 소비되는 것이다.

Framework 는 `IoC` 개념이 적용되어야 하며 이는 특정의 프로세스를 프레임워크가 처리 가능하도록 제어를 넘김으로써 _**클라이언트 코드가 라이브러리의 메소드를 호출해서 사용하는 것**_ 을 의미합니다.

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
> http://isstory83.tistory.com/m/91