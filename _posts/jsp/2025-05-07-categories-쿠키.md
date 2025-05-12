---
title: "cookie (쿠키란?)"
excerpt: "cookie에 대해 알아보자자"

categories:
  - jsp
tags:
  - [tag1, tag2]

permalink: /jsp/cookie

toc: true
toc_sticky: true

date: 2025-05-12
last_modified_at: 2025-05-12
---

# COOKIE

## 쿠키

- 사용자의 시스템에 간단한 정보를 저장해 필요할 때마다 해당전보를 읽어오기 위하여 사용
- 간단한 정보를 클라이언트에 저장함으로써 서버의 부하를 크게 줄일 수 있음
- 쿠키의 동작
    - 쿠키 생성 → 쿠키 저장 → 쿠키 전송

```
<%@ page contentType = "text/html; charset=UTF-8" pageEncoding="UTF-8" %>
<%@ page import = "java.net.URLEncoder" %>
<%@ page import = "java.net.URLDecoder" %>
<HTML><HEAD><TITLE>쿠키</TITLE></HEAD>
<BODY>
<%
Cookie cookie1 = new Cookie("Name", URLEncoder.encode("류문형", "UTF-8"));
Cookie cookie2 = new Cookie("Job", URLEncoder.encode("교수", "UTF-8"));
response.addCookie(cookie1);
response.addCookie(cookie2);

out.println(cookie1.getName()+ " 쿠키의 값 : " + cookie1.getValue() + "<BR>");
out.println(cookie2.getName()+ " 쿠키의 값 : " + cookie2.getValue() + "<BR><BR>");

String strCookie1 = URLDecoder.decode(cookie1.getValue(), "UTF-8");
String strCookie2 = URLDecoder.decode(cookie2.getValue(), "UTF-8");

out.println(cookie1.getName()+ " 쿠키의 디코딩 값 : " + strCookie1 + "<BR>");
out.println(cookie2.getName()+ " 쿠키의 디코딩 값 : " + strCookie2);
%>
</BODY>
</HTML>
```