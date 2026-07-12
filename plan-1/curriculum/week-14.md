# 14주차: JPA Entity의 변경은 언제 SQL이 되고 DB에 반영되는가?

## 이번 주 한 문장

JPA는 persistence context가 관리하는 Entity의 변경을 감지해 flush할 때 SQL로 전달합니다.
Flush는 SQL을 보내는 시점이고, 실제 변경의 확정은 database transaction이 commit될 때입니다.

## 답하기 위해 알아야 할 것

1. JPA로 조회하거나 새로 저장한 Entity는 조건에 따라 persistence context가 관리하는 managed
   state가 되며, 같은 식별자의 Entity를 하나의 객체로 관리합니다.
2. Managed Entity의 field를 바꾸면 JPA provider가 기존 상태와 비교하는 dirty checking의
   대상이 되므로 update method를 별도로 호출하지 않아도 변경 SQL이 만들어질 수 있습니다.
3. Flush가 일어나면 필요한 SQL이 database로 전달됩니다. Query 실행 전이나 transaction
   commit 과정에서 flush될 수 있지만, flush 자체가 commit을 뜻하지는 않습니다.
4. Transaction이 commit되면 변경이 확정되고 rollback되면 앞서 실행된 SQL의 변경도
   취소됩니다.

## 필수 키워드

1. Persistence context
2. Managed Entity와 dirty checking
3. Flush와 commit
4. Transaction boundary

## 설명의 도착점

- Entity 변경, dirty checking, SQL 생성, flush와 commit을 시간 순서로 설명합니다.
- Flush된 SQL도 transaction이 rollback되면 확정되지 않는다는 점을 구분합니다.
- Persistence context와 DB transaction이 같은 개념이 아니며 flush와 commit의 책임도 다르다고
  설명합니다.

## 이번 주 제외 범위

- JPA provider의 dirty checking 구현 algorithm
- 모든 Entity state 전이와 cascade 조합
- Second-level cache와 Open Session in View의 세부 설정
- Fetch join pagination과 provider별 최적화 기법
- N+1과 fetch 전략은 발표 후속 질문으로만 다룸

## 발표에서 이어갈 질문

1. Transaction 안에서 SQL log가 보였는데도 최종 데이터가 바뀌지 않을 수 있는 이유는
   무엇입니까?
2. 회원 목록 한 번을 조회한 뒤 각 회원의 주문을 읽을 때 N+1이 어떻게 발생합니까?

## 상위 링크

- [16주 커리큘럼 목차](./README.md)
- [Plan 1 운영 안내](../README.md)
