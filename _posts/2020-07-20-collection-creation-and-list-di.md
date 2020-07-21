---
title: "콜렉션 생성과 목록 DI"
date: 2020-07-20 23:50:23 +00:00
categories: Development
tags: Spring LectureNote
---

대표적인 콜렉션 : ArraList

![image](https://user-images.githubusercontent.com/24868649/87952083-5673b800-cae4-11ea-9a0b-f7701f613993.png)

이런 식으로 코드를 짤 수 있는데 setting.xml을 통해서도 만들어보자

Program.java

![image](https://user-images.githubusercontent.com/24868649/87952178-77d4a400-cae4-11ea-84eb-06a384e72cbb.png)

Setting.xml

![image](https://user-images.githubusercontent.com/24868649/87952216-87ec8380-cae4-11ea-8b5f-68b7db31634a.png)

이와 같이 ArrayList 형식 역시 DI를 통해 생성할 수 있음

DI를 통해 콜렉션의 setter 구현

Add는 setter가 아니라 그걸로는 안됨

ArrayList의 사용법을 확인해보면 생성자에 collection을 대입하는 방식으로 객체를 추가할 수 있음

![image](https://user-images.githubusercontent.com/24868649/87952287-9b97ea00-cae4-11ea-8991-5274c11bfdaa.png)

ArrayList 생성자의 사용법을 활용해 DI를 통해 객체들을 생성하고 삽입함

직접 bean들을 입력할 수도 있고 ref 태그를 통해 이미 만들어진 bean을 참조할 수 있음

![image](https://user-images.githubusercontent.com/24868649/87952337-aa7e9c80-cae4-11ea-88c4-b7ff6ff0dbdf.png)

setting.xml에서 추가했기 때문에 생략 가능

![image](https://user-images.githubusercontent.com/24868649/87952374-b66a5e80-cae4-11ea-81e9-f70ac5368f02.png)

생성자를 통해서 List를 만드는 것이 아닌 별도의 객체로는 만들 수 없을까?

아래와 같은 방법으로 가능

Namespaces에서 util 항목을 체크

![image](https://user-images.githubusercontent.com/24868649/87952417-c5511100-cae4-11ea-9664-08ac5399d904.png)

util관련 전처리기가 추가됨

![image](https://user-images.githubusercontent.com/24868649/87952469-d1d56980-cae4-11ea-9038-72affaefd997.png)

이후 list라는 태그에 util이라는 전처리기 표시를 하여 따로 List 객체를 생성할 수 있음

consturctor-arg 안에서 사용되는 태그와는 다름

다른 전처리기를 통해 처리되는 것임

![image](https://user-images.githubusercontent.com/24868649/87952497-dac63b00-cae4-11ea-9dc3-a70b71abd6d0.png)

이런식으로 컬렉션을 만들 수 있음

여러 클래스가 있으므로 그것을 지정해줘야 하며 이름도 필요함

![image](https://user-images.githubusercontent.com/24868649/87952550-e87bc080-cae4-11ea-899b-d7f348258c89.png)

이전 코드는 주석처리하여 확인하면 정상 작동됨

참고 영상  
[![Watch the video](https://img.youtube.com/vi/0ktRT5Fatnw/hqdefault.jpg)](https://youtu.be/0ktRT5Fatnw)
