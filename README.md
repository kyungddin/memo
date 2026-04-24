# memo
여러가지 메모

---

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
- 메모 한 번 싹 정리해야 할 거 같은데..
- 월별로 했던 일 정리하기 + 업무노트 구매


## roadmap
- 4월: DB, Computer Network
- 5월: GUI, C++
- 6월: 실전!

---

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
- 하지만 pybind를 쓰는 것도 좋다


## 260313
- MinGW: Minimalist GNU for Windows

- VSC에서 C++ 확장을 설치해도 GNU Compiler가 없으면 컴파일이나 디버깅이 안된다

- GNU 용어 정리
  - GNU: 프로젝트의 이름. 자유 소프트웨어로 구성된 완전한 OS 만들기 프로젝트? (GNU = GNU's Not Unix)
  - GCC: GNU의 Compiler
  - GDB: GNU의 Debugger
  - G++: GCC 안의 C++ 컴파일러
    - 따라서 같은 c++ 소스여도 gcc로 컴파일하냐 g++로 컴파일하냐에 따라 링킹 결과가 다를 수 있다
  - gnome도 있어요

- Visual Studio 작업에 따른 프로젝트&솔루션 명 수정
  - 솔루션은 모르겠는데 프로젝트는 IDE 내에서 이름을 바꿔도 이것이 반영이 안되는 경우가 흔하다
  - 따라서 직접 로컬에서 이름을 바꿔줘야 하는데, 그냥 바꾸기만 하면 오류난다
  - 따라서 sln(솔루션 파일)을 메모장으로 연 뒤에, proj 파일명과 디렉토리를 수정해줄 필요가 있다
  - 그리고 IDE 내에서도 단순히 프로젝트&솔루션 명 뿐만 아니라 네임스페이스 명도 신경써서 수정해주기
  - 이렇게 이쁘게 정리를 해줘야 나중에 Readme 쓸 때 편해진다

- \r은 carriage return

- "Q"으로 git log를 탈출할 수 있다

- 실제로 시스템콜을 직접 다룰 경우는 없을 것이다..!
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
- Powershell 마저 Linux 터미널 명령어가 안 먹는 경우가 많은데, Git-bash로 갈아타자
  
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
      
- 서브넷의 /24는 앞의 24비트만 쓴다는 뜻이었지
  
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
    
- 리눅스(혹은 쉘인지) 버전에 따라 tar가 상대경로가 안 먹을 수도 있으니 참고바람
  
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
  - 아 그리고 이때 ARP Protocol을 썼었지!
    
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
- 심심할때 PS 문제 풀기


## 260406
- keepalived의 경우 특정 옵션이 서로의 타이밍 이슈에 영향을 줄 수 있다 (ex: interval, timeout)
  
- 쉘스크립트의 경우 if문은 0에서 활성화


## 260407
- openCV: 모폴로지, 히스토그램 평탄화, channel split& merge
  - 이것들 아직 좀 부족함.. 많이

## 260408
- C++ 빵꾸: 복사생성자, Static 멤버, 연산자 중복, 상속, 가상함수 (일단은 여기까지만..)
  
- 보조기억장치가 여러 개 있는 상황에서, EFI가 깔리지 않은 곳에 OS를 설치하면 부팅 옵션에서 볼 수 없다
  
- 부트시스템 공부: EFI, 파티션, 포맷 등등
  
- 리눅스 시스템에서 파티션 정리하기
```
1. $ lsblk 로 메모리 체크
2. $ sudo wipefs -a /dev/sda 이건 sda 저장장치 날리기
3. $ sudo fdisk /dev/sda 새 파티션 생성 (n으로 새로운 파티션 생성 w로 저장)
4. $ sudo mkfs.ext4 /dev/sda1 (파티션 데이터용으로 만들어주기)
5. (centos8 기준) $ sudo grub2-mkconfig -o /boot/grub2/grub.cfg 로 grub(boot loader) 정리
```
   
- 비프음 죽이기
```
$ echo 'setterm -blength 0' >> ~/.bashrc
```

- 파티션의 중요성
  - GPT: 파티션은 ‘공간 분할’이 아니라 운영체제에게 “이 디스크를 어떻게 써라”라고 알려주는 ‘메타데이터(설계도)’임
  - 즉, 운영체제 입장에서 그냥 /dev/sda는 원시데이터 덩어리라 데이터 저장용으로 활용 불가
    
- 윈도우 shell에서 패키지를 설치하거나 빌드를 해주려면..
  - MSYS2(Minimal System2)는 윈도우즈(Windows) 운영체계 하에서 라이브러리 또는 소프트웨어를 빌드할 때 사용하는 플랫폼입니다.
  - 이걸 깔면 MINGW도 자동으로 Setup!
  - $ make 나 $ pacman 쓰려면 msys2 터미널로 해주기!
 
- 리눅스는 윈도우처럼 C: D: 와 같은 드라이브 문자를 안 쓰므로.. 해당 저장공간을 사용하려면 디렉터리를 생성 후 /dev에 있는 저장장치 파일과 마운트를 해줘야함
  - 따로 마운트하지 않은 모든 디렉터리는 루트(/)가 올라가 있는 그 파티션(= OS가 설치된 파티션)에 저장된다.
  - 마운트해주기
    1. $ sudo mkdir /data
    2. $ sudo mount /dev/sda1 /data
    3. $ sudo blkid ## UUID 확인
    4. /etc/fstab에 "UUID=xxxx-xxxx  /data  ext4  defaults  0  2" 추가해주기 # 이걸해줘야 영구적으로 마운트!

- 지피띠가 말해주는 닌자가 빠른 이유
```
**닌자 (빌드 시스템)**가 **GNU Make**보다 빠른 이유는
“인술”이 아니라, **설계 목표가 완전히 다르기 때문**입니다.

---

## 🎯 설계 철학 차이

| 항목    | GNU Make          | Ninja                     |
| ----- | ----------------- | ------------------------- |
| 목표    | 사람이 Makefile 작성   | **생성기가 파일 생성** (예: CMake) |
| 문법    | 강력하지만 복잡          | **극도로 단순**                |
| 기능    | 조건문, 변수, 함수, 셸 호출 | **오직 빌드 실행만**             |
| 해석 비용 | 매번 Makefile 해석    | **거의 파싱 없음**              |
| 속도 초점 | 유연성               | **실행 속도**                 |

Make는 “스크립트 언어”에 가깝고,
Ninja는 “빌드 전용 VM”에 가깝습니다.

---

## ⚡ 1) Make는 매번 Makefile을 ‘해석’함

Make는 빌드할 때마다:

* 변수 확장
* 함수 호출
* include
* 조건문 평가
* 셸 실행

을 전부 다시 수행합니다.

프로젝트가 커질수록 **이 해석 시간이 매우 큼**.

Ninja는?

> 이미 계산이 끝난 `build.ninja`를 **그냥 읽고 실행만**.

---

## ⚡ 2) 의존성 그래프를 미리 계산해 둠

보통 **CMake** 같은 생성기가

* 모든 의존성
* 모든 컴파일 명령
* 모든 출력 파일

을 **완성된 형태로** 써 줍니다.

Ninja는 **그래프 계산을 안 함** → 즉시 실행.

Make는 그래프를 매번 계산.

---

## ⚡ 3) 병렬 처리 방식 차이

Make의 `-j` 병렬은 “가능하면” 병렬.
Ninja는 **처음부터 병렬 실행 엔진으로 설계**됨.

* 작업 큐
* CPU 코어 최적 분배
* I/O 대기 최소화

---

## ⚡ 4) 변경 감지(Incremental build)가 압도적으로 빠름

파일 하나 수정했을 때:

* Make: “뭐가 바뀌었지?” 다시 판단
* Ninja: “이 파일 바뀌었네 → 이 타겟만” 즉시 실행

대형 C++ 프로젝트에서 차이가 극적입니다.

---

## 🧠 한 줄 요약

> Make는 **빌드 스크립트를 실행**하고,
> Ninja는 **컴파일 명령을 실행**한다.

그래서 Ninja가 빠름.

---

## 그래서 업계 표준 조합

* **CMake** → 의존성 계산
* **닌자 (빌드 시스템)** → 초고속 실행

이 조합이 현대 C/C++ 빌드의 사실상 표준입니다.
```

- 코드 비교하기? 나중에 필요한 상황이 오면 익혀두자
  - git diff?
  - visual studio compare 기능?

- 당장 더 익혀야 할 것: cpp, TCP/IP, HTTP, CMake, Python Flask
  - 일단 퇴근하고 네트워크부터 더 딥하게 파기
  - GUI와 구현 언어에 대해 고민하기.. 가능하다면 무조건 C++ MFC로..


## 260409
- CMake Static Library Step
  1. /lib와 /includes 생성 후 소스와 헤더 작성
  2. /lib에 CMakeLists.txt 스크립트 작성
    - add_Library()는 add_executable처럼 파일을 생성하는 명령어
    - target_include_directories()로 헤더 파일 경로 추가 (PUBLIC을 하면 이후 메인 CMake에서도 헤더 파일 경로를 추적)
  3. 메인 CMakeLists.txt 작성
    - add_subdirectory()로 lib 추가해주기
    - target_link_libraries()로 라이브러리 링크해주기

- CMake 명령어 몇 가지
  1. set(MY_VAR value): 변수 선언 및 값 저장
  2. include_directories(): 구식.. target_include_direcotries() 추천 (헤더 탐색 경로 추가)
  3. add_subdirectory(): 해당 디렉토리의 CMakeListx.txt를 읽어서 타깃을 가져와라?
  4. include(): C/C++의 #include와 같이 해당 파일의 코드를 추가해주는 것
 
- 아직 CMake의 타깃 개념이 완벽하게 정리가 안됐지만..
  - include_directories는 경로를 직접 추가해준다
  - target_include_direcoties는 라이브러리만 추가해준다 (그리고 타깃인 라이브러리가 그 경로를 들고있다..? 어렵네..)
 
- Doxygen
  - 소스 코드 주석을 읽어서 자동으로 문서(HTML/PDF/LaTeX 등)를 만들어주는 도구
  - C++ 개발자들이 API 문서를 만들 때 가장 많이 사용하는 도구
  - Hmm.. 사용법만 익혀두면 아주 유용할 거 같은데

- Visual Studio 등을 설치 시, Windows SDK가 같이 설치되며.. 여기에서 Win32 API를 사용할 수 있다
  - Visual C++은 Win32 API 라이브러리를 기본으로 제공하고 있어서.. C++ 사용자가 Win32 API를 쉽게 사용할 수 있도록 도와줍니다..
  - 따라서 WinSock과 같은 윈도우 라이브러리 기반 소켓 통신 구조를 알아야 내가 이걸 플젝에서 써먹을 수 있겠지..?
 
- id_rsa와 같이 SSH 암호화 방식에 대해 알아두면 좋을 거 같다
- 추가로 HTTPS는 tcp와 http 사이에 tls를 끼워넣은거라 전혀 새로운 프로토콜은 아니라고 하니 이것도 탑다운 네트워크 일으면서 눈 여겨 보기

- C++에서의 HTTP 프로토콜 통신은 직접 구현해야 한다
  - Winsock과 같은 라이브러리는 바이트 전송 (TCP) 만을 담당한다
  - 즉, Winsock 단독으로는 HTTP를 전혀 이해하지 못한다
  - 즉, TCP로 HTTP 문자열을 주고 받아야 하기에, 이러한 HTTP를 해석하는 부분을 직접 구현해야 한다
    - 상대적으로 보다 high-level의 다른 언어는 이런 것들을 처리해주는 라이브러리가 있는 거 같음
    - 공부하려면.. C++로 짜야겠지..?
    - 필요하다면 서버 쪽을 Flask, Redis, Celery를 이용해 구현해보는 것도 방법


## 260410
- x86_64의 역사..
  - x86이라는 것은 Intel의 CPU 라인업을 의미 (8086 cpu 등등..)
  - 원래 x86 아키텍처는 32bit 아키텍처였음
  - AMD에서 상호 라이센스 협약을 통해 x86 아키텍처 개발이 가능해짐
  - 64비트 시대에 와서 Intel은 완전 새로운 64비트 아키텍처를 설계하다가 망함
  - 반대로 AMD는 기존의 x86 아키텍처를 64비트로 확장
  - 결론은.. 두 회사의 아키텍처는 x86_64로 완전하게 동일Make는 빌드할 때마다:

- Ubuntu의 “운영/관리 도구” 상당수가 Python으로 작성되어 있다. (이건 좀 놀라운데)

- 마리아DB를 centos가 아닌 ubuntu에서 돌리면 좋은 이유
  1. 패키지 최신성
  2. 마리아DB 공식 문서는 우분투 기준으로 작성


## 260411
- SQL 키워드가 대문자인 이유
  - 키워드는 대문자로, 그 외 변수와 같은 것들은 소문자로 해야 가독성이 좋으니까~
 
- SQL문법을 익히기보단.. 개념만 빠르게 훑고 pymysql같은 것으로 역으로 익히는 것도 좋아보임 (히구루마식으로)

- 포맷 간단 공부
  - concept: 저장 장치를 ‘어떤 규칙(형식)’으로 사용할지 정하는 작업
  - 즉, 보조기억장치를 ext4와 같은 파일시스템으로 초기화
    - 파일시스템: 파일을 어디에, 어떤 규칙으로 저장할지 정한 구조
  - 포맷하면 데이터가 날아가는 이유: 데이터 하나하나 지우는 게 아니라 저장 구조(목차, 지도)를 새로 만드는 것
    - 그래서 완전 포맷이 아니라면 데이터가 물리적으로는 남아 있고, 이를 기반으로 복구도 가능!


## 260412
- 2차원 배열 BFS/DFS: 단지번호붙이기(2667), 미로 탐색(2178), 토마토(7576), 섬 연결하기(4963)


## 260413
- localhost가 127.0.0.1인 이유: A클래스 네트워크의 최댓값인 127을 관례로 사용?

- catch2 (doctest)를 통해 C++를 모듈 단위로 빠르게 검증할 수 있다
  - 심지어 라이브러리가 main()도 작성해줌


## 260414
- 적어도 소켓 프로그래밍을 능수능란하게 하려면 Layer4까지는 제대로 익혀놓을 필요가 있다

- 소켓: Windows vs Linux
  - Windows는 역사적으로 초기에 네트워크 없는 OS였다. 즉 특정 프로세스가 네트워크를 사용하려면 DLL을 로드해서 네트워크 스택에 연결해줘야 함
  - 반대로 Linux는 네트워크마저 파일 시스템의 일부로. 프로세스 생성 시 커널 네트워크 스택에 자동으로 연결된다
  - 따라서 WinSock 사용시 WSADATA를 초기화 해줘야 한다


## 260415
- C#만의 포인트
  1. CLR 위에서 JIT을 돌림 (자바랑 같음)
  2. 헤더 없음: 어셈블리 단위 (컴파일 단위가 Assembly? 그래서 include 개념이 없다?)
  3. 포인터 대신 참조 씀 + GC (메모리 leakage 방지)
  4. property: 함수지만 변수처럼 보이는 것?
  5. LINQ
  6. envet / delegate
  7. 리플렉션
  8. async / await
  9. attribute

- C#에서 공부해야 하는 것
  1. property
  2. LINQ
  3. event / delegate
  4. async / await
  5. attribute
  6. WPF 데이터 바인딩 개념


## 260416
- 도커 이미지 빌드 명령어
```bash
docker build -t tw-db-connector:v1.0 . # .는 빌드 디렉토리
```

- 도커 이미지 빌드
```dockerfile
ENV DEBIAN_FRONTEND=noninteractive
```
  - 이게 있다면 사용자 상호작용이 아예 없으므로 표준시간이 None으로 된다

- 도커 이미지 압축
```dockerfile
docker save -o [파일명].tar [이미지명]:[태그]
```

- pybind와 pybind_json은 개발자들이 cmake가 용이하게 파일을 통으로 배포했다
  - Copyright이나 과한 수정 금지!!

- 도커 포트 포워딩 문제
  - 80/tcp라고만 되어 있으면.. 도커 내부의 포트는 80을 사용하지만 외부와 연결이 안됨
  - 따라서 docker run -p 80:80 이런식으로 포트 포워딩을 해줘야 한다

- 정확히 기억 안 나지만 cmake나 makefile 둘 중 하나는 리눅스 환경에서 CRLF에 민감하니 이를 꼭 체크해주기

- HTTP의 메시지 포맷을 제대로 파싱하는 것에 유의! 특히 CRLF!
  
- CMake, Makefile, Dockerfile 정리
  - Doxy 사용법도 숙달하면 좋지만.. 난 직접 README 작성하는게 더 나아보임


## 260417
- 우분투 서버 네트워크 문제
  - archive.ubuntu.com은 여러 대의 서버가 랜덤하게 연결되는데, 하필 오늘 연결된 IP가 상태가 안 좋을 수도 있다!
  - 해결 방법: 미러 서버 교체
    - 기본 서버(archive.ubuntu.com)는 해외 서버라 종종 이런 연결 끊김이 발생한다. 한국의 카카오 서버 등으로 변경하면 속도도 수십 배 빨라지고 훨씬 안정적이다!
    - Dockerfile Setting
    ```Dockerfile
    # 기본 서버를 카카오 미러 서버로 교체
    RUN sed -i 's/archive.ubuntu.com/mirror.kakao.com/g' /etc/apt/sources.list && \
        sed -i 's/security.ubuntu.com/mirror.kakao.com/g' /etc/apt/sources.list
    ```
- Swap Space 복습
  - 메모리 가상화 단계에서, 우리는 프로그램을 load할 때 전체를 load하지 않고 일단 Swap Space에 박아둔다
  - page fault가 발생하면 디스크에서 일부를 가져와 램에 올린다
  - 보다 정확하게 프로그램이 실행되면 램 & 스왑공간 & 디스크 세 공간에 존재한다
    - Small Binary: (코드 + 초기화된 데이터) 원본이 파일로 존재함 && Swap Space: (수정된 데이터 + BSS + 힙 + 스택) 원본 파일이 없음(Anonymous).
    - 그래서 일반적으로 Binary보다 Swap Space 상의 프로그램 데이터 크기가 더 크다

- 리눅스에서 Swap 파티션을 RAM에 2배로 할당하는 이유
  - 가상 메모리 매핑의 안정성, LRU 성능 향상 등, 결국 Hierarchy를 효율적으로 달성하기 위함

- 윈도우 bash에서 python 패키지 설치하기
  ```bash
  $ python -m pip install matplotlib
  ```


## 260418
- Visual Studio 작업한 거 Git하다보니 용량 Issue 발생 >> .gitignore 최초 작성
  - .gitignore 사용법
    1. 디렉토리 작성하면 해당 디렉토리 전부 무시함 (간단하게 디렉토리 패스만 써주면 된다)
    ```
    CPP/MySocket/.vs
    ```
    2. 파일무시
    ```
    test.exe
    config.json
    ```
    3. 특정 확장자 무시 (wild character)
    ```
    *.log
    *.tmp
    *.o
    ```
  - 작성했으면, 수동으로 이전에 잔여 파일도 제거해주자
    ```bash
    # .vs는 디렉터리 명임
    git rm -r --cached .vs 
    ```


## 260419
- 쿠버네티스 vs docker compose 조사하기
- 리액트 조사하기


## 260421
- DLL 파일이 왜 실행파일이랑 같은 디렉터리에 있어야 하는지 조사하기
- 자동으로 창 크기 조정될 수 있도록 MFC 신경쓰기



## 260422
- 전방 선언 (Forward Declaration)
  - C/C++ 에서는 가급적이면 헤더가 다른 헤더를 include 하는 경우는 지양해야 한다
  - <string> 같은 STL은 어쩔 수 없지만.. 클래스 같은 경우는 헤더를 굳이 include 하기보단
    전방선언으로 가볍게 만들자
  ```cpp
  class B;

  class A
  {
      B obj;   // ❌ 불가능
  };
  ```


## 260424
- 라이브러리 복습 철저하게 하기 (기억이 안 나..)
