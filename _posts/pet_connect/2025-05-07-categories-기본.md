---
title: "프로젝트 개발환경 세팅"
excerpt: "개발환경 세팅"

categories:
  - pet_connect
tags:
  - [tag1, tag2]

permalink: /pet_connect/개발환경_세팅

toc: true
toc_sticky: true

date: 2025-05-07
last_modified_at: 2025-05-07
---

# 공통 사항 (OS 및 기본 세팅)

- 운영체제: Windows 10/11 또는 macOS/Linux (사용 중인 환경에 맞게)

- JDK: Java 21

- 빌드 도구: Gradle 

- 스프링 스타터로 생성 시 자동 설정 가능

# 백엔드 개발 환경 (IntelliJ + Spring)
IDE: IntelliJ IDEA (대학교 재학중인 경우에는 유료버전을 무료로 사용 가능)
![Jekyll 이미지 예시](/assets/images/posts_img/fireballs/intelij1.png)
[IntelliJ 다운로드 바로가기](https://www.jetbrains.com/ko-kr/idea/download/?section=windows)

위의 사이트에 접속을 하여 인텔리제이를 다운받는다

- Spring Boot

- Spring Initializr (https://start.spring.io)

### 의존성:

- Spring Web

- Spring Data JPA

- H2 / MySQL / PostgreSQL 등 

- Lombok

- Spring Security 등등

### 데이터베이스:

- 개발용: H2 또는 SQLite

- 운영/배포용: MySQL

- Postman 또는 Insomnia (API 테스트용)

# ✅ 프론트엔드/디자인 개발 환경 (Visual Studio)
Visual Studio Code (웹 개발)
![Jekyll 이미지 예시](/assets/images/posts_img/fireballs/visualstudiocode1.png)
[Visual Studio 다운로드 바로가기](https://code.visualstudio.com/) 

위의 사이트에 접속하여 비주얼 스튜디오 코드를 다운받는다.

- HTML/CSS/JavaScript

- 정적 파일은 Spring의 resources/static 또는 resources/templates 폴더에 배치

- Node.js

- 브라우저: Chrome (개발자 도구 활용 가능)

# ✅ 기타 도구
- Git (버전 관리)

- GitHub (협업 및 코드 저장소)

- 터미널 또는 명령 프롬프트: Bash / PowerShell / CMD

- Docker (배포나 DB 테스트에 사용될 수 있음)

### 전체적인 개발 환경

- 인텔리제이
- 비주얼 스튜디오
- GitHub
- MySQL
