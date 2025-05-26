---
title: "cookie (쿠키란?)"
excerpt: "cookie에 대해 알아보자자"

categories:
  - jsp
tags:
  - [tag1, tag2]

permalink: /jsp/cookied

toc: true
toc_sticky: true

date: 2025-05-12
last_modified_at: 2025-05-12
---

> # COOKIE

> ## 쿠키

- 사용자의 시스템에 간단한 정보를 저장해 필요할 때마다 해당전보를 읽어오기 위하여 사용
- 간단한 정보를 클라이언트에 저장함으로써 서버의 부하를 크게 줄일 수 있음
- 쿠키의 동작
    - 쿠키 생성 → 쿠키 저장 → 쿠키 전송

---

> ## 쿠키에서 제공하는 메소드

- getComment() : 쿠키에 설정된 코멘트 리턴
- getDomainIO : 쿠키 도메인 리턴
- getMaxAge() : 쿠키 유효시간 리턴
- getName() : 쿠키 이름 리턴
- getPath() : 쿠키 전송경로 리턴
- getSecure() : 지정된 boolean 값 리턴
- getValue() : 쿠키값 리턴
- getVersion() : 쿠키버전 리턴
- setComment(String comment) : 쿠키의 사용 목적을 설명하는 코멘트 설정
- setDomain(String pattern) : 도메인 설정
- setMaxage(int expiry) : 쿠키의 유효시간 설정
- setPath(String url) : 쿠키를 전송한 경로 설정

---

## 쿠키 설정 및 읽기

**쿠키를 설정하기 위해서는 Cookie 클래스를 이용해야 함**

```java
Cookie cookie = new Cookie(String name, String value); // **형식**
Cookie cookie = new Cookie("Job", URLEncoder.encode("학생")); // **예제**
```

---

## 쿠키 값 설정

```java
<%-- 프로그램 명 : Cookie 설정 프로그램
개발자 : Alex Ryu
개발 시작일 : 2025년 4월 5일
프로그램 Version UpGrade 2025년 4월7일
--%>
<%@ page contentType = "text/html; charset=euc-kr" %>
<%@ page import = "java.net.URLEncoder" %>
<%@ page import = "java.net.URLDecoder" %>
<HTML><HEAD> <TITLE> 쿠키 </TITLE>
</HEAD>
<BODY>
<%
Cookie cookie1 = new Cookie("Name", URLEncoder.encode(“류문형"));
Cookie cookie2 = new Cookie("Job", URLEncoder.encode(“교수"));
response.addCookie(cookie1);
response.addCookie(cookie2);
out.println(cookie1.getName()+ " 쿠키의 값 : " + cookie1.getValue() + "<BR>");
out.println(cookie2.getName()+ " 쿠키의 값 : " + cookie2.getValue() + "<BR><BR>");
String strCookie1 = URLDecoder.decode(cookie1.getValue());
String strCookie2 = URLDecoder.decode(cookie2.get
Value());
out.println(cookie1.getName()+ " 쿠키의 값 : " + strCookie1 + "<BR>");
out.println(cookie2.getName()+ " 쿠키의 값 : " + strCookie2);
%>
</BODY>
</HTML>ㅇ
```

---

## 쿠키 변경 및 삭제

변경을 위해서는 변경하려는 쿠키의 이름에 해당하는 쿠키 값을 변경

변경하려는 쿠키의 이름이 없을 경우 새롭게 쿠키를 생성

```java
<%-- 프로그램 명 : Cookie 변경 프로그램
개발자 : Alex Ryu
개발 시작일 : 2025년 4월 12일
프로그램 Version UpGrade 2025년 4월13일
--%>
<%@ page contentType = "text/html; charset=euc-kr" %>
<%@ page import = "java.net.URLEncoder" %>
<HTML> <HEAD> <TITLE> 쿠키 </TITLE>
</HEAD>
<BODY>
<%
Cookie[] cookies = request.getCookies();
if(cookies != null){
for(int i=0; i<cookies.length; i++){
if(cookies[i].getName().equals("Name")){
Cookie cookie = new Cookie("Name", URLEncoder.encode("김초롱"));
response.addCookie(cookie);
}
}
}
out.println("쿠키값을 변경하였습니다..");
%>
</BODY>
</HTML>
```

---

## 쿠키 도메인 및 경로

setDomain () 메소드 : 사용하는 서버에 쿠키를 보내려고 할 때 사용

```java
cookie.setDomain(String url); // 형식
cookie.setDomain("[www.shop.net](http://www.shop.net/)"); // 예제 
```

getDomain () 메소드 : 설정한 쿠키 도메인을 리턴하려고 할 때 사용
setPath () 메소드 : 경로 지정

```java

cookie.setPath(String url) // 형식 
cookie.setPath("/"); // 예제 
```

---

## 쿠키 유효 시간 설정

각 쿠키는 유효시간을 가지고 있음

유효시간동안 쿠키가 저장. 설정하지 않고, 웹브라우저를 종료하면 해당쿠키는 삭제된다.

setMaxAge() 메소드 : 쿠키 유효 시간 설정 시 사용 (예 : 60 * 60 (1시간))

```java
cookie.setMaxAge(int expiry) // 형식 
cookie.setMaxAge(60 * 60); // 예제 
```

---

## 쿠키 값 삭제

```java
<%-- 프로그램 명 : Cookie 삭제 프로그램
개발자 : Alex Ryu
개발 시작일 : 2025년 4월 2일
프로그램 Version UpGrade 2025년 4월10일
--%>
<%@ page contentType = "text/html; charset=euc-kr" %>
<%@ page import = "java.net.URLEncoder" %>
<HTML> <HEAD> <TITLE> 쿠키 </TITLE>
</HEAD> <BODY>
<%
Cookie[] cookies = request.getCookies();
if(cookies != null){
for(int i=0; i<cookies.length; i++){
if (cookies[i].getName().equals("Name")){
Cookie cookie = new Cookie("Name", "");
cookie.setMaxAge(0);
response.addCookie(cookie);
}
}
}
out.println("쿠키를 삭제하였습니다..");
%>
</BODY>
</HTML>
```