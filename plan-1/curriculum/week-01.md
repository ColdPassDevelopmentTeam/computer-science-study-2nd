# 1주차: Spring과 Spring Boot는 무엇이 다른가?

## 이번 주 한 문장

Spring Framework는 객체 관리, 웹 요청 처리와 트랜잭션 같은 애플리케이션 기반 기능을
제공합니다. Spring Boot는 그 Spring 애플리케이션을 더 적은 설정으로 구성하고 실행할 수 있게
자동 설정, 기본값과 실행 방식을 제공합니다.

## 답하기 위해 알아야 할 것

1. Spring Framework가 애플리케이션 객체와 공통 기능을 관리하는 기반을 제공합니다.
2. 개발자는 필요한 Spring 모듈과 설정을 선택해 애플리케이션을 구성합니다.
3. Spring Boot는 classpath, property와 이미 등록된 설정을 확인해 자동 설정 후보를 선택합니다.
4. 개발자가 직접 설정한 내용이 있으면 조건에 따라 일부 자동 설정은 적용되지 않습니다.
5. Spring Boot가 애플리케이션 시작과 배포에 필요한 관례를 제공하더라도 실제 기능은 Spring
   Framework 위에서 동작합니다.

## 필수 키워드

1. Spring Framework
2. Spring Boot
3. Auto-configuration
4. Convention over configuration
5. Embedded server

## 설명의 도착점

- Spring Framework와 Spring Boot를 서로 다른 경쟁 제품으로 설명하지 않습니다.
- Spring Boot가 Spring을 대신하는 것이 아니라 구성과 실행을 단순화한다는 관계를 설명합니다.
- 자동 설정은 무조건 적용되는 마법이 아니라 조건에 따라 적용되거나 물러난다고 설명합니다.

## 이번 주 제외 범위

- Bean 생성과 의존성 주입의 상세 과정
- `ApplicationContext.refresh()`의 내부 단계
- Spring MVC 요청 처리와 Spring Transaction
- AOT와 native image

## 발표에서 이어갈 질문

1. Spring Boot 없이도 Spring Framework 애플리케이션을 만들 수 있습니까?
2. 자동 설정과 개발자가 직접 작성한 설정이 함께 있으면 어느 설정이 적용됩니까?

## 상위 링크

- [16주 커리큘럼 목차](./README.md)
- [Plan 1 운영 안내](../README.md)
