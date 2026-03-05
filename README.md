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

