---
layout: post
title: "제네릭 타입을 사용하는 이유"

categories: JAVA
tags: JAVA
---

제네릭 타입은 클래스나 메소드를 선언할 때 타입을 미리 정해두도록 하여 컴파일시 지정된 타입이 아닌 타입의 객체가 할당될 경우, 컴파일 에러를 발생시킨다. 이는 오히려 런타임 에러를 예방시킬 수 있어 코드의 안정성을 높혀주는 효과를 가져온다.

다시 말해, 개발자가 직접 형변환을 해야 하는 수고도 없애주고 잘못된 형변환으로 인해 발생할 에러를 컴파일 과정에서 확인하고 처리할 수 있다는 장점이 있다.

> [참고사이트](https://hoony-devblog.tistory.com/12)
