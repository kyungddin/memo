# memo


## ToDoList
- 하루 날 잡아서 레포지토리 대청소
- 스핀락 / 뮤텍스 / 세마포어 공부하기
- std::string 더 공부하기
- 운영체제 복습할 방법 생각하기

## 260305

- Python in C/C++

```python
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
- 너무 당연한 것이지만 VSC에서 C++ 확장을 설치해도 GNU Compiler가 없으면 컴파일이나 디버깅이 안된다
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
- virtual의 적절한 사용법에 대해 공부하기
- \r은 carriage return!
- "Q"으로 git log를 탈출할 수 있다..!


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
- 우리의 시스템콜은 이렇게 호출되므로.. 우리는 간접적으로 시스템콜을 사용한다..
- 가령 WinAPI인 CreateMutex()를 써서 mutex를 사용하는 코드가 MFC 내에서 보인다..!

### 260316

- Visual Studio 쓰면서, 해당 변수나 함수가 다른 파일에서 어떻게 쓰이는지 쉽게 추적하려면 모든 참조 찾기를 활용하자
