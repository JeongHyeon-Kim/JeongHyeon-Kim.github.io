---
title: "After Returning/Throwing Advice 구현하기"
date: 2020-08-07 23:32:00 +00:00
categories: Development
tags: Spring LectureNote
---

![image](https://user-images.githubusercontent.com/24868649/89656263-4cd0b980-d906-11ea-8ac9-d44745987b6c.png)

- 지난 시간과 동일하게 클래스명을 먼저 xml 파일에서 정의

![image](https://user-images.githubusercontent.com/24868649/89656280-522e0400-d906-11ea-9001-3542cff714aa.png)

- class명을 참고해서 새로운 java 파일 생성

- AfterReturningAdvice 인터페이스를 가져와 구현(ctrl+space를 통해 가져오기 가능)

- 구현에 필요한 기본 틀도 생성(마우스 갖다대서 클릭하면 자동 구현)

![image](https://user-images.githubusercontent.com/24868649/89656295-59eda880-d906-11ea-9b57-48d02bf93b82.png)

- returnValue 인자를 통해 주업무 로직에서 반환 값이 있으면 그것을 사용할 수 있음

- method 인자를 통해 호출된 메소드에 대한 정보를 확인할 수 있음

![image](https://user-images.githubusercontent.com/24868649/89656312-607c2000-d906-11ea-98ad-f7aa5e4e5f02.png)

- 간단하게 확인을 위해 출력 코드 작성

![image](https://user-images.githubusercontent.com/24868649/89656332-68d45b00-d906-11ea-8776-f928e03f0f65.png)

- 실행 결과를 보면 BeforeAdvice 내용 이후 출력된 것을 확인할 수 있음

![image](https://user-images.githubusercontent.com/24868649/89656355-6f62d280-d906-11ea-906e-9664a09d824a.png)

- AfterThrowingAdvice 역시 동일한 방법으로 클래스 이름을 먼저 설정

![image](https://user-images.githubusercontent.com/24868649/89656375-7689e080-d906-11ea-9f92-17b52dc4b1ef.png)

- java 파일도 생성한 후 implements를 통해 ThrowsAdvice를 받음

- 앞선 다른 Advice와는 다르게 구현해야 될 인자가 정해지지 않음

- 예외 처리는 어떻게 해야 된다고 정할 수 있는 부분이 아니기 때문임

- 어떠한 예외가 일어나냐에 따라 인자가 달라짐

![image](https://user-images.githubusercontent.com/24868649/89656400-7ee21b80-d906-11ea-80c2-b50634d69e6f.png)

- IllegalArgumentException라는 부분의 인자가 수많은 경우의 수를 가짐

- 여기선 Argument에 대한 exception 예제를 위해 IllegalArgumentException라고 지음

- 원래는 before 이후 after가 불리지만 주업무 로직 실행 중 예외가 발생하면 불림

![image](https://user-images.githubusercontent.com/24868649/89656419-86092980-d906-11ea-980f-004a311d8158.png)

- aop.entity 패키지의 NewlecExam에 정의된 함수에서 예외에 대한 처리 로직을 추가하여 예외 발생 시 예외 로직으로 빠지도록 코드 추가

![image](https://user-images.githubusercontent.com/24868649/89656434-8b667400-d906-11ea-9e84-9090f3e187f0.png)

- 예외처리 로직을 타도록 xml 파일에서 kor 변수의 초기값을 수정

![image](https://user-images.githubusercontent.com/24868649/89656449-90c3be80-d906-11ea-9f9a-a9e474f95dea.png)

![image](https://user-images.githubusercontent.com/24868649/89656459-93beaf00-d906-11ea-800e-a7a679c591ca.png)

![image](https://user-images.githubusercontent.com/24868649/89656466-96210900-d906-11ea-804e-773f47ff8247.png)

- AfterThrowingAdvice 구현부에서 메시지 출력 부분을 추가하면 다음과 같이 실행됨

![image](https://user-images.githubusercontent.com/24868649/89656484-9c16ea00-d906-11ea-8709-0bc04d643fcb.png)

여태까진 total, avg와 같이 타겟 모두에 대해 곁다리 업무가 추가됐는데 다음 시간에는 원하는 타겟들에 대해서만 출력할 수 있도록 하는 방법을 알아볼 예정

참고 영상  
[![Watch the video](https://img.youtube.com/vi/rClfDKEiEA0/hqdefault.jpg)](https://youtu.be/rClfDKEiEA0)
