# 하이퍼바이저 개념 정리


하이퍼바이저(hypervisor)는 호스트 컴퓨터에서 다수의 운영 체제(operating system)를 동시에 실행하기 위한 논리적 플랫폼을 말한다. 가상화 머신 모니터(virtual machine monitor) 또는 가상화 머신 매니저(virtual machine manager) 약어로 VMM라고 한다.

하나 이상의 가상머신(virtual machine)을 실행하는 컴퓨터가 “호스트(Host)”가 되고 각 가상 머신들은 “게스트(Guest)”가 된다.

하이퍼바이저는 게스트 운영 체제에 가상 운영 플랫폼을 제공하면서 게스트 운영 체제를 관리한다. 다양한 운영 체제의 여러 인스턴스가 가상화된 하드웨어 리소스를 공유할 수 있다. 예를 들면 Linux, Windows 및 mac OS 인스턴스는 모두 단일 물리적 x86 시스템에서 실행될 수 있다.

- 하이퍼바이저는 단일 하드웨어에서 여러 다른 가상 머신을 호스팅할 수있는 프로그램이다.
- 시스템에서 호스트 하드웨어의 프로세서, 메모리 및 리소스가 있는 것처럼 보이기 때문에 이러한 가상 머신 또는 운영 체제 각각은 자체 프로그램을 실행할 수 있다. 그러나 실제로 이러한 리소스를 가상 시스템에 할당하는 것은 하이퍼바이저이다.
- 실제로 하이퍼 바이저를 사용하면 여러 컴퓨터가 단일 컴퓨터 하드웨어에서 최적으로 작동하도록 할 수 있다.
- 하이퍼바이저는 서버에 있는 모든 물리적 장치에 액세스할 수 있다. 또한 메모리와 디스크에 액세스할 수 있다. 또한 가상 머신의 모든 측면과 부분을 제어할 수 있다.



## 하이퍼바이저 유형

하이퍼바이저에는 유형 1 또는 유형 2라는 두 가지 유형의 하이퍼 바이저가 있다. “Native”또는 “Bare-Metal” 하이퍼바이저라고도하는 유형 1 하이퍼바이저는 호스트 하드웨어에서 직접 실행되어 하드웨어를 제어하고 게스트 가상머신을 관리한다.

### Hypervisor TYPE 1

![image](https://user-images.githubusercontent.com/42468263/185088561-be227259-7dd6-4fbf-a843-01c62b3aadd9.png)

유형 1의 주요 이점은 가상 시스템 또는 게스트 운영 체제 중 하나의 문제가 하드웨어에서 실행 중인 다른 게스트 운영 체제에 영향을 미치지 않는다는 것이다.

**유형 1** 하이퍼 바이저에는 대표적으로 Xen, Oracle VM Server for SPARC, Oracle VM Server for x86, Microsoft Hyper-V 및 VMware의 ESX / ESXi가 있다.

### Hypervisor TYPE 2

![image](https://user-images.githubusercontent.com/42468263/185088865-45a81f84-50d8-4c06-9148-56679b57ce8f.png)

호스트 된 하이퍼 바이저라고도 하는 **유형 2** 하이퍼 바이저는 시스템의 다른 응용 프로그램과 마찬가지로 일반적인 OS에서 실행된다. 이 경우 게스트 OS는 호스트에서 프로세스로 실행되는 반면 하이퍼 바이저는 게스트 OS와 호스트 OS를 분리한다.

유형 2 하이퍼바이저는 운영에 있어 호스트 운영 체제에 전적으로 의존한다. 기본 운영 체제에서 실행되는 하이퍼 바이저가 안전하더라도 기본 운영 체제의 모든 문제는 전체 시스템에 영향을 준다.

**유형2** 하이퍼 바이저의는 VMware Workstation, VMware Player, VirtualBox 및 Parallels Desktop for Mac이 있다.



## 컨테이너(container)와 하이퍼바이저(Hypervisor)

최근 컨테이너 기술은 가상머신보다 단일 물리적 서버에 더 많은 애플리케이션을 배치할 수 있기 때문에 하이퍼바이저를 대체할 수있는 가능성으로 인기를 얻고 있다.

컨테이너형 가상화 기술은 기존의 가상화 기술보다 가벼워지고, 이식성이 뛰어나다. 대표적인 컨테이너 기술로는 도커(Docker)가 있다. 컨테이너는 가상머신보다 공간을 덜 차지하며, 더 많은 응용 프로그램을 처리할 수 있다.

그러나 보안 문제와 가상머신의 실제 사용자들은 컨테이너가 하이퍼바이저/가상머신을 반드시 대체 할 필요가 없으며, 이 두가지 모두 혼용하여 사용하는것이 더 좋다고 말한다.

보안 문제에서 일부 사람들은 컨테이너가 응용 프로그램이 공유하는 OS가 하나만 있고 가상머신이 응용 프로그램뿐만 아니라 OS도 격리하기 때문에 컨테이너가 하이퍼 바이저보다 덜 안전하다고 생각한다.

응용 프로그램이 손상되면 컨테이너의 단일 OS를 공격하여 다른 응용 프로그램에 영향을 줄 수 있다. 가상머신의 응용 프로그램이 손상되면 해당 서버의 한 OS 만 영향을 받고 다른 응용 프로그램이나 OS는 영향을 받지 않다.



## 하이퍼바이저 보안 문제

하이퍼 바이저가 일부 조치에 의해 컨테이너보다 더 안전한 것으로 간주될 수도 있지만 하이퍼 바이저와 관련된 보안 문제가 없는 것은 아니다. 이론상 해커는 OS 아래에 하이퍼 바이저로 설치되는 멀웨어 및 루트킷을 만들 수 있다.

멀웨어가 OS 아래에서 실행되기 때문에 멀웨어 방지 소프트웨어가 감지하지 않으면서 멀웨어가 OS 작동(예:암호 입력)을 가로챌 수 있기 때문에 하이퍼 재킹으로 알려진 이 프로세스를 탐지하기가 더 어려울 수 있다.



출처: [하이퍼바이저 개념 정리 – Hypervisor 란?](https://dora-guide.com/%ED%95%98%EC%9D%B4%ED%8D%BC%EB%B0%94%EC%9D%B4%EC%A0%80/)