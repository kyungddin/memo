# memo


## To Do List
- 하루 날 잡아서 레포지토리 대청소
- 스핀락 / 뮤텍스 / 세마포어 공부하기
- std::string 더 공부하기
- 운영체제 복습할 방법 생각하기
- virtual의 적절한 사용법에 대해 공부하기
  
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
