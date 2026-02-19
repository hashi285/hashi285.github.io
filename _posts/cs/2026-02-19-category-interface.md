---
title: "interface"
excerpt: "interface"

categories:
  - CS
tags:
  - [tag1, tag2]

permalink: /cs/interface


toc: true
toc_sticky: true

date: 2026-02-19
last_modified_at: 2026-02-19
---

## 인터페이스란?

- *인터페이스(Interface)**는 자바에서 **추상 메서드(구현이 없는 메서드)와 상수를 정의**할 수 있는 일종의 "계약서"이다.

인터페이스를 사용하면 **클래스 간의 규칙**을 정의하고, **다형성(Polymorphism)**을 활용하여 코드의 유연성과 확장성을 높일 수 있다. 

---

## 사용 이유

1. **규칙 정의**:
    - 인터페이스는 클래스가 반드시 구현해야 하는 메서드들을 정의한다.
    - "이 클래스는 이런 기능을 제공해야 해!"라는 규칙을 명확히 한다.
2. **다형성(Polymorphism)**:
    - 다양한 클래스가 동일한 인터페이스를 구현할 수 있어, 서로 다른 객체를 같은 방식으로 다룰 수 있다.
3. **코드 확장성 및 유지보수성**:
    - 새로운 기능이나 클래스를 추가할 때 기존 코드를 수정하지 않고 확장이 가능하다.

---

## 사용 전과 후의 비교

### **1. 인터페이스 없는 경우**

가정: **동물이 소리를 내는 프로그램을 작성해야 한다.**

각 동물마다 다른 방식으로 소리를 낸다.

```java
java
코드 복사
class Dog {
    public void makeSound() {
        System.out.println("멍멍");
    }
}

class Cat {
    public void makeSound() {
        System.out.println("야옹");
    }
}

public class NoInterfaceExample {
    public static void main(String[] args) {
        Dog dog = new Dog();
        Cat cat = new Cat();

        // 각각의 클래스 메서드를 개별적으로 호출
        dog.makeSound(); // 멍멍
        cat.makeSound(); // 야옹
    }
}

```

**문제점**:

1. **다형성 부재**:
    - 서로 다른 객체를 공통된 방식으로 처리할 수 없다.
    - 예: 모든 동물을 배열로 처리하고 싶다면, 개별 타입으로 관리해야 한다.
2. **확장 어려움**:
    - 새로운 동물 클래스를 추가할 때, 기존 메서드와 코드에 영향을 미친다.

---

### **2. 인터페이스 사용하는 경우**

**동물이 소리를 내는 규칙**을 인터페이스로 정의해 봅시다.

```java
java
코드 복사
// 인터페이스 정의
interface Animal {
    void makeSound(); // 동물이 소리를 내야 한다는 규칙 정의
}

// Dog 클래스
class Dog implements Animal {
    @Override
    public void makeSound() {
        System.out.println("멍멍");
    }
}

// Cat 클래스
class Cat implements Animal {
    @Override
    public void makeSound() {
        System.out.println("야옹");
    }
}

// Bird 클래스 추가 (새로운 동물 클래스 추가)
class Bird implements Animal {
    @Override
    public void makeSound() {
        System.out.println("짹짹");
    }
}

public class InterfaceExample {
    public static void main(String[] args) {
        // 모든 동물을 공통된 방식으로 처리 가능
        Animal dog = new Dog();
        Animal cat = new Cat();
        Animal bird = new Bird();

        Animal[] animals = { dog, cat, bird };

        // 다형성을 활용해 동일한 방식으로 처리
        for (Animal animal : animals) {
            animal.makeSound();
        }
    }
}

```

**출력**:

```
코드 복사
멍멍
야옹
짹짹

```

**장점**:

1. **다형성**:
    - `Animal` 인터페이스를 통해 동물 객체를 배열로 관리하고, 반복문으로 동일한 방식으로 처리할 수 있다.
2. **확장성**:
    - 새로운 동물 클래스(`Bird`)를 추가해도 기존 코드 수정 없이 확장 가능하다

---

## **정리**

1. **인터페이스가 없는 경우**:
    - 개별적으로 메서드를 호출하고 관리해야 하므로 확장성과 다형성이 부족하다.
2. **인터페이스가 있는 경우**:
    - 동일한 규칙을 따라 구현하므로 다형성을 활용하여 다양한 객체를 공통적으로 다룰 수 있다.
    - 유지보수성과 확장성이 크게 향상된다.

---

## **결론**

인터페이스는 **규칙을 정의하고 강제**하여, 코드의 **일관성**, **유연성**, **확장성**을 크게 향상시킨다.

작은 프로젝트에서는 필요성을 못 느낄 수 있지만, 규모가 커지거나 팀 프로젝트에서 **인터페이스는 필수적**인 도구가 된다.