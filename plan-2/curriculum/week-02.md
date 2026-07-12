# 2주차: Timeout 뒤 재시도해도 중복 처리와 DB 경합을 막을 수 있는가?

## 이번 주 판단

Timeout은 상대 작업의 실패를 확정하지 않으며 재시도는 중복 처리와 부하를 늘릴 수 있습니다.
외부 호출의 실패 계약과 DB의 동시성 제어를 하나의 업무 흐름 안에서 판단해야 합니다.

## 공개 시스템 전제

- 주문 서비스가 결제 서비스에 HTTP 요청을 보내고 MySQL 8.4.x InnoDB의 재고 차감
- 외부 호출은 HTTP/2 over TLS/TCP를 사용하며 connection pool 재사용 가능
- 간헐적인 Timeout 뒤 client retry와 동시 재고 차감으로 중복 결제와 lost update 발생
- 하나의 전역 deadline 안에 외부 호출과 DB 처리 존재
- 결제 API는 idempotency key를 받을 수 있지만 저장·만료 정책은 미정
- 재고 row의 충돌률과 retry 성공률은 측정 가능하며 분산 transaction은 제외

## 공개 키워드

- timeout, deadline과 cancellation
- retry, backoff와 retry budget
- HTTP semantics와 idempotency key
- MVCC, isolation level과 lost update
- optimistic·pessimistic lock과 atomic update

## 답변을 확장할 방향

- 정의: Timeout, 재시도, 멱등성과 transaction 격리의 책임 경계
- 동작: 응답을 받지 못한 요청과 동시에 같은 재고를 변경하는 요청의 처리 과정
- 대안: 재시도 정책, 중복 차단과 DB 갱신 방식별 이익과 비용
- 실패와 측정: 장애 증폭·중복·경합이 발생하는 조건과 확인할 지표
- 적용과 철회: 제한된 범위에 정책을 적용하고 중단하거나 이전 방식으로 돌릴 기준

## 이번 주 제외 범위

- HTTP header와 상태 코드 전체 암기
- 모든 Timeout에 동일한 retry 정책 적용
- MySQL replication·sharding의 상세 구현
- 분산 transaction protocol 비교
- production 결제·개인정보를 사용한 사례

## 질문자 안내

실제 질문은 면접 대상자에게 공개하지 않습니다. 제목 질문을 그대로 사용하지 말고 API의
멱등성, DB 충돌률 또는 장애 지점 중 하나 이상을 바꿔 스터디장에게 전달합니다.

## 상위 링크

[4주 커리큘럼 목록](./README.md) | [2안 운영 안내](../README.md)
