---
title: "생성자 DI"
date: 2020-07-19 13:53:07 +00:00
categories: Development
tags: Spring LectureNote
---

Constructor-arg 속성 이용

오버로드 생성자 생성 : 소스 영역에서 오른쪽 마우스 클릭 - source - Generating Constructor with Fields, 원하는 필드들 선택하고 generate

![image](https://user-images.githubusercontent.com/24868649/87867400-634eb980-c9c7-11ea-8675-50add8d3f9b6.png)

자동 생성된 Super는 삭제

순서대로 입력하여 그대로 생성자를 통해 초기화할 수 있음

헷갈릴 수 있기 때문에 인덱스 지정도 가능

이를 확인하기 위해 toString 함수 구현

자동으로 만드는 방법 : 소스 영역에서 오른쪽 마우스 클릭 - Source - Generating toString() 클릭 - 원하는 Field 선택

toString()을 활용해서 순서를 바꿔서 세팅한 것을 확인할 수 있음

![image](https://user-images.githubusercontent.com/24868649/87867411-795c7a00-c9c7-11ea-9023-27eeefa969af.png)

순서대로 넣기, Index 지정을 통해 넣기, name 지정을 통해 넣기, type 지정을 통해 넣기 정리

![image](https://user-images.githubusercontent.com/24868649/87867415-8711ff80-c9c7-11ea-88e1-7cdd31656bda.png)

처리기를 통해 p 속성을 통해 단일 태그에 바로 초기화할 수 있게 하기 위해 namespaces영역에서 p의 체크박스 체크, 오류 메시지는 변경으로 인해 삭제 혹은 추가될 수 있다는 내용으로 그냥 확인 클릭

![image](https://user-images.githubusercontent.com/24868649/87867419-94c78500-c9c7-11ea-8cd9-128af310b865.png)

Namespace가 추가되고 p:kor쪽에 더 이상 오류 뜨지 않음

![image](https://user-images.githubusercontent.com/24868649/87867427-a741be80-c9c7-11ea-8657-4c317fc90649.png)

모듈이라는 단위, 같은 객체명을 가질 수 있으니 이를 구분하는 성과 같은 개념

즉, 성이 Namespace, 확장된 이름

Ex. 같은 문서에 bean이 두 개일 수 있음, Namespace를 사용하면 자기가 처리하는 Namespace가 아니면 무시하고 지나감

Namespace의 용도

1. 태그가 특정한 처리기에 의해서 처리될 수 있게 함

2. 태그 이름을 식별하기 위해 씀

![image](https://user-images.githubusercontent.com/24868649/87867448-bd4f7f00-c9c7-11ea-8170-36d20879fbb9.png)

즉P가 담당한 태그이다라는 것을 추가한 것이라고 볼 수 있음

![image](https://user-images.githubusercontent.com/24868649/87867457-c9d3d780-c9c7-11ea-87d4-fdcd63e2ca7a.png)

이런 것들을 Bean과 같은 태그 앞에도 쓸 수 있음 ex. p:bean

참고 영상  
[![Watch the video](https://img.youtube.com/vi/K_4xDEeDvk8/hqdefault.jpg)](https://youtu.be/K_4xDEeDvk8)
