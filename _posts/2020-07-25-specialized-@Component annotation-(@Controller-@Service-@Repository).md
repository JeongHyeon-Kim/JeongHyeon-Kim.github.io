---
title: "특화된 @Component 어노테이션 (@Controller/@Service/@Repository)"
date: 2020-07-25 23:44:30 +00:00
categories: Development
tags: Spring LectureNote
---

Component 어노테이션을 통해 객체를 생성했을 때는 기본값을 어떻게 설정할 수 있을까?

Value 어노테이션을 사용함

![image](https://user-images.githubusercontent.com/24868649/88459610-a4683180-ced1-11ea-87a8-1faab1ea589b.png)

실제 적용해보면 이렇게 출력됨

![image](https://user-images.githubusercontent.com/24868649/88459614-aa5e1280-ced1-11ea-9adb-1e289dd0efa1.png)

지난번 코드는 Component 어노테이션으로 객체를 생성하는 것 자체는 문제가 되지 않으나 의미론적으로는 맞지 않음

해당 어노테이션은 MVC 패턴을 통해 웹앱 만들 때 업무형 로직을 가지고 있는 코드들을 나타내는 것임

좀더 의미론적으로 이름을 가진 어노테이션이 존재: Controller Component, Service Component, Repository Component

![image](https://user-images.githubusercontent.com/24868649/88459621-b34ee400-ced1-11ea-9dd1-31c1fca3f1bc.png)

이에 따라 Component 대신 세 가지의 어노테이션으로 교체해도 정상 작동함

![image](https://user-images.githubusercontent.com/24868649/88459627-b8ac2e80-ced1-11ea-8083-7af1c214ff08.png)

이름으로 역할을 좀 더 부여하여 특화한 것이라고 볼 수 있음

객체가 어떤 것이다라고 명시할 수 있어 좋음

MVC의 기본 구성은 다음과 같음

![image](https://user-images.githubusercontent.com/24868649/88459633-c1046980-ced1-11ea-8145-3b93c0c9c14b.png)

Controller: 사용자 입출력 담당

Service: 사용자의 요구사항에 맞는 서비스를 제공, 업무, 트랜잭션 단위

Repository: 데이터를 제공해주는 곳, 보통 DAO라고 말함

![image](https://user-images.githubusercontent.com/24868649/88459640-ce215880-ced1-11ea-85be-0dc93be8a903.png)

클래스의 쓰임을 명시해주므로써 쉽게 이해할 수 있음

Model과 Entity(NewlecExam)은 Component로 취급하지 않음

그럼 xml이 계속 필요한 것이냐?

아님, 모든 것들을 xml에서 어노테이션을 쓰도록 바꿀 예정

참고 영상  
[![Watch the video](https://img.youtube.com/vi/pyMzPpK4uXk/hqdefault.jpg)](https://youtu.be/pyMzPpK4uXk)
