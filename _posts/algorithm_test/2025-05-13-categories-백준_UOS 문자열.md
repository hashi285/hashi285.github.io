---
title: "UOS 문자열(백준 32929번)"
excerpt: "알고리즘 테스트"

categories:
  - Algorithm
tags:
  - [tag1, tag2]

permalink: /Algorithm/UOS문자열

toc: true
toc_sticky: true

date: 2025-05-13
last_modified_at: 2025-05-13
---

# 문제
UOS 문자열이란 UOSUOSUOSU...와 같이 UOS가 무한히 반복되어 나타나는 문자열이다. 양의 정수 
$x$가 주어질 때 UOS 문자열의 
$x$번째 문자를 구하여라.

# 입력
첫 번째 줄에 
$x$가 주어진다. 
$(1 \leq x \leq 10^9)$ 

# 출력
UOS 문자열의 
$x$번째 문자를 출력한다.

# 예제 입력 1 
```
5
```
# 예제 출력 1
``` 
O
```
# 예제 입력 2
``` 
1000000000
```
# 예제 출력 2
``` 
U
```
---
## 백준 32929번 "UOS문자열"을 풀어보자

UOS가 무한히 반복되어 나타나는 문자열이 있으으며, 이를 $y$라고 이 글에서 정의를 하겠다. 
양의 정수 $x$가 주어질 때 $y$의 $x$번째 문자열을 구하면 되는 쉬운 문제이다. 
이 문제를 풀기 위해서는, 


```
import java.io.*;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        String[] a = new String[3];
        int b = Integer.parseInt(br.readLine());
        int c = b % 3;

        if (c == 0) {
            bw.write("S");
        } else if (c == 1) {
            bw.write("U");
        } else if (c == 2) {
            bw.write("O");
        }
        bw.flush();
    }
}
```