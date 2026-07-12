# 13주차: 두 요청이 같은 데이터를 바꾸면 DB는 어떻게 일관성을 지키는가?

## 이번 주 한 문장

Database는 관련 작업을 transaction으로 묶고 isolation level에 따라 서로의 변경을 보여 주는
범위를 정합니다. MVCC와 lock으로 읽기와 쓰기 충돌을 조정한 뒤 commit하거나 rollback합니다.

## 답하기 위해 알아야 할 것

1. Transaction은 함께 성공하거나 실패해야 하는 작업의 경계이며, ACID는 그 경계가 지켜야 할
   atomicity, consistency, isolation과 durability를 나타냅니다.
2. Isolation level은 동시에 실행되는 transaction이 아직 끝나지 않았거나 먼저 끝난 변경을
   언제 볼 수 있는지와 어떤 anomaly를 허용할지 결정합니다.
3. MVCC는 여러 version의 row를 이용해 reader가 정해진 시점의 일관된 내용을 보게 하며,
   일반적인 조회가 writer를 항상 기다리지 않도록 돕습니다.
4. 같은 데이터를 변경하거나 잠금을 요구하는 조회는 lock을 사용할 수 있습니다. 순서에 따라
   lock wait, lost update 또는 서로가 기다리는 deadlock이 발생할 수 있습니다.
5. Commit은 transaction의 변경을 확정하고 rollback은 취소합니다. Deadlock 등으로 rollback된
   경우 application은 일부 query가 아니라 transaction 전체의 재시도 가능성을 판단합니다.

## 필수 키워드

1. ACID와 transaction boundary
2. Isolation level
3. MVCC
4. Lock과 deadlock
5. Commit과 rollback

## 설명의 도착점

- Transaction을 annotation이 아니라 일관성을 지켜야 하는 업무 경계로 설명합니다.
- MVCC가 담당하는 일관된 읽기와 변경 충돌에서 lock이 담당하는 역할을 구분합니다.
- 두 요청의 실제 read-modify-write 순서로 lost update와 대응 방법을 설명합니다.

## 이번 주 제외 범위

- 특정 DBMS의 record·gap·next-key lock 세부 규칙
- Undo log와 version 정리 과정의 내부 구현
- XA와 distributed transaction
- 모든 isolation anomaly의 형식적 증명

## 발표에서 이어갈 질문

1. 두 요청이 같은 재고를 읽은 뒤 각각 차감하면 lost update가 어떻게 발생합니까?
2. Optimistic locking과 pessimistic locking은 충돌 가능성과 비용이 어떻게 다릅니까?

## 상위 링크

- [16주 커리큘럼 목차](./README.md)
- [Plan 1 운영 안내](../README.md)
