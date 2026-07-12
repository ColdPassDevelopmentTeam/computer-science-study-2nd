# 4주차: `@Transactional`을 붙이면 어디까지 하나의 작업이 되는가?

## 이번 주 한 문장

Database transaction은 관련 변경을 함께 commit하거나 rollback하는 작업 경계입니다. 기본적인
Spring Transaction은 외부 호출이 Transaction Proxy를 통과할 때 이 경계를 시작하고, method의
종료 결과에 따라 commit 또는 rollback합니다.

## 답하기 위해 알아야 할 것

1. Transaction은 함께 성공하거나 실패해야 할 DB 변경을 하나의 작업 경계로 묶습니다.
2. Spring은 `@Transactional` 대상 객체 앞에 Transaction Proxy를 둡니다.
3. 외부 호출이 Proxy를 통과하면 transaction interceptor가 transaction manager를 이용해
   transaction을 시작하거나 기존 transaction에 참여합니다.
4. 실제 method가 실행되는 동안 같은 실행 흐름의 DB 작업이 참여합니다. Method가 정상
   반환되면 commit을 시도하고, rollback rule에 해당하는 예외가 전파되면 rollback합니다.
5. 같은 객체 내부에서 method를 직접 호출하는 self-invocation은 Proxy를 다시 통과하지 않아
   새 transaction 설정이 적용되지 않을 수 있습니다.

## 필수 키워드

1. Transaction Proxy
2. Transaction interceptor
3. Transaction manager
4. Rollback rule
5. Self-invocation

## 설명의 도착점

- Annotation 자체가 transaction을 여는 것이 아니라 Proxy를 통한 호출이 시작점이라고
  설명합니다.
- Method 호출 경계와 실제 transaction 경계를 구분하고 예외 전파가 rollback에 미치는 영향을
  설명합니다.
- Self-invocation에서 기대한 transaction 설정이 적용되지 않을 수 있는 이유를 설명합니다.

## 이번 주 제외 범위

- DB isolation level, MVCC와 lock
- JPA persistence context, dirty checking과 flush
- 분산 transaction과 보상 transaction
- Transaction manager 구현체 내부

## 발표에서 이어갈 질문

1. Checked exception과 runtime exception은 기본 rollback 동작이 어떻게 다릅니까?
2. 같은 class의 `@Transactional` method를 내부에서 호출하면 왜 별도 설정이 적용되지 않을 수
   있습니까?

## 상위 링크

- [16주 커리큘럼 목차](./README.md)
- [Plan 1 운영 안내](../README.md)
