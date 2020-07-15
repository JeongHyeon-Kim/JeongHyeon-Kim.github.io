---
title: "스프링 IoC 컨테이너 사용하기(ApplicationContext 이용하기)"
date: 2020-07-15 22:41:52 +00:00
categories: Development
tags: Spring LectureNote
---

xml 파일의 위치에 따라 ApplicationContext 생성

Java Prj을 Maven Prj으로 바꾸기

프로젝트에서 오른쪽 마우스 클릭 - Configure - Convert to Maven Project 선택 - com.newlecture로 Group Id 변경(Maven 강의 듣기)

Dependencies - Dependencies 탭의 Add 클릭

목록이 안 나오는건 당장은 Window - Show View - Others - Maven - Maven Repositories Open

Global Repositories - Central - 오른쪽 마우스 클릭 - Rebuild Index 클릭(시간이 너무 걸림)

Maven Repository 검색 후 mvnrepository.com 사이트 접속 - Spring Framework 검색 - Spring Context - 최신버전의 Maven 내용을 클릭하여 복사

Pom.xml의 version 태그 밑에 해당 내용 붙여넣기

저장하면 필요한 것들을 가져오는 작업을 쭉 함

![image](https://user-images.githubusercontent.com/24868649/87552004-1380a180-c6ec-11ea-9299-4bf6771af689.png)

Dependencies Hierarchy를 확인해보면 필요한 Dependeny들을 모두 가져온 것을 볼 수 있음

IoC 컨테이너 형태(context)로 만들어뒀고 꺼내 쓸 때는 id로 가져올 수도 있고 class로도 가져올 수 있음

Class로 써서 뭉뚱그려 가져올 수 있으며 추가될 때는 구분하는 명시를 추가로 해주면 됨

![image](https://user-images.githubusercontent.com/24868649/87552078-2abf8f00-c6ec-11ea-9ce6-1e83c593badf.png)

setting.xml 작성 시 ref나 value는 가져올 객체의 이름(id)을 넣어줌(=exam)

설정 파일만 수정하면 소스 코드 수정 없이 다른 형태의 함수 호출 가능

참고 영상  
[![Watch the video](https://img.youtube.com/vi/R_6fW1tVj8Y/hqdefault.jpg)](https://youtu.be/R_6fW1tVj8Y)
