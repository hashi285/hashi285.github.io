---
title: "줄 세기(백준 4806번)"
excerpt: "알고리즘 테스트"

categories:
  - Algorithm
tags:
  - [tag1, tag2]

permalink: /Algorithm/4806

toc: true
toc_sticky: true

date: 2025-05-20
last_modified_at: 2025-05-20
---
# 문제
줄의 개수를 세는 프로그램을 작성하시오.

## 입력
한 줄에 최대 100글자씩 주어진다. 빈 줄이 주어질 수도 있다.

## 출력
입력으로 몇 줄이 주어졌는지를 출력한다.

## 예제 입력 1 
```
one
and two
three

```
## 예제 출력 1
``` 
3
```
 
---

# 💻 백준 4806번 "줄 세기" Java 풀이 + NullPointerException 주의

백준 4806번 문제를 자바(Java)로 풀면서 발생할 수 있는 **런타임 에러 (NullPointerException)**와 입력 처리 방식에 대해 정리합니다.

---

## 📌 문제 요약

- 여러 줄의 입력을 받는다.
- 입력은 **EOF(End Of File)**까지 주어진다.
- 줄 수를 세어서 출력한다.
- **빈 줄도 1줄로 세야 한다.**

---

## ✅ 정답 코드 (BufferedReader + EOF 처리)

```
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int lineCount = 0;
        String line;

        while ((line = br.readLine()) != null) {
            lineCount++;
        }

        System.out.println(lineCount);
    }
}
```

## 🔍 설명
readLine()은 입력이 끝나면 null을 반환한다.

따라서 null이 아닐 동안 계속 줄을 읽으면서 줄 수를 센다.

빈 줄도 null이 아니기 때문에 정상적으로 카운트된다.

## ❌ 잘못된 코드 예시 (NullPointerException 발생 가능)

```
import java.io.*;
import java.util.Objects;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

        int n = 0;
        while (true){
            if (Objects.equals(br.readLine(), "")){
                break;
            } else {
                n++;
            }
        }
        bw.write(String.valueOf(n));
        bw.flush();
        bw.close();
    }
}
```

## ⚠️ 문제점
빈 문자열 ""을 만나면 종료되므로 EOF까지 모두 세지 못한다.

readLine()이 EOF에서 null을 반환하므로 Objects.equals(null, "")에서 NullPointerException이 발생할 수 있다.

## ✅ 올바른 수정 방법

```
String line;
while ((line = br.readLine()) != null) {
    n++;
}

```
readLine()의 결과가 null이 아닌 동안 반복.

null 확인으로 EOF를 정확하게 처리한다.

## 📌 비교 요약
항목	정답 코드	잘못된 코드
EOF 처리 방식	readLine() != null	readLine().equals("")
빈 줄 포함 여부	✅ 포함됨	❌ 포함되지 않음
NullPointerException 발생 가능성	❌ 없음	⚠️ 있음
백준 환경 적합성	✅ 적합	❌ 부적합

## ✍️ 마무리
백준처럼 EOF 입력을 사용하는 문제는 반드시 readLine() != null 방식으로 처리해야 한다.

빈 줄과 null은 다르다. null은 EOF이고, 빈 줄은 실제로 존재하는 한 줄이다.

문자열 비교 전에 null 여부를 먼저 확인해야 런타임 에러를 방지할 수 있다.