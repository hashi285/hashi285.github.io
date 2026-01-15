---
title: "제네릭이란?"
excerpt: "제네릭에 대해 알아보자"

categories:
  - java_spring
tags:
  - [tag1, tag2]

permalink: /java spring/Generics

toc: true
toc_sticky: true

date: 2025-10-10
last_modified_at: 2025-10-10
---

# 제네릭이란?

## 제네릭의 이해

제네릭이 갖는 의미는 일반화이다. 

자바에서의 제네릭의 일반화 대상은 자료형이다. 

간단한 코드를 보고 설명하겠다.

```java

// 사과와 오렌지를 단순히 표현한 클래스
class Apple {
    public String toString() {
        return "I am an apple";
    }
}

class Orange {
    public String toString() {
        return "I am an orange";
    }
}

// 사과와 오렌징를 담는 상자를 표현한 클래스
class AppleBox {
    private Apple ap;

    
}
