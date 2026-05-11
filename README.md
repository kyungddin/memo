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


## 260503
- MAC vs IP, 둘을 비교해서 좀 더 공부하기
- 클라우드 서버를 기반으로 통신하는 프로그램 구상하기
- JSON, HTTP 파서 만들기 (C++? Python?)


## 260504
- 포인터의 레퍼런스
  - **와 *& 전부 가능하다
  - 다만 C Style은 **
  - C까지 호환되는 라이브러리 쓸 때는 보통 **로 선언되어 있음
    
- XML과 DOM Tree research하고 정리하기


## 260506
- git branch 생성 관련 테크닉
  - `$ git checkout -b <name>` 로 새로운 브랜치 생성
  - `$ git push --set-upstream origin feature/haha` 로 새로운 브랜치에 대해 원격에 push


## 260507
- SQL에서 Column이 ROM인 경우가 있는데 왜 그런지 Research

- C/C++에서 path를 상대경로로 지정하면 빌드된 exe 파일을 실행할 때 에로사항이 발생할 수 있다
  - 따라서 절대경로와 출력 디렉터리 설정을 적절하게 해줄 필요가 있음

## 260508
- `$ git config --global --get pull.ff` 를 해줘야 fast forward 없이 merge가 가능하도록 기본값이 바뀜
  - fast forward를 고려해서 브랜치를 관리하는 연습을 해보기


## 260509
- git commit 메시지는 제목과 본문이 나뉜다
  - 제목과 본문 사이에 빈 줄이 반드시 있어야 한다
  - CLI에서 merge 할 때도 이것이 적용된다

- git config 범위 플래그
  - `--system`: 이 컴퓨터의 모든 사용자
  - `--global`: 이 컴퓨터의 현재 사용자
  - `--local`: 해당 디렉터리 git에만

- python virtual env 정리

  ```markdown
  # 프로젝트 폴더에서
  python -m venv .venv              # 가상환경 생성
  source .venv\Scripts\activate            # 활성화 (Windows: git bash)
  pip install -r requirements.txt   # 패키지 설치
  # ... 작업 ...
  deactivate                        # 비활성화
  ```


## 260510
- StockMonitor 작업 내용
  - PySide6 기본 구조 이해
  - 커스텀 타이틀바 코드 분석
  - 네이버 금융 API JSON 구조 파악

- Git Alert 작업 내용
  - PySide6 타이틀바 코드 분석
  - GitHub Webhook + ngrok + Flask + winotify 연동
  - 방해금지 모드와의 전쟁 승리


## 260511
- Git Alert에 .env 추가하기
- 
