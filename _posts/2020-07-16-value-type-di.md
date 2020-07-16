---
title: "값 형식 DI"
date: 2020-07-16 23:57:52 +00:00
categories: Development
tags: Spring LectureNote
---

![image](https://user-images.githubusercontent.com/24868649/87687828-29ac6180-c7c1-11ea-89c8-69bb85dc6a25.png)

태그를 중첩해서도 설정 가능

![image](https://user-images.githubusercontent.com/24868649/87687911-421c7c00-c7c1-11ea-8a9b-9b9b97dfb48a.png)

Value 설정 이후 실행하면 오류 발생

값을 세팅할 수 있는 Setter를 만들지 않았기 때문 -> NewlecExam에서 setter 만들기

![image](https://user-images.githubusercontent.com/24868649/87687978-59f40000-c7c1-11ea-8078-52e463f28a5f.png)

파일 내용 영역에서 마우스 오른쪽 클릭 -  Source - Generating Getters and Setter... 클릭

규칙에 의해 kor 이름은 setKor를 자동 호출할 수 있게 됨

value 태그를 중첩해서 값을 세팅할 수도 있고 value 옵션을 통해 세팅할 수도 있다

setter를 통한 DI 예시

![image](https://user-images.githubusercontent.com/24868649/87688052-6f692a00-c7c1-11ea-9022-7c7158ace36b.png)

참고 영상  
[![Watch the video](https://img.youtube.com/vi/9iNvs7aeeDM/hqdefault.jpg)](https://youtu.be/9iNvs7aeeDM)
