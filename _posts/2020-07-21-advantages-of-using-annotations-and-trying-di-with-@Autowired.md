---
title: "어노테이션을 이용할 때의 장점과 @Autowired를 이용한 DI 해보기"
date: 2020-07-21 23:25:23 +00:00
categories: Development
tags: Spring LectureNote
---

설정 파일을 지정하는 방법

1. 외부에 xml 파일 두기

2. 내부 코드에 Annotation(설정 정보)으로 심기 -> 자바 강의 듣기

DI하는 부분을 Annotation으로 바꿔볼 예정

스프링 관련 어노테이션들

![image](https://user-images.githubusercontent.com/24868649/88067370-db74d500-cba9-11ea-9621-5eddaad41297.png)

설정 파일을 수정하는 것도 귀찮아짐

Annotation을 사용했을 때 객체를 바꿔버리면 코드도, 설정도 바뀌게 함

객체 생성은 다음 시간에 배울 것

객체에 객체를 DI하는 것을 일단 어노테이션으로 해볼 것(@Autowired)

xml 파일쪽 주석 처리

![image](https://user-images.githubusercontent.com/24868649/88067431-f2b3c280-cba9-11ea-9d68-bdfb607993d0.png)

java 파일쪽 주석 처리

![image](https://user-images.githubusercontent.com/24868649/88067531-124aeb00-cbaa-11ea-8fd6-cba8be3309e7.png)

이대로 실행 시 NullPointerException 발생

![image](https://user-images.githubusercontent.com/24868649/88067577-20007080-cbaa-11ea-8b29-d8f42a711b45.png)

실제로 DI가 안된 것을 확인한 것임

![image](https://user-images.githubusercontent.com/24868649/88067641-36a6c780-cbaa-11ea-9785-dd91548d761e.png)

setter쪽에 Annotation을 추가함, 하지만 그래도 NullPointerException이 발생

![image](https://user-images.githubusercontent.com/24868649/88067682-41f9f300-cbaa-11ea-98cf-a238ff95ff1b.png)

굳이 Class 안에 Autowired Annotation을 찾으려 하지 않기 때문임

지시서에 그걸 찾아달라는 것을 추가해야 함

Namespaces에서 context 체크

![image](https://user-images.githubusercontent.com/24868649/88067706-4b835b00-cbaa-11ea-854c-e93b3510b5a2.png)

xml 파일에 다음과 같은 처리기 추가됨

![image](https://user-images.githubusercontent.com/24868649/88067752-576f1d00-cbaa-11ea-8d28-aba7b170df93.png)

태그 추가

![image](https://user-images.githubusercontent.com/24868649/88067776-5fc75800-cbaa-11ea-9719-508b66901cf4.png)

객체들이 Annotation을 갖고 있다는 뜻

정상 실행됨

![image](https://user-images.githubusercontent.com/24868649/88067842-72419180-cbaa-11ea-9c42-8cf44375ab50.png)

xml 설정 파일에서 ref 속성을 통해 exam을 참고했던 것과 다르게 Annotation은 뭐를 근거로 바인딩을 한 것일까? -> 다음 시간

참고 영상  
[![Watch the video](https://img.youtube.com/vi/S065KRjXRSY/hqdefault.jpg)](https://youtu.be/S065KRjXRSY)
