---
title: "예외처리란? (Exception)"
excerpt: "자바의 예외처리에 대해 알아보자"

categories:
  - jsp
tags:
  - [tag1, tag2]

permalink: /jsp/Exception

toc: true
toc_sticky: true

date: 2025-05-20
last_modified_at: 2025-05-20
---
# 오늘은 자바의 예외처리에 대해 알아보는 시간을 가져보겠다.
아래의 표는 자바의 주요 예외이다.

## 자바 주요 예외(Exception) 종류와 설명

| 예외 이름                    | 분류               | 설명                                   |
|--------------------------|------------------|--------------------------------------|
| `Exception`              | Checked Exception | 일반적인 예외의 기본 클래스                     |
| `RuntimeException`       | Unchecked Exception | 런타임 예외 기본 클래스                        |
| `IOException`            | Checked Exception | 입출력 관련 예외                           |
| `FileNotFoundException`  | Checked Exception | 파일을 찾지 못했을 때 발생                     |
| `SQLException`           | Checked Exception | DB 처리 중 발생                            |
| `InterruptedException`   | Checked Exception | 스레드 인터럽트 발생                        |
| `NullPointerException`   | RuntimeException | 널 객체 참조 시 발생                         |
| `ArithmeticException`    | RuntimeException | 산술 연산 오류 (예: 0으로 나누기)                |
| `ArrayIndexOutOfBoundsException` | RuntimeException | 배열 인덱스 범위 초과                         |
| `NumberFormatException`  | RuntimeException | 문자열을 숫자로 변환 실패                      |
| `ClassCastException`     | RuntimeException | 잘못된 클래스 타입 변환                       |


### 1. 자바 예외 클래스 계층 구조 (대표적)

```
java.lang.Throwable
├── java.lang.Error                 (프로그램 복구 불가능한 심각한 오류)
└── java.lang.Exception
    ├── java.lang.RuntimeException (Unchecked Exception)
    └── Checked Exception (직접 상속된 예외들)
```

### 2. Error (심각한 오류, 보통 처리하지 않음)

VirtualMachineError (JVM 관련 치명적 오류)

OutOfMemoryError (메모리 부족)

StackOverflowError (스택 오버플로우)

NoClassDefFoundError

AssertionError

LinkageError 등

### 3. Checked Exception (컴파일러가 처리 강제)

**IOException 계열 (입출력 관련)**

IOException

FileNotFoundException

EOFException

InterruptedIOException

MalformedURLException

SocketException

UnknownHostException

**SQL 관련**

SQLException

**Reflect 관련**

ClassNotFoundException

NoSuchMethodException

InvocationTargetException

**Thread/Concurrency 관련**

InterruptedException

**Others**

CloneNotSupportedException

ParseException

InstantiationException

IllegalAccessException

### 4. Unchecked Exception (RuntimeException 계열)

NullPointerException — 널 참조 접근

ArithmeticException — 산술 연산 오류 (0으로 나누기 등)

ArrayIndexOutOfBoundsException — 배열 인덱스 범위 초과

StringIndexOutOfBoundsException — 문자열 인덱스 범위 초과

IllegalArgumentException — 부적절한 인수 전달

NumberFormatException (문자열 -> 숫자 변환 실패)

ClassCastException — 잘못된 타입 캐스팅

IllegalStateException — 잘못된 상태에서 메서드 호출

UnsupportedOperationException — 지원하지 않는 연산 호출

ConcurrentModificationException — 동시 수정 시도 시 발생

ArrayStoreException — 잘못된 배열 타입 저장

SecurityException — 보안 위반

