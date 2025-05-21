---
title: "Can you add this?(백준 7891)"
excerpt: "알고리즘 테스트"

categories:
  - Algorithm
tags:
  - [tag1, tag2]

permalink: /Algorithm/7891

toc: true
toc_sticky: true

date: 2025-05-21
last_modified_at: 2025-05-21
---

> ## **문제**

- Given two integers, calculate and output their sum.

>## 입력

The input contains several test cases. The first line contains and integer t (t ≤ 100) denoting the number of test cases. Then t tests follow, each of them consisiting of two space separated integers x and y (−109 ≤ x, y ≤ 109).

>## 출력

For each test case output output the sum of the corresponding integers.

>## 예제 입력 1 

```
4
-100 100
2 3
0 110101
-1000000000 1
```
>## 예제 출력 1 

```
0
5
110101
-999999999
```
>## 출처

ICPC > Regionals > Europe > Central European Regional Contest > CERC 2008 연습 세션 PA번

---
>## 풀이

간단한 문제이다. 두 가지의 수를 입력받으면, 이 두 수의 합을 구하고, 출력을 하면 된다. 아래는 정답코드이다.

```java
import java.io.*;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

        int N = Integer.parseInt(br.readLine()); //테스트 케이스의 개수를 나타내는 정수

        while (N-- > 0) { //테스트케이스 N만큼 반복
            StringTokenizer st = new StringTokenizer(br.readLine()); 
            int a = Integer.parseInt(st.nextToken()); //첫 번재 정수
            int b = Integer.parseInt(st.nextToken()); //두 번쨰 정수

            bw.write(a+b + "\n"); //두 정수의 합합
        }
        bw.flush();
        bw.close();
    }
}
```
