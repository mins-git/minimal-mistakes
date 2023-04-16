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



# Project 진행중 알게된 부분



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