---
title: "간소화된 Advisor"
date: 2020-08-10 21:24:09 +00:00
categories: Development
tags: Spring LectureNote
---

PointCut을 위해 Advisor가 필요했었는데 이 설정을 간소화하고 싶음

![image](https://user-images.githubusercontent.com/24868649/89782460-49307300-db50-11ea-82f5-3f26f2cbd18a.png)

- Advisor와 PointCut이 결합된 형태의 Advisor를 사용할 수 있음

- 결합되면서 PointCut의 내용이 Advisor의 안으로 들어감

![image](https://user-images.githubusercontent.com/24868649/89782888-058a3900-db51-11ea-80c7-4a94a3bf65b0.png)

- 이전 코드는 주석 처리하고 Advisor 내용을 복사해 결합된 Advisor를 만듦

- PointCut의 이름을 Advisor 앞에 붙여놓음

- property 태그를 이용해 total과 연결

![image](https://user-images.githubusercontent.com/24868649/89782910-1044ce00-db51-11ea-94b3-cfbcb8e60041.png)

- 실행 시 오류가 나게 되는데 PointCut을 다른 곳에서 쓰고 있었기 때문임

![image](https://user-images.githubusercontent.com/24868649/89782939-189d0900-db51-11ea-93d7-72accfda1420.png)

- 예전의 코드들은 모두 주석 처리하고 앞서 설정한 것과 동일하게 만들어줌

![image](https://user-images.githubusercontent.com/24868649/89782961-1f2b8080-db51-11ea-9831-c1ba57126538.png)

- 실행해보면 total 함수에 대해서만 Around, Before Advice가 실행된 것을 볼 수 있음

![image](https://user-images.githubusercontent.com/24868649/89782984-26528e80-db51-11ea-86bd-a93dbe8073bc.png)

- mappedName's'라는 것으로 바꾸면 여러 개의 PointCut에 대해서 Advisor를 추가할 수 있음

![image](https://user-images.githubusercontent.com/24868649/89783003-2fdbf680-db51-11ea-81c8-7fcab85eab06.png)

- avg에도 Around Advisor가 추가된 것을 볼 수 있음

- 강의에서는 Before Advisor에 추가했음

패턴으로 할 수 있진 않을까?

![image](https://user-images.githubusercontent.com/24868649/89783020-37030480-db51-11ea-84fa-047264964c6f.png)

- 정규식 패턴을 사용할 수 있음 PointCut을 새로 설정

- 정규식의 의미 .(온점) : 어떠한 캐릭터, *(별표) : 캐릭터가 0개 이상 나올 수 있음, .*(온점과 별표) : 어떠한 캐릭터가 0개 이상 나올 수 있음

- patterns라는 name으로 바꿔주며 class도 RegexpMethodPointCutAdvisor로 바꿔줌

![image](https://user-images.githubusercontent.com/24868649/89783187-7af60980-db51-11ea-8074-68b3457de2b4.png)

- 실행해보면 total에 대해서만 Around Advisor가 호출된 것을 확인할 수 있음

- 정규식 이외에도 스프링이 나오기 전부터 있었던 표현 방법이 존재 (AspecJ)

실질적으론 어노테이션을 통해 쓰므로 다음 시간에는 어노테이션을 통한 Advisor 설정을 알아볼 것


참고 영상  
[![Watch the video](https://img.youtube.com/vi/uPHMcE5iVcY/hqdefault.jpg)](https://youtu.be/uPHMcE5iVcY)
