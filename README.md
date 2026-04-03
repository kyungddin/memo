# memo


## To Do List
- 레포지토리 Readme 업데이트
  - 다음에 Shadow Boxing Readme 채우기
- 스핀락 / 뮤텍스 / 세마포어 공부하기
- std::string 더 공부하기
- 운영체제 복습할 방법 생각하기
- virtual의 적절한 사용법에 대해 공부하기
- 도커/쿠버네티스 공부
  - 도커 컴포즈와 그와 관련된 용어들로 우선 숙지..
- 깃허브 Pull Request 공부
- 포트포워딩 개념에 대해 공부하기
- TCP의 핸드셰이킹 개념 체화하기
  
<br>

- roadmap
  - 컴퓨터 네트워크: 하향식 접근
  - SQL
  - C++: STL, Effective, Algorithm, MFC
  - Docker & Kubernetes
  - Mini Project (OS/Network/DB)

## 260305

- Python in C/C++

```cpp
  #include <Python.h>

  int main()
  {
  	Py_Initialize();
  	PyRun_SimpleString("print('Hello from Python!')");
  	Py_Finalize();
  }
```


## 260313
- MinGW: Minimalist GNU for Windows
- VSC에서 C++ 확장을 설치해도 GNU Compiler가 없으면 컴파일이나 디버깅이 안된다
- GNU 용어 정리
  - GNU: 프로젝트의 이름. 자유 소프트웨어로 구성된 완전한 OS 만들기 프로젝트? (GNU = GNU's Not Unix)
  - GCC: GNU의 Compiler
  - GDB: GNU의 Debugger
  - G++: GCC 안의 C++ 컴파일러
    - 따라서 같은 c++ 소스여도 gcc로 컴파일하냐 g++로 컴파일하냐에 따라 링킹 결과가 다를 수 있다
- Visual Studio 작업에 따른 프로젝트&솔루션 명 수정
  - 솔루션은 모르겠는데 프로젝트는 IDE 내에서 이름을 바꿔도 이것이 반영이 안되는 경우가 흔하다
  - 따라서 직접 로컬에서 이름을 바꿔줘야 하는데, 그냥 바꾸기만 하면 오류난다
  - 따라서 sln(솔루션 파일)을 메모장으로 연 뒤에, proj 파일명과 디렉토리를 수정해줄 필요가 있다
  - 그리고 IDE 내에서도 단순히 프로젝트&솔루션 명 뿐만 아니라 네임스페이스 명도 신경써서 수정해주기
  - 이렇게 이쁘게 정리를 해줘야 나중에 Readme 쓸 때 편해진다
- \r은 carriage return
- "Q"으로 git log를 탈출할 수 있다


## 실제로 시스템콜을 직접 다룰 경우는 없을 것이다..!

```
C/C++ 코드
↓
Windows API
↓
User-mode system library
↓
System Call
↓
Kernel
```

- 우리의 시스템콜은 이렇게 호출되므로.. 우리는 간접적으로 시스템콜을 사용한다
- 가령 WinAPI인 CreateMutex()를 써서 mutex를 사용하는 코드가 MFC 내에서 보인다


## 260316

- Visual Studio 쓰면서, 해당 변수나 함수가 다른 파일에서 어떻게 쓰이는지 쉽게 추적하려면 모든 참조 찾기를 활용하자


## Python Interpreter

```
source.py
   ↓
bytecode
   ↓
Python VM
   ↓
실행
```

- 즉, 파이썬은 컴파일 시 기계어로 변환되지 않는다
  - 대신에 바이트코드를 VM이 해석하는 식으로 동작한다 (그래서 느림)
- 추가로 파이썬의 자료형은 Dynamic Typing이므로, VM이 이를 해석하는 과정이 포함되어 더 느리다
- Java
  - Java는 인터프리터와 컴파일 언어의 중간 정도
  - JVM, 즉 VM을 거치는 것은 맞지만, 자주 쓰는 코드는 JIT Compile을 통해 기계어로 변환
  - 그렇기에 Python과 C의 중간 정도의 속도를 자랑한다
 - 좀 더 정확한 Python 동작 Structure

```
Python code
↓
bytecode
↓
Python VM
↓
C 코드
↓
machine code
↓
CPU
```
Python의 실제 컴파일 과정


## 260317
- SCP → SSH를 이용한 파일 복사 프로토콜
- Git을 통해 Github에 push/pull 해줄 때 HTTPS와 SSH를 사용
  - Git은 파일이 아니라 commit graph와 object를 동기화합니다. 따라서 SCP가 아닌 SSH 프로토콜을 사용하는 것
- 도커와 쿠버네티스를 엮어서 가르치는 이유는, 쿠버네티스가 많은 수의 도커 컨테이너를 효율적으로 관리해주는 기술이기 때문이다
- Layer4의.. QUIC을 이용한 LiDAR Wireless Communication?


## 260318
- NAT vs 브리지; VM 동작의 관점에서
  - NAT (Network Address Translation)
  ```
  [VM] → [가상 NAT 라우터] → [Host PC] → [회사 네트워크 스위치] → 인터넷
  ```
  
  - 브리지
  ```
  [VM] → [회사 네트워크 스위치] → 인터넷
  ```

- /dev vs /media vs /mnd
  - /dev: 장치를 파일처럼 다루기 위한 인터페이스
  - /media: 자동 마운트 된 파일의 위치
  - /mnt: 수동 마운트 된 파일의 위치
 
- 마운트
  - 저장장치를 특정 디렉토리에 연결해서 사용 가능하게 만드는 것
  - 리눅스는 디스크/USB를 바로 못 쓰므로.. 마운트를 통해 파일 시스템에 연결하여 사용 가능
  - 즉, 마운트는 장치를 디렉토리에 꽂는다 라는 개념
 
- 데몬
  - 백그라운드에서 계속 돌아가는 서비스 프로그램
  - 보통 데몬이 마운트를 자동으로 해주는 경우가 많음
 
- 리눅스 명령어 정리
  - sed(stream editor): 텍스트 파일을 자동으로 수정/치환하는 명령어
  - ip addr: 네트워크 정보 확인할 때 씀
  - dnf: 최신 패키지 관리자 (yum의 업그레이드 버전)
  - rpm: 패키지 파일을 직접 다루는 도구 (파일 직섭 설치)
  - systemctl: 서비스(데몬) 관리 명령어
    - 데몬이므로 이 명령어 exec 이후 부팅 시에 자동으로 해당 서비스 ON
  - 고정 IP 설정할 때의 기본 DNS는, 그 이더넷의 DNS를 처리하는 DNS서버의 IP이다
  - 회사 같은 제한된 네트워크에서는 DHCP를 막고, DNS와 게이트웨이를 지정해줘야 한다. 따라서 수동 IPv4 지정이 필요함
 

## 260319
- https://gomu92.tistory.com/13
  - 만약 리눅스 깔 때 root로 SSH 비밀번호 접속 옵션 안 키면 이거 보고 수정해주자
  - /etc/ssh/sshd_conf
- PasswordAutentication 옵션으로 일반 유저도 접속 가능
- Linux 쓸 때 User별로 디렉터리 환경이나 Config가 다르니까 그걸 감안해서 환경 세팅을 해주도록 하자


## 260320
- Powershell 마저 Linux 터미널 명령어가 안 먹는 경우가 많은데, Git-bash로 갈아타자..
- Visual Studio Code에서 Git-Bash 기본 터미널로
  - ctrl+,로 설정 들어가서 terminal.integrated.defaultprofile.windows 검색
  - null -> git-bash
- 마운트 지점 설정 안 하면 매 부팅시마다 마운트 폴더 증발되는 이유.. 왜 그런지 파악하기


## 260321
- Pull Request, git 명령어의 branch 관리 등, 아직 깃허브 활용 역량을 더 키울 여지가 있다..!
- README에 상대경로를 지정해서 이미지 넣기
```
<img src="img/scan.png">
```


## 260323
- 브리지 vs NAT
  - 브리지: VM에 추가적인 IP를 할당하는 것 (즉, VM을 별도의 네트워크 노드로 보는 것)
  - NAT: 호스트에 내부망을 만들고 거기에 VM을 연결 (즉, VM을 호스트 안에 숨긴다)
    - 실질적으로 통신은 호스트의 IP로 하므로.. 이를 걱정 ㄴㄴ 해
- 서브넷의 /24는 앞의 24비트만 쓴다는 뜻이었지..
- 전자메일 프로토콜: POP3/IMAP/SMTP
  - 클라이언트 to 서버 OR 서버 to 서버: SMTP 프로토콜 사용
  - 서버 to 클라이언트: POP3 or IMAP 프로토콜 사용
    - POP3: 메일을 서버에서 가져와서 다운로드
    - IMAP: 메일을 서버에 두고 동기화
  - 전달과 관리의 역할이 다르기에 이렇게 프로토콜이 나뉜다
- 네트워크 프로토콜, 가령 SSH를 사용하다가 서버가 뻑 나는 경우가 있는데.. 어떤 경우가 있는지 research


## 260324
- Ansible Playbook 명령어를 쓰면, 그것이 활성화시키는 main.yml의 상대경로는 명령어에 따라 달라지낟
  - Shell 명령어는 일반적인 기준을 적용하면 된다
  - copy나 template은 ansible playbook 명령어가 사용되는 디렉터리를 기준으로한다
- enp0s3나 enp2s0은 장치 위치에 따른 이름으로.. 일반적으로 enp0s3는 VM에서 쉽게 볼 수 있는데 자세한 건 더 알아보기
  - s 앞은 PCI 버스 번호, s 뒤는 슬롯 번호
  - 그리고.. 윈도우에서는 이러한 장치명은 안 쓰고 직관적으로 이더넷 이런식으로 표기
- 리눅스(혹은 쉘인지) 버전에 따라 tar가 상대경로가 안 먹을 수도 있으니 참고 발암
- SQL Create 구문 까다로운데 이에 대한 파악 필요..


## 260325
- SQL 명령어에 문제가 있다면 SQL 서버와 socket 오류가 날 수 있다, 네트워크 문제로 생각하지 말고 syntax 체크부터!
- docker compose는 자동으로 이미지를 갱신해주지 않으니, 명령어에 build를 붙여서 갱신해주기
- vrrp_instance VI_1 = “하나의 가상 라우터(VIP + 상태 관리 단위)”
- UNIX Socket이란게 있고.. MariaDB는 그러한 소켓 방식을 사용해서 통신할 수도 있는데.. 이에 대해선 좀 더 공부하자
  - MariaDB는 localhost != 127.0.0.1
  - host를 안쓰거나 localhost를 쓰면 자동으로 UNIX Socket 통신
    - IP 명시가 안되어 있으니 파일 기반 UNIX Socket 통신..
    - .sock라는 소켓 파일을 기반으로 커널에서 통신이 발생한다
  - 반대로 -h로 host를 127.0.0.1로 강제하면 TCP 통신
    - Loopback 네트워크 지정하면 마리아DB에 의해 자동으로 포트가 3306으로 지정

   
## 260326
- 윈도우 자격 증명 때문에 깃 안될 수도..
- VSC 전체 주석 ctrl+/
- Docker Network의 브리지의 경우 컨테이너가 run이 되지 않는다면 veth0와 br 네트워크 장치가 안생긴다
- 왜인지 모르겠지만 mariadb를 도커 환경에서 실행할 경우 권한이나 접근 자체에 문제가 생기는 경우가 부지기수
- vm에서 nat 네트워크의 dhcp 알아두기



## 260327
- VM에서 NAT을 쓰는 경우
  - 호스트 컴퓨터가 NAT 게이트웨이 역할을 하며, 가상 머신의 네트워크 트래픽을 인터넷으로 라우팅한다.
  - VirtualBox NAT 엔진이 DHCP로 강제로 IP를 지정 (10.0.2.15 부터 자동~)
    - 그래서 만약 고정 IP를 사용하면 변환 과정에서 네트워크 내 기기로 판단하지 않고 먹통이 되는 것..!
- LAN에서의 IP vs MAC
  - LAN에서 실제 데이터의 전달은 MAC 주소를 통해서 이루어진다
  - 다만.. 송신지와 수신지를 특정하는 논리적 체계로서.. 페이로드에 있는 IP 주소 정보를 활용한다
  - 아 그리고 이때 ARP Protocol을 썼었지..!@@!
- SHEBANG
  - 대표적인 쉬뱅 구문
  ```
  #!      → shebang (이 파일은 스크립트다)
  /bin/bash  → 이 파일을 bash 로 해석해라
  ```
  - 즉 파일이 바이너리인지 스크립트인지 명확하게 정해준다
 

## 260328
- 사설 IP 정리
```
| 클래스 | 범위        | 특징       
| --- | -------------- | --------     
| A   | 10.0.0.0/8     | 엄청 큼       
| B   | 172.16.0.0/12  | 중간          
| C   | 192.168.0.0/16 | 작음 (가정용) 
```


## 260329
- Python의 PATH를 아나콘다보다 우선으로 놔도, pip와는 별개이기에 pip의 PATH도 아나콘다보다 우선으로 놔야, python 본진에서 패키지가 설치될 수 있다..!


## 260330
- Docker의 경우 컨테이너가 종료되면 작업 내용이 날아갈 수 있으니, volume을 통한 디렉터리 마운트..? 로 이를 해결한다?


## 260401: 만우절날 도커 공부
- docker image 분석
```
docker load -i image.tar
docker inspect image
docker history image:tag
docker run --rm -it -v /var/run/docker.sock:/var/run/docker.sock wagoodman/dive:latest image:tag
```

- docker-compose yml 분석
  -  ocker-compose.yml에 environment를 사용하면, run 시에 필요한 옵션을 자동으로 할당

- 컨테이너 안에 들어가서 실행 중인 프로세스 목록을 보는 명령어
docker exec -it <컨테이너ID> ps aux 

- 도커 이미지 업데이트 하기 (by using Dockerfile)
```
FROM image:tag
"명령어"
```
```
docker build -t image:tag .
docker save -o image.tar image:tag
```

- 도커 레이어는 한 번 쌓으면 돌이킬 수 없다. 매 레이어 마다 백업 tar로 대비하기


## 260402
- Git CRLF 무시하는 옵션 찾아놓기
- HTTP 프로토콜로 GIt 대용량 업로드 하면 push에서 터진다
  - git config --global http.postBuffer 524288000
  - 이걸로 해결

 
## 260403
- Keepalived에서 track_script 해서 script가 실행되어도 역할 교체는 오로지 advertisement가 끊겼을때만 발생한다!
  - 따라서 script에 의해서 역할교체도 원하면 priority를 0이하로 떨구도록 weight를 충분히 큰 음수로 지정해줄 것
