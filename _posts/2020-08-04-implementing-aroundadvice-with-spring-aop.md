---
title: "스프링 AOP로 AroundAdvice 구현하기"
date: 2020-08-04 22:53:33 +00:00
categories: Development
tags: Spring LectureNote
---

스프링 버전의 AOP 만들어볼 것

지난 번에 만들었던 코드 확인

![image](https://user-images.githubusercontent.com/24868649/89302730-2b719280-d6a6-11ea-8680-2c62d5af8a5b.png)

- 로그 출력을 위해 위와 같은 곁다리 코드들 삽입할 수 있음

- 더 이상 필요없게 되면 제거하거나 다른 곁다리 로직을 넣을 수 있어야 함

- 코드 상에서 이런 로직들을 직접적으로 넣게 되면 자유롭게 제거/삽입이 불가능함

분리해서 작성하는 것이 AOP 방법론

![image](https://user-images.githubusercontent.com/24868649/89303045-991dbe80-d6a6-11ea-86ea-94153cfa18d1.png)

- 쉽게 유지보수 가능

- 주업무 부분을 Core Concern, 곁다리 업무 부분을 Cross-cutting Concern 부분으로 분리
지난 시간엔 자바의 Proxy를 사용해서 구현

![image](https://user-images.githubusercontent.com/24868649/89303099-acc92500-d6a6-11ea-9a4d-e59963fdc190.png)

- AOP에는 반드시 Proxy가 필요

- Proxy에 곁다리 업무를 작성

- 실제 주업무에는 곁다리 업무 작성 안함

- 이런 구성을 스프링을 사용하면 편해질까? 그렇다, 스프링을 통해 쉽게 구현 가능

- Proxy+Cross-cutting Concern+Core Concern, 이렇게 필요한 3박자가 갖춰져야 함

- 스프링이 제공하는 Proxy가 존재

- IoC 컨테이너를 활용해서 수행

- 위의 3가지의 객체를 뺏다 꽂았다 할 수 있게 활용가능한 게 IoC 컨테이너임

곁다리 업무가 필요한 곳에 따라 스프링에서는 총 네가지의 종류로 구분해서 처리하고 있음

![image](https://user-images.githubusercontent.com/24868649/89303167-c8343000-d6a6-11ea-9a70-0ef59b03654d.png)

- 앞에만 필요한 곁다리 업무(Before Advice)

- 뒤에만 필요한 곁다리 업무(After Advice)

- 예외를 처리하는 곁다리 업무(After throwing Advice)

- 앞뒤 모두 필요한 곁다리 업무(Around Advice)

- 이 네가지중 내가 구현하고자 하는 형태와 맞는 것으로 인터페이스를 상속 받아 구현함

- 이번 시간엔 Around Advice를 활용해서 지난 시간에 작성한 코드를 변경해볼 것

![image](https://user-images.githubusercontent.com/24868649/89303536-4abcef80-d6a7-11ea-8373-9c5557b64230.png)

- Spring을 쓰기 위해 설정 작업을 수행

- 우선 setting.xml 파일을 aop 패키지 쪽에 복사/붙여넣기함

![image](https://user-images.githubusercontent.com/24868649/89303557-51e3fd80-d6a7-11ea-8602-4e09045954e3.png)

- Program.java 파일에서도 필요한 내용 복사해서 붙여넣기함

- xml을 이용하는 방법과 annotation을 이용하는 방법 모두 사용할 예정

![image](https://user-images.githubusercontent.com/24868649/89303572-590b0b80-d6a7-11ea-9f49-3f1e96eb6830.png)

- 복사한 코드를 수정하여 오류가 없도록 작성

- 경로 변경(spring/aop/setting.xml)

- 객체 변경(ApplicationContext) 및 자동 Import(ctrl+shift+o)

![image](https://user-images.githubusercontent.com/24868649/89303602-61fbdd00-d6a7-11ea-947e-7f2d28dd12e4.png)

- 이제 setting.xml 파일을 수정하여 위의 세가지 코드를 작성할 것

![image](https://user-images.githubusercontent.com/24868649/89303623-67592780-d6a7-11ea-9325-45dd542bb313.png)

- 필요 없는 코드들 삭제, NewlectExam 클래스의 위치를 di 패키지에서 aop 패키지로 수정

- 초기값을 math, com도 추가

- tip: bean의 class를 찾을 때는 오타 등으로 인해 잘못 생성할 수 있으니 .java파일에서 찾아서 쓰기, Proxy를 만드는 bean 생성

- setTarget이라는 setter 함수를 만들기 위한 target이라는 이름의 property 생성

- 곁다리 업무 코드를 작성하기 위한 LogAroundAdvice새로운 클래스 생성 및 bean 태그 추가

- target은 value인지 ref인지 판단했을 때 참조형이므로 ref로 부름

- 클래스명은 class이기 때문에 첫문자는 대문자로 작성

- interceptorNames 속성을 활용하여 복수형으로 여러개의 곁다리 업무 코드를 가질 수 있으며 list 태그를 통해 객체를 추가할 수 있음

![image](https://user-images.githubusercontent.com/24868649/89303655-70e28f80-d6a7-11ea-9f78-1f7ae14fe0c3.png)

- 곁다리 코드를 위한 aop.advice라는 것으로 분리

- 클래스의 이름의 첫글자는 대문자인 것 확인

![image](https://user-images.githubusercontent.com/24868649/89303676-78099d80-d6a7-11ea-8994-8eaf0c113766.png)

- implements 찾을 시 여러 패키지가 있는데 org.aopalliance.intercept로 잘 추가하기

![image](https://user-images.githubusercontent.com/24868649/89303693-7d66e800-d6a7-11ea-8e6b-4602c965ec81.png)

- 위와 같은 예전 코드가 아래와 같이 바뀜

![image](https://user-images.githubusercontent.com/24868649/89303714-83f55f80-d6a7-11ea-9cf7-9fe31e84592d.png)

- exam, args같은 파라미터가 사라지고 proceed 함수로 깔끔하게 대체됨

![image](https://user-images.githubusercontent.com/24868649/89303739-8b1c6d80-d6a7-11ea-8a69-693299fd4248.png)

- 결합하는 부분을 xml 설정으로 뺀 게 특징이며 결합을 자유롭게 바꿀 수 있음

![image](https://user-images.githubusercontent.com/24868649/89303757-91124e80-d6a7-11ea-8b67-2789e81e46d5.png)

- 이전 코드는 주석 처리하고 실행해보면 에러가 뜸

![image](https://user-images.githubusercontent.com/24868649/89303772-97a0c600-d6a7-11ea-8e56-ff01528569f1.png)

- advice라는 패키지 경로를 추가해서 그런 것으로 xml 설정파일에서 수정

![image](https://user-images.githubusercontent.com/24868649/89303792-9cfe1080-d6a7-11ea-91e9-7ef66ab5b9f5.png)

- 수정하고 나면 정상적으로 업무 로직과 함께 로그 출력됨

![image](https://user-images.githubusercontent.com/24868649/89303805-a25b5b00-d6a7-11ea-8085-df2130692deb.png)

- proxy라는 명명을 exam으로 바꿈

- 소스 코드에선 로그 출력을 위한 객체라는 것을 알 수가 없게 됨

![image](https://user-images.githubusercontent.com/24868649/89303823-a8513c00-d6a7-11ea-8a04-f1e4420e0951.png)

- xml 파일에서도 proxy에서 exam으로 바꿈

![image](https://user-images.githubusercontent.com/24868649/89303839-ad15f000-d6a7-11ea-9249-88c358a619c9.png)

- 결과를 출력해보면 정상적으로 로그와 함께 결과가 출력됨

![image](https://user-images.githubusercontent.com/24868649/89303855-b3a46780-d6a7-11ea-985f-a3b9e10fde8b.png)

- 소스 코드는 exam이라는 객체로 두고 곁다리 업무는 필요 없을 땐 주석 처리할 수 있음

![image](https://user-images.githubusercontent.com/24868649/89303872-b901b200-d6a7-11ea-88c8-2b113b027e9a.png)

- 로그 처리 부분을 주석 처리해도 주업무 로직은 정상 동작함

- 소스 코드의 변경 없이 설정 파일 변경을 통해 로그 출력 여부를 결정할 수 있음을 확인

참고 영상  
[![Watch the video](https://img.youtube.com/vi/eHYPujubB3E/hqdefault.jpg)](https://youtu.be/eHYPujubB3E)
