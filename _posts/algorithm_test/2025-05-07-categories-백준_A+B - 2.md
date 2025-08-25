---
title: "백준 A+B-2"
excerpt: "알고리즘 테스트"

categories:
  - Algorithm
tags:
  - [tag1, tag2]

permalink: /Algorithm/A+B-2

toc: true
toc_sticky: true

date: 2025-08-25
last_modified_at: 2025-08-25
---

## 문제

두 정수 A와 B를 입력받은 다음, A+B를 출력하는 프로그램을 작성하시오.

---

## 입력
첫째 줄에 A, 둘째 줄에 B가 주어진다. (0 < A, B < 10)

---

## 출력
첫째 줄에 A+B를 출력한다.

---

## 예제 입력 1 
```
1
2
```
## 예제 출력 1 
```
3
```

---
## 풀이
BufferedReader과 BufferedWriter를 사용하여 풀었다. 

두 수를 입력을 받고, 이의 합을 출력하는 문제이다. 

```java
import java.io.*;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

        int A = Integer.parseInt(br.readLine()); // 첫 번쨰 숫자 입력
        int B = Integer.parseInt(br.readLine()); // 두 번째 숫자 입력

        // 두 수의 합을 출력
        bw.write(A + B + "\n"); 
        bw.flush(); 
        bw.close();
    }
}
```

