---
title: "AOP - Before Advice 구현하기"
date: 2020-08-05 23:11:10 +00:00
categories: Development
tags: Spring LectureNote
---

Spring에서는 Cross-cutting Concern 로직을 어떻게 꽂아넣느냐에 따라 4가지로 분리해서 생각함

앞에만 쓴다고 하면 Before 형태가 적절할 것임

![image](https://user-images.githubusercontent.com/24868649/89423256-3ba27400-d771-11ea-9ef3-70a59bcd4ccb.png)

- xml 파일에서 생성할 객체에 대해서 추가해줌

- list 형태기 때문에 여러개를 등록해 함께 호출될 수 있도록 할 수 있음

![image](https://user-images.githubusercontent.com/24868649/89423316-4bba5380-d771-11ea-873b-bd65649269b8.png)

- 클래스명을 복사해 spring.aop.advice 위치에 새로운 클래스 추가

- 파라미터의 정보를 알고 싶다면 args를 활용, 타겟의 정보를 알고 싶다면 target을 활용

- 이것으로 끝남, 앞에부분에 들어갈 내용만 포커스 맞춰서 하게 됨

- 이곳에 로컬 변수를 확인하든 DB를 확인하든 코드를 추가하면 됨

![image](https://user-images.githubusercontent.com/24868649/89423375-612f7d80-d771-11ea-861d-7363cfc412d8.png)

- 정상적으로 출력되는 모습

After와 After Throwing은 다음 시간에 알아 볼 것

참고 영상  
[![Watch the video](https://img.youtube.com/vi/oysjZMw9S6M/hqdefault.jpg)](https://youtu.be/oysjZMw9S6M)
