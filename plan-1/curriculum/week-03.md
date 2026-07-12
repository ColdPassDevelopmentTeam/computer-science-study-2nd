# 3주차: HTTP 요청은 어떻게 Controller까지 도착하는가?

## 이번 주 한 문장

웹 서버가 받은 HTTP 요청은 Servlet Container와 Filter를 지나 `DispatcherServlet`에 도착하고,
Spring MVC가 요청에 맞는 Controller를 찾아 실행한 뒤 응답이나 예외를 HTTP 결과로 바꿉니다.

## 답하기 위해 알아야 할 것

1. Servlet Container가 network에서 들어온 HTTP 요청을 Servlet 요청과 응답 객체로 만듭니다.
2. Filter chain이 인증, logging처럼 Controller 앞뒤에 필요한 공통 처리를 수행합니다.
3. `DispatcherServlet`이 요청을 받고 `HandlerMapping`을 통해 실행할 Controller method를 찾습니다.
4. `HandlerAdapter`가 입력값 변환과 validation을 거쳐 Controller method를 호출하고 반환값을
   HTTP 응답으로 변환합니다.
5. Spring MVC 안에서 발생한 예외는 `HandlerExceptionResolver`가 처리할 수 있지만, Filter에서
   발생한 예외는 MVC 바깥에 있으므로 Filter 경계에서 별도로 처리해야 합니다.

## 필수 키워드

1. Servlet Container
2. Filter
3. `DispatcherServlet`
4. `HandlerMapping`
5. Exception boundary

## 설명의 도착점

- HTTP 요청이 Controller를 바로 호출하는 것이 아니라 여러 처리 단계를 지난다고 설명합니다.
- Filter와 Spring MVC 내부 처리의 실행 위치와 책임을 구분합니다.
- 예외가 발생한 위치에 따라 처리할 수 있는 경계가 달라진다고 설명합니다.

## 이번 주 제외 범위

- Servlet Container별 thread model과 connector 설정
- 모든 argument resolver와 message converter 구현
- Spring WebFlux
- 인증과 인가의 상세 흐름

## 발표에서 이어갈 질문

1. Filter와 `HandlerInterceptor`는 요청 흐름에서 어디에 위치합니까?
2. Controller에 도착하기 전에 발생한 예외를 `@ControllerAdvice`가 처리하지 못할 수 있는 이유는
   무엇입니까?

## 상위 링크

- [16주 커리큘럼 목차](./README.md)
- [Plan 1 운영 안내](../README.md)
