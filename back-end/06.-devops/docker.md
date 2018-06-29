---
description: '모든 하드웨어 사양을 가상화 시키는 VM Ware, VirtualBox 가 아닌 프로세스를 격리화 시켜서 사용하는 방식'
---

# Docker

## Docker 란 ?

호스트 OS 위에 게스트 OS 전체를 가상화 시키는 기존 방식과는 달리   
CPU 의 가상화 기술 \(HVM\) 을 이용한 KVM \(Kernel-based Virtual Machine\) 과 반가상화 \(Paravirtualization\) 방식의 Xen 방식으로 구성된다.  
Docker 는 _**프로세스를 격리**_ 시켜 하나의 독립된 OS 처럼 가상화 시키는 방법으로 사용된다.

![](../../.gitbook/assets/image.png)

Docker 에서는 이미지를 가지고 컨테이너로 구성하여 사용한다.

{% hint style="info" %}
_**이미지는 변하지 않으며 \(Immutable\) 특성을 가진다.  
컨테이너는 이미지를 실행한 상태로 추가되거나 변경되는 값은 컨테이너에 저장된다.**_
{% endhint %}

![](../../.gitbook/assets/image%20%281%29.png)

{% hint style="info" %}
**참고 자료**

* [초보를 위한 도커 안내서](https://subicura.com/2017/01/19/docker-guide-for-beginners-1.html) 
* [가장 빨리 만나는 Docker](http://pyrasis.com/docker.html)
{% endhint %}

 







