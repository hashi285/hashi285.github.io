---
title: "CAPS(백준 15000번)"
excerpt: "알고리즘 테스트"

categories:
  - Algorithm
tags:
  - [tag1, tag2]

permalink: /Algorithm/15000

toc: true
toc_sticky: true

date: 2025-08-27
last_modified_at: 2025-08-27
---

## 문제

Earth is under attack! Messages need to be sent to the Earth Defense Force (EDF) that makes clear that the situation is dire. The EDF’s strongest forces consist of mechs (huge bipedal robots) that are piloted by Japanese teenagers. To make sure that the messages come across as urgent, they must be displayed on the monitors of the pilots in uppercase letters. Unfortunately, the tachyon communication system that is used by the EDF is only able to send strings in lower-case alphabetic characters.

The set of lower-case alphabetic characters is made up of the following characters: ’a’, ’b’, ’c’, ’d’, ’e’, ’f’, ’g’, ’h’, ’i’, ’j’, ’k’, ’l’, ’m’, ’n’, ’o’, ’p’, ’q’, ’r’, ’s’, ’t’, ’u’, ’v’, ’w’, ’x’, ’y’, ’z’.

Your job is to write a program that converts the given messages to upper-case.

## 입력

A single line containing a string of length n (100 ≤ n ≤ 106), consisting of lower-case alphabetic characters.

## 출력

A single line containing the input string where all letters are converted to upper-case letters.

## 예제 입력 1

``` 
alert
```

## 예제 출력 1 
```
ALERT
```

## 예제 입력 2

```
earthisunderattack
```

## 예제 출력 2 

```
EARTHISUNDERATTACK
```

## 예제 입력 3 

```
canyoupickupsomegroceries
```

## 예제 출력 3 

```
CANYOUPICKUPSOMEGROCERIES
```

##  풀이

입력으로 들어온 문자를 대문자로 출력하는 문제이다.

**.toUpperCase(Locale.ROOT)** 를 사용하였다. 

```java
import java.io.*;
import java.util.Locale;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

        String input = br.readLine();
        String upperCase = input.toUpperCase(Locale.ROOT); // 대문자로 변환 

        bw.write(upperCase);
        bw.flush();
        bw.close();
    }
}
```