---
title: "XML Configuration을 Java Configuration으로 변경하기"
date: 2020-07-26 23:49:05 +00:00
categories: Development
tags: Spring LectureNote
---

xml을 통해 했었음 -> 이제 Annotation을 사용
몇개 남지 않은 xml 설정도 모두 어노테이션으로 바꿀 것임

개발 단계에서는 xml로만 할건지 어노테이션으로 할건지 골라야 함
지시서를 자바 클래스로 만들 것임
xml 파일이 자바 파일로 바뀌는 것임
- @Configuration 어노테이션을 통해 클래스 설정
- 순서는 중요하지 않으며 그 위에 @ComponentScan 설정
- 두 가지 이상의 package를 참고할 경우 자바 문법에 따라 배열 형태로 추가

entity에 있던 어노테이션은 지웠기 때문에 spring.di.entity는 삭제
bean의 경우는 @Bean이라는 어노테이션을 써줌
함수를 직접 생성하는 것처럼 보이지만 그렇지 않음
IoC는 공유하는 객체가 담긴 컨테이너로 거기서 꺼내보는 것임
메소드의 이름이 보통 동사형이나 여기선 exam이라는 명사형임에 주목
함수명이 아닌 컨테이너에 담겨졌을 때의 이름이라고 생각해야 함, 실제 bean의 id와 대응됨

함수명을 가지고 있다 해서 기능함수라 생각하지 말고 이름을 통해 가지고 있음을 인지하기
NewlecDIConfig라는 config용 class 파일을 만들고 xml 파일의 내용에 대응하는 class 파일을 작성, 이때 getExam 등의 동사형태의 함수명을 쓰지 말고 명사형태의 함수명을 쓰는 것에 유의

xml을 사용하는 3가지의 방식이 있었음
이제는 그 아래의 자바 파일을 통한 config 파일을 쓰는 AnnotationConfigApplicationContext를 사용하여 작성

아래와 같이 어노테이션을 통해서 변경 가능하게 됨

여러개의 config 파일을 만들어 쓸 수 있음, register라는 함수 이용
여러번 호출하거나 ,(콤마)를 이용해 구분해서 넣을 수 있음


register 함수를 통해 설정하는 방법으로 써보고 결과가 나온 모습

참고 영상  
[![Watch the video](https://img.youtube.com/vi/XzrXZIRB1vM/hqdefault.jpg)](https://youtu.be/XzrXZIRB1vM)
