# 2주차: Spring은 객체를 어떻게 만들고 연결하는가?

## 이번 주 한 문장

Spring Container는 설정을 바탕으로 애플리케이션 객체인 Bean을 만들고, 각 객체가 필요로 하는
다른 객체를 생성자에 전달해 연결합니다.

## 답하기 위해 알아야 할 것

1. 역할을 interface로 표현하면 사용하는 쪽이 구체적인 구현 class에 직접 묶이지 않습니다.
2. 상속으로 기능을 물려받는 대신 작은 객체를 조합하면 역할과 변경 범위를 나누기 쉽습니다.
3. Component scan이나 Java configuration이 어떤 객체를 만들지 Bean definition으로 등록합니다.
4. Spring Container가 Bean을 생성하고 필요한 dependency를 constructor로 주입합니다.
5. 객체 생성과 연결의 제어가 애플리케이션 코드 밖으로 이동해도 각 객체의 책임과 의존 관계는
   개발자가 설계합니다.

## 필수 키워드

1. Interface
2. Composition
3. IoC
4. DI
5. Bean

## 설명의 도착점

- interface가 필요한 이유를 구현 교체보다 역할과 의존 방향의 관점에서 설명합니다.
- 상속과 조합의 차이를 설명하고 변경 범위가 중요한 상황에서 조합을 선택할 수 있습니다.
- IoC, DI와 Spring Container의 관계를 객체 생성과 연결 순서로 설명합니다.

## 이번 주 제외 범위

- Bean scope와 순환 참조
- Bean post-processor의 내부 구현
- AOP Proxy와 Transaction
- 모든 의존성 주입 방식의 장단점 비교

## 발표에서 이어갈 질문

1. 생성자 주입은 객체가 반드시 필요로 하는 dependency를 어떻게 드러냅니까?
2. Interface가 없는 class도 Spring Bean으로 등록하고 주입할 수 있습니까?

## 상위 링크

- [16주 커리큘럼 목차](./README.md)
- [Plan 1 운영 안내](../README.md)
