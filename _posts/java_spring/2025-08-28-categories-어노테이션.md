---
title: "자주 쓰는 어노테이션에 대해 알아보자"
excerpt: "자주 쓰는 어노테이션에 대해 알아보자"

categories:
  - java_spring
tags:
  - [tag1, tag2]

permalink: /java spring/annotation

toc: true
toc_sticky: true

date: 2025-08-28
last_modified_at: 2025-08-28
---


```java 
import lombok.*;

@RequiredArgsConstructor
@AllArgsConstructor
@NoArgsConstructor
public class User {
    private final String name;
    private int age;
    private @NonNull String email;
}
```

###  @RequiredArgsConstructor

포함 필드: final + @NonNull

여기서는 name(final), email(@NonNull) 포함

자동 생성되는 생성자:

```java
public User(String name, String email) {
    this.name = name;
    this.email = Objects.requireNonNull(email);
}
```


핵심: 필수값만 넣어서 객체 생성 가능

### @AllArgsConstructor

포함 필드: 모든 필드 (name, age, email)

자동 생성되는 생성자:

``` java
public User(String name, int age, String email) {
    this.name = name;
    this.age = age;
    this.email = email;
}
```


핵심: 모든 필드를 한 번에 초기화할 때 사용

### @NoArgsConstructor

포함 필드: 없음

자동 생성되는 생성자:

```java
public User() {
}
```


핵심: 아무 값 없이 객체 생성 가능 (ex: JPA 엔티티용, 프레임워크에서 기본 생성자 필요할 때)

---

### 요약

```java
@RequiredArgsConstructor → 필수값만 넣고 싶을 때

@AllArgsConstructor → 전체 필드 넣고 싶을 때

@NoArgsConstructor → 빈 객체 만들고 싶을 때
```