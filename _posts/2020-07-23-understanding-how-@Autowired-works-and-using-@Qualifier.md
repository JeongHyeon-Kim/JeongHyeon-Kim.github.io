---
title: "어노테이션을 이용한 객체생성"
date: 2020-07-23 23:40:37 +00:00
categories: Development
tags: Spring LectureNote
---

xml에서 객체를 생성하던 부분을 Annotation을 통해 만들 수 있도록 바꿔볼 것임

![image](https://user-images.githubusercontent.com/24868649/88300962-0d6b7000-cd3f-11ea-9f06-542abd5eb360.png)

xml에서 InlineExamConsole이라는 객체를 생성하는 부분을 지우고 해당 클래스의 윗부분에 @Component라는 Annotation을 지정해줘 객체가 자동으로 생성될 수 있게 해줌. 단, xml에서는 객체가 생성된다는 내용이 없으므로 단순하게 @Component만 쓰는 것이 아닌 @Autowired Annotation처럼 설정이 필요함. component-scan이라는 설정을 통해 spring.di.ui라는 패키지에서 한번 component가 있는지 쭉 스캔해주라는 의미로 추가함

![image](https://user-images.githubusercontent.com/24868649/88300929-02b0db00-cd3f-11ea-9e41-b24bcb07621a.png)

스캔 뒤에 있으면 객체화 시켜주게 됨

이 과정에서 annotation-config는 객체가 생성되고 그 안을 들여다 보라는 의미인데 scan 과정에서 안을 들여다보므로 필요 없어지게 됨

![image](https://user-images.githubusercontent.com/24868649/88300903-fb89cd00-cd3e-11ea-8925-7dd32b91f3ac.png)

아래와 같이 주석처리를 하여 xml에서는 더 이상 객체를 생성하는 부분이 없게 만듦

![image](https://user-images.githubusercontent.com/24868649/88300884-f4fb5580-cd3e-11ea-99a2-de69db5ef380.png)

앞서 예상했듯 @Component라는 Annotation은 지시서에서는 인식하지 못하므로 에러가 뜸

console이라는 이름을 아는 것은 Program.java 파일에서 console이라는 이름으로 객체를 가져오려고 하기 때문임

![image](https://user-images.githubusercontent.com/24868649/88300857-eca31a80-cd3e-11ea-8063-2a1ae5819d8e.png)

패키지는 spring.di.ui이므로 이 안을 뒤져봐라 하는 의미로 xml에 추가함

![image](https://user-images.githubusercontent.com/24868649/88300784-d5642d00-cd3e-11ea-8e48-636206c9b87a.png)

![image](https://user-images.githubusercontent.com/24868649/88300778-d301d300-cd3e-11ea-8c2a-41bda9962103.png)

그래도 에러가 나게 되나 이번엔 에러 메시지가 다름

console이라는 이름 자체도 없어졌으므로 이름으로는 찾을 수 없음

따라서 ExamConsole이라는 인터페이스 형식에 맞게 찾게 하는 방법을 통해 실행되게 할 수 있음

![image](https://user-images.githubusercontent.com/24868649/88300748-caa99800-cd3e-11ea-8d08-ac3d3ac0aa58.png)

다음과 같이 어노테이션을 통해서도 이름을 줄 수 있음

xml의 id 대신 @Component의 옵션으로 주는 것임

![image](https://user-images.githubusercontent.com/24868649/88300619-a77ee880-cd3e-11ea-8235-7bf3f09461ea.png)

정상 작동됨

![image](https://user-images.githubusercontent.com/24868649/88300604-a352cb00-cd3e-11ea-8e33-82126574b0c2.png)

위에서는 Autowired가 되지 않았으므로 이를 되게 하기 위해선 exam2로 지정해줬던 Qualifier를 지우고 component-scan에 패키지를 추가함

![image](https://user-images.githubusercontent.com/24868649/88300584-9afa9000-cd3e-11ea-8b8c-bf1cf68da76a.png)

![image](https://user-images.githubusercontent.com/24868649/88300580-9930cc80-cd3e-11ea-93df-91393fb8bc36.png)
 
생성될 NewlecExam 객체에도 @Component 어노테이션을 설정해줌

![image](https://user-images.githubusercontent.com/24868649/88300567-9504af00-cd3e-11ea-8dcf-8e2b731204e4.png)

그래도 같은 결과가 나오는데 이는 binding이 되지 않아 exam이 null이여서 나오는 게 아니라 위에서 볼 수 있듯 NewlecExam객체 생성자에서 아무런 작업을 안했기 때문임

확인하는 방법은 Autowired에서 required를 빼고 entity 패키지의 범주를 빼면 에러가 나는데 범주에 넣어주게 되면 정상 출력됨

![image](https://user-images.githubusercontent.com/24868649/88300541-8d450a80-cd3e-11ea-9a1b-555b31f80a21.png)

이렇게 xml에서 객체 생성하는 것까지도 어노테이션을 통해 할 수 있다

참고 영상  
[![Watch the video](https://img.youtube.com/vi/DNrkw3pAsAM/hqdefault.jpg)](https://youtu.be/DNrkw3pAsAM)
