# Spring Boot

## Linux Deploy Shell Script

### start.sh

앱을 시작하고 해당 _**PID**_ 를 파일에 저장한다.

```bash
#!/bin/bash
java -jar myapp.jar & echo $! > ./pid.file &
```

### stop.sh

저장된 _**PID**_ 를 사용하여 앱을 중지 한다.

```bash
#!/bin/bash
kill $(cat ./pid.file)
```

{% hint style="info" %}
참고 경로   
[https://code.i-harness.com/ko/q/195154c](https://code.i-harness.com/ko/q/195154c)
{% endhint %}



