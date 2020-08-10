---
title: "Point Cut (Weaving, JointPoint)"
date: 2020-08-08 22:33:58 +00:00
categories: Development
tags: Spring LectureNote
---

![image](https://user-images.githubusercontent.com/24868649/89720745-94436c80-da10-11ea-8f09-d8d3e6b1d126.png)

- weaving, JoinPoint, Pointcuts : AOP를 스프링으로 구현할 때 이러한 용어들을 씀

- 마치 뜨개질을 하듯 주업무를 꽂아놓는 과정을 의미 (weaving)

- 주업무를 join하게 될 지점(메소드)을 의미 (JoinPoint)

- 기본적으로 모든 메소드를 JoinPoint로 생각함 (모든 메소드에 대해 weaving)

- 특정 메소드만 weaving하고 싶게 정보를 지정 (Pointcuts)

![image](https://user-images.githubusercontent.com/24868649/89720748-a45b4c00-da10-11ea-9419-d80fd973c605.png)

- 클래스명에서 보듯 NameMatch 즉, 이름을 통해서 PointCut을 함

- Advice와 PointCut한 것을 연결해줘야 함, 다음 시간엔 더 쉽게 할 예정

- 이번 시간엔 코드를 좀 길게 써서 해봄, 연결하기 위한 객체를 생성(classicBeforeAdvisor)

- setter인 setAdvice라는 메소드를 advice라고 생성, 약속임

- PointCut과 Advice를 연결함, total에 대해서만 beforeAdvice가 실행되도록

![image](https://user-images.githubusercontent.com/24868649/89720753-ade4b400-da10-11ea-80ba-e91e681cbe34.png)

- 이전에 예외 처리를 위해 101로 설정했던 부분 1로 되돌리기

![image](https://user-images.githubusercontent.com/24868649/89720755-b63cef00-da10-11ea-848a-7562bdb6fd5b.png)

- total에 대해서만 해당 문구가 출력돼야 하는데 현재 avg에서도 출력중

![image](https://user-images.githubusercontent.com/24868649/89720757-bb01a300-da10-11ea-93bd-55d2bcf71eb5.png)

- 강의에서처럼 나오도록 해결법 찾아야 함

![image](https://user-images.githubusercontent.com/24868649/89720760-c1901a80-da10-11ea-869e-7c8f413b1548.png)

- 생성한 Advisor는 이 부분에서 설정을 해줌

- logBeforeAdvice 대신 써줌

![image](https://user-images.githubusercontent.com/24868649/89720764-cb198280-da10-11ea-9c31-854b1eab6187.png)

- avg에선 BeforeAdvice가 정상적으로 출력되지 않는 것 확인

![image](https://user-images.githubusercontent.com/24868649/89720766-d076cd00-da10-11ea-9fee-041776ac2ee6.png)

- 다른 Advisor를 추가할 수 있음

- 동일하게 Advisor 객체를 생성하고 Advice와 연결해줌

![image](https://user-images.githubusercontent.com/24868649/89720776-e8e6e780-da10-11ea-9893-9421c696f24c.png)

- total만 로그가 많이 출력된 것을 확인할 수 있음

- Advice-Advisor가 1대1 대응돼 불편함, 이 방법은 옛날 방식

- 다음 시간엔 더 나은 방식을 알아볼 예정

- 그 다음 시간엔 어노테이션으로 설정하는 방법을 알아볼 것

참고 영상  
[![Watch the video](https://img.youtube.com/vi/ikKy-6K63wU/hqdefault.jpg)](https://youtu.be/ikKy-6K63wU)
