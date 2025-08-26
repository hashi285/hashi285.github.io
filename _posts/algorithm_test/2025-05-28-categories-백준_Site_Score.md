---
title: "Site Score(백준 20254번)"
excerpt: "알고리즘 테스트"

categories:
  - Algorithm
tags:
  - [tag1, tag2]

permalink: /Algorithm/20254

toc: true
toc_sticky: true

date: 2025-05-28
last_modified_at: 2025-05-28
---

## 문제

Teams from variaous universities compete in ICPC regional contests for tickets to the ICPC World Finals. The number of tickets allocated to every regional contest may be different. The allocation method in our super region, Asia Pacific, is based on a parameter called site score.

Site scores will only count teams and universities solving at least one problem, in the regional contest or its preliminary contest TOPC. In 2020, the formula for calculating the site score of the Taipei-Hsinchu regional contest is much simpler than past years. Let

UR be the number of universities solving at least one problem in the regional contest.
TR be the number of teams solving at least one problem in the regional contest.
UO be the number of universities solving at least one problem in TOPC.
TO be the number of teams solving at least one problem in TOPC.
The site score of 2020 Taipei-Hsinchu regional contest will be 56UR + 24TR + 14UO + 6TO. Please write a program to compute the site score of the 2020 Taipei-Hsinchu regional contest.

## 입력 

The input has only one line containing four blank-separated positive integers UR, TR, UO, and TO.

## 출력

Output the site score of the 2020 Taipei-Hsinchu regional contest.

## 제한

0 < UR ≤ TR ≤ 120
0 < UO ≤ TO ≤ 1000

## 예제 입력 1 
```
1 1 1 1
```

## 예제 출력 1 
```
100
```
## 예제 입력 2 
```
1 10 100 1000
```
## 예제 출력 2 
```
7696
```

## 노트
The problem statement is fiction. The real site score has a different formula.

---

입력값 네가지 숫자를 각각 순서대로 56, 24, 14, 6에 곱한 뒤에 합을 구하면 되는 문제이다. 

```java
import java.io.*;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        StringTokenizer st = new StringTokenizer(br.readLine());

        int[] N = {56,24,14,6}; //곱해야 하는 수를 배열에 넣는다.
        int k = 0; //정답이 될 변수 초기화화

        for (int i = 0; i < 4; i++){ //각각의 숫자를 총 4회 곱하고, k에 넣는다.
            int n = Integer.parseInt(st.nextToken());
            k += n*N[i];
        }
        bw.write(k + "\n");
        bw.flush();
    }
}
```
