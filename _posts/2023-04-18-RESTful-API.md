---
layout: single
title: "[IT-용어] RESTful API"
categories: IT-용어
tag: [back-end, it-용어]
toc: true
toc_sticky: true
toc_label: index
toc_icon: "fa-solid fa-indent"
author_profile: false
# sidebar:
#     nav: "docs"
# search: false
---



<br>

<br>

# 👀 RESTful API 정의

REST(Representational State Transfer)는 분산 시스템에서 소프트웨어 아키텍처의 한 형태로, 웹에서 사용되는 HTTP/HTTPS 프로토콜을 이용하여 클라이언트와 서버 사이의 통신을 처리하는 방식입니다. 

RESTful API는 이러한 REST 아키텍처를 기반으로 한 API(Application Programming Interface)입니다. 

**RESTful API는 HTTP GET, POST, PUT, DELETE 등의 요청 메소드를 사용하여 데이터를 주고 받으며, 데이터 형식은 일반적으로 JSON(JavaScript Object Notation)이나 XML(Extensible Markup Language)로 표현됩니다.**

<br>

<br>

## 💻RESTful API의 코드 예시

RESTful API는 클라이언트와 서버 간의 통신을 위해 일반적으로 HTTP 프로토콜을 사용합니다.

이를 이용하여 간단한 RESTful API 코드를 적어보면,   

- **아래 코드는**

  Java에서 RESTful API를 작성하기 위해 가장 일반적으로 사용되는 프레임워크 중 하나인 **Spring Boot**를 사용하여 간단한 RESTful API를 작성함 ↓

```java
@RestController
@RequestMapping("/api")
public class HelloWorldController {

    @GetMapping("/hello")
    public String helloWorld() {
        return "Hello, mins!";
    }
}
```

위 코드는 Spring Boot 프레임워크를 이용하여 '/api/hello' 경로로 GET 요청을 받으면 "Hello, mins!" 문자열을 반환하는 RESTful API를 작성한 예시입니다.

먼저 @RestController 어노테이션을 사용하여 해당 클래스가 RESTful API를 제공하는 컨트롤러임을 선언합니다. 그리고 @RequestMapping 어노테이션을 이용하여 요청 경로를 '/api'로 지정하고, @GetMapping 어노테이션을 이용하여 GET 요청을 처리하도록 합니다. 메소드 내부에서는 "Hello, world!" 문자열을 반환합니다.

위와 같이 간단한 Java 코드를 이용하여 RESTful API를 작성할 수 있습니다. Spring Boot 프레임워크는 RESTful API를 작성하기에 편리한 다양한 기능들을 제공하므로, 개발자들은 이를 이용하여 더욱 효율적이고 안정적인 API를 구현할 수 있습니다.    

<br>

<br>

<br>

## 💡 RESTful API의 활용법

RESTful API는 어플리케이션에서 데이터를 생성, 읽기, 수정, 삭제하는 데 사용할 수 있습니다. 이를 이용하여 여러분의 어플리케이션과 다른 어플리케이션 간에 데이터를 공유할 수 있습니다.   

RESTful API를 사용하기 위해서는 먼저 해당 API를 제공하는 서버가 존재해야 합니다. 이후 클라이언트에서는 HTTP/HTTPS 프로토콜을 이용하여 해당 서버에 요청을 보내 데이터를 주고 받습니다. 요청 메소드는 GET, POST, PUT, DELETE 등이 있으며, 요청 메소드에 따라 서버는 해당하는 데이터를 처리하고 응답을 반환합니다. 응답은 일반적으로 JSON이나 XML 형식으로 반환됩니다.   

<br/>

<br/>

<br/>

## 💡 RESTful API를 사용하기 위한 고려사항

**RESTful API를 사용할 때 고려해야 할 몇 가지 주요 사항들은 다음과 같습니다.**

1. API 버전과 업데이트 방법 API를 설계할 때, API 버전을 고려하여 URL 경로에 버전 정보를 명시하는 것이 좋습니다. 이렇게 하면 API가 업데이트되거나 변경될 경우에도 클라이언트가 기존 API와 새 API를 구분할 수 있으며, 호환성 문제를 예방할 수 있습니다.
2. 데이터 형식과 데이터 스키마 RESTful API에서는 XML 또는 JSON 형식의 데이터를 사용합니다. 이 중에서도 JSON 형식의 데이터가 가장 널리 사용됩니다. 데이터 스키마를 명확하게 정의하여 API를 사용하는 클라이언트가 데이터를 정확하게 이해하고 처리할 수 있도록 하는 것이 중요합니다.
3. HTTP 메소드 사용 HTTP 메소드를 올바르게 사용하는 것이 RESTful API의 핵심입니다. GET, POST, PUT, DELETE 등의 HTTP 메소드를 사용하여 자원의 조회, 생성, 수정, 삭제 등을 처리합니다. 이때, 각 HTTP 메소드가 의미하는 바를 명확하게 이해하고 사용해야 합니다.
4. 보안 RESTful API에서는 클라이언트와 서버 간의 통신이 평문으로 이루어지므로 보안 문제가 발생할 수 있습니다. 따라서 API를 보호하기 위해 HTTPS를 사용하거나 OAuth와 같은 인증 및 권한 부여 프로토콜을 사용하는 것이 좋습니다.
5. API 문서화 RESTful API의 문서화는 API를 사용하는 클라이언트들이 API의 기능과 사용 방법을 이해하고 쉽게 활용할 수 있도록 하는 데 중요한 역할을 합니다. API의 입력 매개변수, 출력 값, 예외 처리 방법 등을 명확하게 문서화하고 공개함으로써 API 사용자들이 문제를 해결하는 데 도움을 줄 수 있습니다.

<br>

<br>

<br>



## ⭐ 결론

결론적으로, RESTful API는 HTTP/HTTPS 프로토콜을 이용하여 클라이언트와 서버 간의 통신을 처리하는 방식 중 하나입니다. RESTful API를 사용하면 클라이언트와 서버 간의 데이터 통신이 효율적이고 표준화되어 있어 개발자들이 쉽게 개발하고 연동할 수 있습니다.

RESTful API를 사용하기 위해서는 API를 제공하는 서버와 해당 API를 사용하는 클라이언트 모두가 RESTful 아키텍처를 준수하고 있어야 합니다. 따라서 RESTful API를 사용할 때는 API의 버전과 업데이트 방법, 데이터 형식과 데이터 스키마, API에서 제공하는 기능과 서비스 등을 고려하여 개발하고 연동하는 것이 중요합니다.

<br/>

<br/>

### ⭐ 다음 블로깅 주제

**데이터 스키마** 

<br>

<br>
