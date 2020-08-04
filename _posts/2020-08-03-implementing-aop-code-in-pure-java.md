---
title: "순수 자바로 AOP 코드 구현하기"
date: 2020-08-03 23:56:05 +00:00
categories: Development
tags: Spring LectureNote
---

AOP를 통해 곁다리 업무를 만들어볼 것

main함수를 포함해서 spring.aop라는 패키지명으로 Program이라는 새로운 클래스 추가

![image](https://user-images.githubusercontent.com/24868649/89304487-72608780-d6a8-11ea-9ed3-70eefbd2c8c3.png)

AOP를 하기에 앞서 주업무로직이 필요한데 이전에 썼었던 spring.di.entity를 활용

패키지에 대고 ctrl + C, V 하면 복사할 수 있음

![image](https://user-images.githubusercontent.com/24868649/89306340-b2c10500-d6aa-11ea-9993-2aa4fb607a0a.png)

이름을 적절하게 수정

![image](https://user-images.githubusercontent.com/24868649/89307693-55c64e80-d6ac-11ea-9e64-a78b579a7e60.png)

spring.aop.entity 패키지에 NetlecExam.java 파일로 가서 이제 필요 없어진 내용들은 지우고 어노테이션을 쓰기 위해 import된 것들도 ctrl + shift + o를 눌러 없애줌

곁다리 업무를 추가하기 위해 total 함수와 avg함수를 수정함

![image](https://user-images.githubusercontent.com/24868649/89307718-5eb72000-d6ac-11ea-9b6c-9a24c226bf96.png)

본격적으로 Program.java에서 주업무를 불러보도록 함

가져올 때 패키지명에 주의하기

![image](https://user-images.githubusercontent.com/24868649/89307750-68408800-d6ac-11ea-81ac-23de8eae4615.png)

마찬가지로 Exam 인터페이스도 패키지명에 유의해서 패키지 import하기

간단하게 생성자를 통해 초기화를 하고 총합을 출력하는 주업무 로직을 생성

여기까지가 사용자가 원하는 로직

![image](https://user-images.githubusercontent.com/24868649/89307793-7393b380-d6ac-11ea-8109-2b7109681f5a.png)

예를 들어 성능 이슈가 있어 확인을 해봐야 한다고 가정

사용자가 필요로 하는 주 업무 로직 앞과 뒤로 테스트를 위한 코드를 직접 넣는 것을 해봄

쓰레드를 통해 sleep되도록 하며 시작과 끝에 시간을 확인해서 걸린 시간을 출력

![image](https://user-images.githubusercontent.com/24868649/89307968-ac338d00-d6ac-11ea-8774-65ccc75527b0.png)

여기서 해본 것이 옛날에 소스 코드에 직접 꽂아 넣는 업무였음

AOP라는 것은 꽂아 놓지 않고 곁다리 업무를 따로 만들어서 연결하겠다임

연결할 수 있는 Proxy라는 도구를 사용

자바에서 기본적으로 Proxy를 제공중임

첫번째 인자는 실제로 불릴 객체를 클래스 형태로 넣어줌

두번쨰 인자는 인터페이스를 넣어주되 복수개가 들어갈 수 있으므로 배열 형태로 넣어줌

마지막 인자는 곁다리 업무가 들어갈 자리임

![image](https://user-images.githubusercontent.com/24868649/89308006-b5bcf500-d6ac-11ea-8ff8-709baa55f1e6.png)

그림에서 동그라미 부분을 구현하는데 마지막 인자는 InvocationHandler를 넣어주는 것임

![image](https://user-images.githubusercontent.com/24868649/89308016-ba81a900-d6ac-11ea-98ff-1c1f2e72cfa6.png)

별도의 클래스 파일을 만들지 않고 익명 클래스를 직접 작성해서 만들도록 함

ctrl + space bar를 통해 InvocationHandler를 익명 클래스를 만듦

- 이전의 곁다리 업무 코드들을 이곳으로 가져오며 주업무 로직을 호출하기 위해 두번째 인자인 method의 invoke함수를 활용하여 부르도록 함

- invoke함수의 첫번째 인자는 주 실제 업무 객체인 exam를 넣어주게 되고 두번째 인자는 total이나 avg를 호출할 수 있을텐데 그를 위한 파라미터를 args로 넘겨주게 되므로 이를 써줌

- 이렇게 불리게 되면 주업무 로직을 타게 된 이후 반환값이 있을텐데 그것도 돌려줘야 하므로 모든 형태의 값을 받을 수 있게 Object라는 형태로 반환

- Loader를 넘겨주기 위해 class 뒤에 getClassLoader를 넣어줌

- Object 형식으로 반환하므로 Exam으로 형변환

- proxy를 이용해 total 호출

![image](https://user-images.githubusercontent.com/24868649/89308050-c7060180-d6ac-11ea-97c6-cee50310c476.png)

위와 같이 곁다리 업무 로직이 포함돼 결과 확인 가능

exam.total()로 바꾸면 주업무로직만 호출됨

![image](https://user-images.githubusercontent.com/24868649/89308073-cc634c00-d6ac-11ea-8f53-ce3d3deb9744.png)

인터페이스를 공유하고 있는 다른 함수들도 proxy를 통해 끼워넣어서 호출 가능

![image](https://user-images.githubusercontent.com/24868649/89308085-cff6d300-d6ac-11ea-9db2-faf6b4e70c7c.png)

이런게 AOP 방식, proxy를 통해 곁다리 업무를 따로 떼어놓고 끼워넣거나 뺄 수 있음

참고 영상  
[![Watch the video](https://img.youtube.com/vi/pr2dwdf_03k/hqdefault.jpg)](https://youtu.be/pr2dwdf_03k)
