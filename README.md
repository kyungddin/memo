# memo


## 260305
- noexcept 구문에 대해 알아보기
- 운영체제 복습할 방법 생각하기
- Python in C/C++

  #include <Python.h>

  int main()
  {
  	Py_Initialize();
  	PyRun_SimpleString("print('Hello from Python!')");
  	Py_Finalize();
  }


## 260306
- std::string 더 공부하기
- string VS CString 알아두기.. (CString은.. Window용?)


## 260313
- MinGW: Minimalist GNU for Windows
- 너무 당연한 것이지만 VSC에서 C++ 확장을 설치해도 GNU Compiler가 없으면 컴파일이나 디버깅이 안된다
- GNU 용어 정리
  - GNU: 프로젝트의 이름. 자유 소프트웨어로 구성된 완전한 OS 만들기 프로젝트? (GNU = GNU's Not Unix)
  - GCC: GNU의 Compiler
  - GDB: GNU의 Debugger
  - G++: GCC 안의 C++ 컴파일러
    - 따라서 같은 c++ 소스여도 gcc로 컴파일하냐 g++로 컴파일하냐에 따라 링킹 결과가 다를 수 있다
