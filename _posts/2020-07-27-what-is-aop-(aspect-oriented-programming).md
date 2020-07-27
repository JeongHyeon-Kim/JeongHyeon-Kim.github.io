---
title: "AOP(Aspect Oriented Programming) 이란?"
date: 2020-07-27 23:11:39 +00:00
categories: Development
tags: Spring LectureNote
---

Spring은 아니고 방법론임, 이 방법론에 Spring이 도움이 된다고 함

Aspect Oriented Programming

OOP에선 사용자의 업무 로직에만 관심이 있었음

![image](https://user-images.githubusercontent.com/24868649/88552816-7ca6d400-d05f-11ea-8867-4a8ba9c819ac.png)

사용하다보니 업무 로직 이외의 코드들이 필요하게 됨

사용자는 모르며 개발자나 운영자만 아는 코드들임

![image](https://user-images.githubusercontent.com/24868649/88553070-d4ddd600-d05f-11ea-813f-62a797f40a3a.png)

관점이 다른 업무지만 개발자, 운영자는 필요한 것임

개발자나 운영자의 관점에서도 필요한 것임

AOP는 OOP를 포함하는 개념(더 큰 개념)

객체와 메소드를 포현, ->는 사용하고 있음을 의미

![image](https://user-images.githubusercontent.com/24868649/88553140-e626e280-d05f-11ea-9167-27622f722f8d.png)

필요에 따라 로그처리(성능 테스트, 사용자 권한 등), 보안처리, 트랜잭션처리같은 껴들어가는 업무, 주업무는 아니지만 필요한 것들이 있을 수 있음

![image](https://user-images.githubusercontent.com/24868649/88553160-ecb55a00-d05f-11ea-8c1c-4c89532cbc8f.png)

앞이라던지 뒤에 껴들어 가게 돼있음(그림에선 위와 아래)

마치 아이스크림 빵또아 같은 느낌

Cross-cutting이란 빵또아의 빵처럼 뺏다 꽂았다가 자유로움을 의미, 주업무는 아니지만 필요한 것들

![image](https://user-images.githubusercontent.com/24868649/88553200-f63ec200-d05f-11ea-9e5f-bab618790e99.png)

옛날에는 이걸 쉽게 할 수 없었음, 직접 소스 코드를 주석했다가 풀었다가 했었음

소스코드를 가지고 있는 사람만 이런 작업이 가능했음

![image](https://user-images.githubusercontent.com/24868649/88553216-fc34a300-d05f-11ea-80ea-3a750ec89fe0.png)

이런걸 쉽게 할 수 있는 방법이 없을까 생각하다가 나온 것이 AOP 방법론

소스코드는 그대로 쓰도록 둠

즉, 굳이 Cross-cutting Concern을 Core Concern에 꽂아두지 않고 만듦

직접 넣을 필요가 없음, 따로 Proxy를 사용해서 호출되도록 함

따로 분리를 하고 거기에서 Core Concern을 호출하도록 바꿈

이런 것을 할 때 Spring을 사용하게 되면 쉽게 가능함

![image](https://user-images.githubusercontent.com/24868649/88553264-0bb3ec00-d060-11ea-9c4e-b427ec503e99.png)

Spring이 아니라 Java만 가지고도 가능하므로 그렇게 해볼 예정

참고 영상  
[![Watch the video](https://img.youtube.com/vi/y2JkXjOocZ4/hqdefault.jpg)](https://youtu.be/y2JkXjOocZ4)
