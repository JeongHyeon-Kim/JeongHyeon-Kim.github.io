---
title: "@Autowired의 동작방식 이해와 @Qualifier 사용하기"
date: 2020-07-22 23:38:31 +00:00
categories: Development
tags: Spring LectureNote
---

DI를 대신하는 Annotation

그 안을 들여다 봐라 -> Annotation 확인

Exam이라는 객체를 찾아서 자동으로 꽂아라라는 것

무슨 기준일까? 이름 or 객체 타입

확인을 위해 방해가 되는 코드는 주석 처리하고 두 줄만 남겨둠

![image](https://user-images.githubusercontent.com/24868649/88190971-e72dcd80-cc75-11ea-80e0-e5057131866a.png)

설정 파일에 따라 객체 생성 이후 그냥 지나가지 않고 객체 내부에 Annotation이 있는지 확인하게 됨

![image](https://user-images.githubusercontent.com/24868649/88191009-ef860880-cc75-11ea-9e2a-04014815c0a2.png)

해당되는 함수에 @Autowired Annotation을 작성해줘 자동으로 DI를 할 수 있도록 함

![image](https://user-images.githubusercontent.com/24868649/88191034-f6ad1680-cc75-11ea-8c68-61cc4364b83a.png)

위의 상태로 실행하면 잘 동작하는 것 확인

변수명을 토대로 검사하는지 확인용

![image](https://user-images.githubusercontent.com/24868649/88191064-00cf1500-cc76-11ea-85ea-7581d000e511.png)

에러가 나면 안되지만 에러가 나게 됨, 참조를 하는 지시서의 내용이 있기 때문임, 해당 부분을 삭제하여 테스트

![image](https://user-images.githubusercontent.com/24868649/88191255-33790d80-cc76-11ea-893c-d5bc5c321bfb.png)

이후 확인해보면 정상 작동하는 것을 볼 수 있음 -> 이름이 아닌 객체 타입으로 구분한다는 결론

심지어 이름(id)을 아예 없어도 바인딩이 잘됨

![image](https://user-images.githubusercontent.com/24868649/88191324-4855a100-cc76-11ea-8398-0e2fbc53613c.png)

Exam이라는 인터페이스와 부합/참조할 수 있는 객체를 자동으로 찾아와 바인딩을 해주는 것임

아래와 같이 같은 객체를 생성하려고 하려면 만족할 수 있는 디펜던시를 찾다가 두개가 나와 되지 않게 됨

![image](https://user-images.githubusercontent.com/24868649/88191346-4ee41880-cc76-11ea-911c-a2b1d9f04a46.png)

#0과 #1 객체가 있어 못해먹겠다는 에러가 발생함

그럼 이름을 지정해주면 어떨까?

![image](https://user-images.githubusercontent.com/24868649/88191365-54d9f980-cc76-11ea-94c9-d07f1f90e513.png)

모호한 객체에 위와 같이 이름으로 구분해주면 정상 동작함

이름을 다시 구분하지 못하는 것으로 바꾸면 에러가 나는 것을 확인할 수 있음

![image](https://user-images.githubusercontent.com/24868649/88191384-5a374400-cc76-11ea-82f5-1a05bca4a921.png)

구분할 때 먼저 객체의 형식으로 구분하고 그 구분이 모호하면 이름(변수명)을 통해 구분 짓는다

따라서 이 상태에서도 오류가 나기 마련임, 객체는 동일하기 때문 -> @Qualifier Annotation을 통해 해결

![image](https://user-images.githubusercontent.com/24868649/88191419-61f6e880-cc76-11ea-8e6a-11b330ce7af6.png)

객체가 같을 때 어떤 아이를 쓸꺼다라는 것을 지정, exam1에 대한 결과가 나옴(total 20)

![image](https://user-images.githubusercontent.com/24868649/88191484-74712200-cc76-11ea-84d6-18949279d51d.png)

exam2로 바꾸면 total 40으로 나옴

![image](https://user-images.githubusercontent.com/24868649/88191515-789d3f80-cc76-11ea-9ceb-66cad963452b.png)

결론: Autowired가 자동으로 DI해주는 좋은 것인데 기본적으로 어떤 것을 통해 구분하는지 알아봤다. 자료형식이 기본 이름으로 구분 되는데 함수의 변수명으론 구분하는 게 한계가 있으니 Qualifier로 구분한다.

참고 영상  
[![Watch the video](https://img.youtube.com/vi/Od-WtriilwY/hqdefault.jpg)](https://youtu.be/Od-WtriilwY)
