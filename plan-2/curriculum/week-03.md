# 3주차: `@Transactional`을 붙였는데도 데이터가 예상과 다르게 저장되는 이유는 무엇인가?

## 이번 주 판단

`@Transactional`은 모든 호출에 자동으로 transaction을 보장하거나 entity 변경을 즉시 commit하는
표시가 아닙니다. Proxy 경계, 예외, persistence context와 DB transaction의 실제 흐름을 함께
봐야 합니다.

## 공개 시스템 전제

- 주문 확정 service가 managed entity를 변경하고 연관 상품 조회
- 일부 호출은 같은 Bean 안의 다른 `@Transactional` method로 연결
- 실행 중 checked exception 또는 runtime exception 발생 가능
- 목록 조회에는 N+1이 있고 같은 상품을 수정하는 요청 사이에는 충돌 존재
- 기준 환경은 Spring Boot 3.5.16, Spring Framework 6.2.19, Spring Data JPA 3.5.13
- JPA provider는 Hibernate ORM 6.6.53.Final, Persistence API는 Jakarta Persistence 3.1.0
- Database는 MySQL 8.4.x InnoDB이며 실제 프로젝트를 다루면 그 환경을 우선

## 공개 키워드

- AOP Proxy, transaction boundary와 self-invocation
- rollback rule과 exception 전파
- persistence context, dirty checking과 flush
- 선택 A: N+1과 fetch strategy
- 선택 B: optimistic·pessimistic locking

공통 키워드 세 개와 선택 A 또는 B 중 하나만 이번 주 범위로 사용합니다.

## 답변을 확장할 방향

- 정의: Framework transaction, persistence context와 DB transaction의 경계
- 동작: method 호출부터 entity 변경, SQL 실행과 commit·rollback까지의 과정
- 대안: transaction 경계를 구성하는 방법과 선택 분기의 해결 방식별 비용
- 실패와 측정: 예상과 다른 저장 결과나 성능·충돌 문제가 생기는 조건과 지표
- 적용과 철회: 한 경로부터 변경하고 문제가 생기면 이전 방식으로 되돌릴 기준

## 이번 주 제외 범위

- 모든 Spring annotation 암기
- provider가 다른 환경에 Hibernate 세부 동작을 그대로 적용
- Open Session in View 찬반만으로 설계 결론 내리기
- 실제 DB 없이 H2 결과만으로 MySQL lock 동작 확정
- 분산 transaction과 event-driven consistency
- 이번 주에 선택하지 않은 조회 성능 또는 동시성 분기

## 질문자 안내

실제 질문은 면접 대상자에게 공개하지 않습니다. 제목 질문을 그대로 사용하지 말고 호출 경계,
예외 종류, 조회량 또는 충돌률 중 하나 이상을 바꿉니다. 선택 A와 B 중 하나만 정해 스터디장에게
전달합니다.

## 상위 링크

[4주 커리큘럼 목록](./README.md) | [2안 운영 안내](../README.md)
