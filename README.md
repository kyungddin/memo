## To Do List
- 스핀락 / 뮤텍스 / 세마포어 공부하기
 

## roadmap
- 4월: DB, Computer Network
- 5월: GUI, C++
- 6월: TEST


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


## 260512
- git에서 원격 브랜치 특정 커밋 삭제하기 (주의)
  - `$ git reset --hard` 로 특정 커밋 날리기
  - `$ git push origin 브랜치명 --force`로 해당 결과물 강제로 원격에 push

- git에서 merge가 완료된 feature는 삭제하자 (재사용 금지!)
  - `$ git branch -d feature/브랜치명`
  - `$ git push origin --delete feature/브랜치명`


## 260513
- C++ MFC 디버깅 팁
  - AssertValid()에 중단점 걸면 메모리 크러시 없이 추적을 진행할 수 있다

- C++ MFC Create Style
  ```markdown
  WS_  Window Style  윈도우 공통 스타일
  ES_  Edit StyleEdit  컨트롤 전용 스타일
  BS_  Button   StyleButton 컨트롤 스타일
  SS_  Static   StyleStatic 컨트롤 스타일
  LBS_  ListBox   StyleListBox 스타일
  CBS_  ComboBox   StyleComboBox 스타일
  SBS_  ScrollBar   StyleScrollBar 스타일
  TBS_  TrackBar   StyleTrackBar(슬라이더) 스타일
  PBS_  ProgressBar   StyleProgressBar 스타일
  WS_  EX_Window Style Extended  확장 윈도우 스타일
  ```

- C++ 동적 배열 생성
  ```cpp
  std::vector<CChartBalloonLabel<SChartXYPoint>*> pLabel(size);
  ```
  - 그냥 이런식으로 vector로 패자

- git --amend
  - `$ git commit --amend` 를 쓰면 이전 커밋과 합친다
  - `$ git commit --amend --no-edit` 을 하면 커밋 메시지 그대로 유지한다!


## 260514
- `$ git fetch --prune` ?
  - git fetch 동작에 대해서는 더 공부할 필요가 있어 보임


## 260515
- 전방 선언을 하지 않으면, 특정 클래스의 헤더를 가져와도 멤버 변수로 지정을 못하는 경우가 왕왕 발생하는데
  - 전방 선언에 대해 제대로 공부할 필요가 있어보인다
- C++ MFC에서 각 리소스에 대한 포인터 초기화에도 부모/자식별로 쓰이는 함수가 다 다르다


## 260516
- C++ 클래스 전방 선언
  - 특정 클래스에서 다른 클래스를 포인터로 사용할 때, 미리 해당 클래스가 필요하다는 것을 알려줌
  - 사용 가능한 경우
    - 클래스 멤버 포인터
    - 클래스 멤버 참조
    - 함수 매개변수/반환형 (포인터/참조)
  - 불가능한 경우
    - 객체 자체가 멤버인 경우
    - 멤버 함수를 호출하는 경우
    - 즉, 클래스 내부 정보를 진짜로 알아야 하거나 메모리에 배치해야 하는 경우
  - 보통 프로젝트에서는 헤더에서 클래스 전방 선언을 하고, 실제 include는 cpp 소스 파일에서 선언
  - #include를 하고 전방 선언을 안 했을 때 클래스 포인터 오류가 나는 이유
    - 순환 참조 (무한 루프)
    - 순환 참조를 `#pragma once` 와 같은 가드로 막아도, 해당 헤더의 일부만을 읽는 식의 오류가 발생
    - 이를 방지하기 위해 전방 선언을 사용하는 것

- SonarQube Test
  - Sequrity Spot: strlen or wcslen
    - 이 두 함수는 기본적으로 string이나 wide character 문자열이 nullptr이 아니라는 가정하에 짜여진 함수이다
    - 따라서, 예외처리 로직이 앞서 선행 되지 않으면 undefined behavior, 즉 미정의 동작 발생 가능성이 있다


## 260518
- `git push --force-with-lease` 를 써서 --amend 커밋에 대해 강제 push
