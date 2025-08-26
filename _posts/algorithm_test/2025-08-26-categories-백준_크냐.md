---
title: "크냐?(백준 4101번)"
excerpt: "알고리즘 테스트"

categories:
  - Algorithm
tags:
  - [tag1, tag2]

permalink: /Algorithm/4101

toc: true
toc_sticky: true

date: 2025-08-26
last_modified_at: 2025-08-26
---

## 문제
두 양의 정수가 주어졌을 때, 첫 번째 수가 두 번째 수보다 큰지 구하는 프로그램을 작성하시오.


## 입력
입력은 여러 개의 테스트 케이스로 이루어져 있다. 각 테스트 케이스는 한 줄로 이루어져 있으며, 두 정수가 주어진다. 두 수는 백만보다 작거나 같은 양의 정수이다. 입력의 마지막 줄에는 0이 두 개 주어진다.

## 출력
각 테스트 케이스마다, 첫 번째 수가 두 번째 수보다 크면 Yes를, 아니면 No를 한 줄에 하나씩 출력한다.

## 예제 입력 1 
```
1 19
4 4
23 14
0 0
```
## 예제 출력 1 
```
No
No
Yes
```

---

## 풀이

두 개의 숫자를 입력을 받아 이 두 숫자의 크기를 비교하여 "Yes / No" 를 출력하는 문제이다.

만약 입력받은 두 숫자가 0이면, 프로그램을 종료시킨다.  

```java
import java.io.*;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));


        while(true) {
            StringTokenizer st = new StringTokenizer(br.readLine());
            int a = Integer.parseInt(st.nextToken());
            int b = Integer.parseInt(st.nextToken());

            if (a == b && a == 0){
                break;
            } else if(a > b){
                bw.write("Yes" + "\n");
            } else {
                bw.write("No" + "\n");
            }
        }
        bw.flush();
        bw.close();
    }
}
```
