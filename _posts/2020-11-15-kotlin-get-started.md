---
title: "Kotlin 언어 배우기"
date: 2020-11-15 15:17:35 +00:00
categories: Development
tags: Kotlin LectureNote
---

Variable declaration
- var: 변수 선언
- val: 상수 선언
- Type inference
  - 정적으로 입력되는 언어, 컴파일 시간에 유형이 결정
  - 예시)
  ```
  val languageName: String = "Kotlin"
  val uppperCaseName = languageName.toUpperCase() (O)
  languageName.inc() (X) // int 연산자 함수
  ```
- Null safety
  - 일반적인 선언으로 Null 할당 불가
  - 예시)
  ```
  val languageName: String = null (X)
  val languageName: String? = null (O) // nullable 유형 지정
  ```

Conditional
- C++과 기본적인 사용법은 동일
- 삼항 연산자가 없는 대신 아래의 기능을 제공
- 변수에 직접적으로 사용 가능
  - 예시)
  ```
  val answerString: String = if (count == 42) {
      "I have the answer."
  } else if (count > 35) {
    "The answer is close."
  } else {
    "The answer eludes me."
  }
  println(answerString)
  ```
- 조금 더 복잡해질 시 *when* 표현식 사용 가능
  - 조건 -> 결과로 표현
  - 예시)
  ```
  val answerString = when {
    count == 42 -> "I have the answer."
    count > 35 -> "The answer is close."
    else -> "The answer eludes me."
  }

  println(answerString)
  ```

참고 문서
[[Kotlin 프로그래밍 언어 알아보기]](https://developer.android.com/kotlin/learn#conditionals)
