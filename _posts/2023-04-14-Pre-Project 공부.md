---
layout: single
title: "[Project] 프로젝트 진행중 공부한 내용"
categories: Project
tag: [back-end, fornt-end, project]
toc: true
toc_sticky: true
toc_label: index
toc_icon: "fa-solid fa-indent"
author_profile: false
# sidebar:
#     nav: "docs"
# search: false

---



<br/>

<br/>

**2023.04.17 수정됨.**

<br/>



# 🔖 Project 진행중 알게된 부분



## DTO

- `DTO란?`

  DTO(Data Transfer Object)는 데이터 전송 객체로, 데이터를 전송하기 위한 객체입니다. DTO는 데이터베이스와의 상호작용에서 데이터를 가져오거나 저장할 때 사용됩니다. 데이터베이스와 상호작용할 때, 데이터베이스의 엔티티(Entity) 클래스가 사용되는데, 이 클래스는 데이터베이스와 밀접하게 연관되어 있기 때문에 클라이언트와의 데이터 전송을 위해서는 적합하지 않습니다.

  따라서, DTO는 엔티티 클래스와 유사하게 필드를 가지고 있지만, 로직이 없는 순수한 데이터 객체입니다. DTO는 데이터를 전송하기 위해 사용되며, 클라이언트와 서버 간의 데이터 전송 시에는 DTO를 이용하여 데이터를 전송합니다. 이렇게 함으로써 데이터의 전송 효율을 높일 수 있습니다.

  DTO를 사용하는 가장 일반적인 이유 중 하나는, 클라이언트와 서버 간의 데이터 전송 시, 불필요한 데이터 전송을 최소화하여 대역폭을 절약하고, 보안성을 향상시키기 위해서입니다. 또한, DTO를 이용하여 엔티티 객체와는 별개로 데이터를 다루므로, 엔티티 객체를 변경하지 않고도 데이터 전송에 필요한 새로운 필드를 추가할 수 있습니다.

- 



## Spring Security

- `.csrf().disable()`: CSRF 공격 방지 기능을 비활성화합니다.

  CSRF(Cross-Site Request Forgery) 공격 방지 기능은 악의적인 사용자가 특정 웹사이트를 공격하여, 인증된 사용자의 권한으로 위조된 요청을 전송하여 원치 않는 동작을 유도하는 공격을 방지하기 위한 기능입니다. 하지만, 일부 경우에는 CSRF 공격이 발생하지 않을 가능성이 높거나, 보안 수준이 상승하지 않을 때는 이 기능을 비활성화하는 것이 유용할 수 있습니다. 예를 들어, API 서버와 같이 외부에서 호출할 수 있는 리소스를 제공하는 경우, CSRF 공격 방지 기능이 필요하지 않을 수 있습니다. 따라서, 해당 코드에서는 CSRF 공격 방지 기능을 비활성화하여, 리소스를 외부에서 호출할 때 불필요한 오버헤드를 줄이는 것이 목적일 수 있습니다.



- `.headers().frameOptions().sameOrigin()` :  HTTP Response Header 설정을 위한 코드로, X-Frame-Options Header를 SAMEORIGIN으로 설정합니다. 이는 Clickjacking 공격을 방지하기 위함입니다.

- `.cors().configurationSource(corsConfigurationSource())`:  

  CORS는 웹 어플리케이션이 다른 도메인의 자원에 접근하는 것을 제한하는 보안 메커니즘입니다. 이를 위해 서버에서는 CORS 설정을 해주어야 하는데, Spring Security에서는 `cors()` 메소드를 이용하여 설정을 할 수 있습니다.

  `configurationSource()` 메소드는 `CorsConfigurationSource` 인터페이스를 구현한 객체를 반환하는데, 이 객체는 어떤 도메인에서 접근을 허용할지에 대한 정보를 담고 있습니다. 따라서 `corsConfigurationSource()` 메소드를 호출하여 `CorsConfigurationSource` 객체를 반환하고, 이 객체를 `cors()` 메소드에 전달하여 CORS 설정을 진행한 것입니다. 이를 통해 웹 어플리케이션이 다른 도메인의 자원에 대한 접근을 제한하는 것을 완화시킬 수 있습니다.  

- `.sessionManagement().sessionCreationPolicy(SessionCreationPolicy.STATELESS)` :

   Spring Security가 세션을 생성하지 않고 요청을 처리하도록 지정합니다.

  일반적으로 Spring Security는 기본적으로 세션 기반 인증을 사용하며, 로그인 후에는 세션을 생성하고 유지합니다. 이렇게 하면 사용자 인증 상태를 유지하면서 보안을 유지할 수 있습니다.

  그러나 세션 기반 인증은 여러 서버 및 클러스터에서 작동할 때 문제가 발생할 수 있습니다. 예를 들어 사용자가 다른 서버에 요청을 보낼 경우, 그 서버는 세션 정보를 가지고 있지 않기 때문에 사용자가 인증되지 않았다고 판단하게 됩니다. 이러한 문제를 해결하기 위해 Spring Security는 세션을 사용하지 않는 `STATELESS` 세션 생성 정책을 제공합니다.

  따라서 `SessionCreationPolicy.STATELESS`는 서버에서 세션을 생성하지 않고, 각 요청에 대해 새로운 인증 정보를 제공하도록 하는 것입니다. 이 방법으로 Spring Security는 세션을 사용하지 않고, 사용자가 인증된 요청만 처리합니다.