---
title: "Singleton Pattern"
excerpt: "싱글톤 패턴에 대해 알아보자"

categories:
  - CS
tags:
  - [tag1, tag2]

permalink: /cs/Singleton Pattern


toc: true
toc_sticky: true

date: 2025-05-27
last_modified_at: 2025-05-27
---
>## **싱글톤 패턴이란?**

> **싱글톤 패턴(singleton pattern)**은 하나의 클래스에 오직 하나의 인스턴스만 가지는 패턴이다.

하나의 클래스를 기반으로 여러 개의 개별적인 인스턴스를 만들지 않고 하나의 클래스를 기반으로 단 하나의 인스턴스를 만들어 이를 기반으로 로직을 만드는 데 쓰이며, 데이터베이스 연결 모듈에 많이 쓰인다.

**장점**
- 인스턴스를 생성할 때 드는 비용이 줄어든다.

**단점**
- 의존성이 높아진다.

>## 자바의 싱글톤 패턴

**🎯 문제 상황:**

우리가 어떤 애플리케이션을 만들고 있고, 로그를 남기는 Logger 클래스를 만든다고 가정해보자.

만약 Logger 객체를 매번 새로 만든다면?

```java

Logger logger1 = new Logger();
Logger logger2 = new Logger();

logger1.log("시작");
logger2.log("종료");
```

logger1과 logger2는 서로 다른 인스턴스이기 때문에 로그 출력 방식이나 상태가 달라질 수 있다. 이는 문제가 될 가능성이 있다.

### ✅ 해결 방법: 싱글톤 Logger 클래스 

```java

public class Logger {
    // 정적(static) 변수로 단 하나의 인스턴스를 저장
    private static final Logger instance = new Logger();

    // 외부에서 생성하지 못하도록 생성자 private
    private Logger() {
        // 초기화 작업
    }

    // 유일한 인스턴스를 반환하는 메서드
    public static Logger getInstance() {
        return instance;
    }

    public void log(String message) {
        System.out.println("[로그] " + message);
    }
}
```

### 🔧 사용 방법:

```java

public class Main {
    public static void main(String[] args) {
        Logger logger1 = Logger.getInstance();
        Logger logger2 = Logger.getInstance();

        logger1.log("앱 시작");
        logger2.log("앱 종료");

        System.out.println(logger1 == logger2); // true (같은 인스턴스)
    }
}
```

>## 데이터베이스의 싱글톤 패턴

**싱글톤 패턴은 데이터베이스 연결에서도 많이 사용된다**

DB 연결은 리소스를 많이 쓰기 때문에, 매번 새로 만들면 성능이 나빠지고, 

불필요한 연결이 많아지면 **서버가 터질 수 있기 때문이다.**

>## ✅ 데이터베이스에서 싱글톤이 쓰이는 이유

📌 이유 1: DB 연결 객체는 무겁다
DB에 연결할 때마다 네트워크 통신이 일어나요.

자주 만들면 속도가 느려지고 리소스 낭비가 심함.

📌 이유 2: 공통으로 연결 객체를 써야 한다
여러 클래스가 DB에 접근하더라도 하나의 연결을 공유하거나,

**연결 풀(Connection Pool)**을 만들어서 관리하는 게 더 안전하고 효율적이다.

**🎯 간단 예시: 싱글톤 DB 연결**
```java

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class DatabaseManager {
    private static DatabaseManager instance;
    private Connection connection;

    private final String URL = "jdbc:mysql://localhost:3306/mydb";
    private final String USER = "root";
    private final String PASSWORD = "1234";

    // private 생성자 → 외부에서 new 못 함
    private DatabaseManager() {
        try {
            connection = DriverManager.getConnection(URL, USER, PASSWORD);
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }

    // getInstance() → 유일한 인스턴스를 반환
    public static synchronized DatabaseManager getInstance() {
        if (instance == null) {
            instance = new DatabaseManager();
        }
        return instance;
    }

    // 외부에서 연결 객체를 가져가게 하는 메서드
    public Connection getConnection() {
        return connection;
    }
}
```
**🔧 사용 예시**
```java

public class UserDAO {
    public void getUserById(int id) {
        Connection conn = DatabaseManager.getInstance().getConnection();
        // 여기서 DB 작업 수행
    }
}
```


