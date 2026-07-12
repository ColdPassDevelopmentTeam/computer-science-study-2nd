# 12주차: Index를 추가하면 조회는 왜 빨라지고 쓰기는 왜 느려지는가?

## 이번 주 한 문장

Index는 검색 key를 정렬된 구조로 관리해 조건에 맞는 row까지의 탐색 경로를 제공합니다. 대신
데이터를 추가하거나 바꿀 때 Index도 함께 수정해야 하므로 저장 공간과 쓰기 비용이 늘어납니다.

## 답하기 위해 알아야 할 것

1. 관계형 database는 데이터를 table의 row와 column으로 표현하고 primary key로 row를
   식별합니다. 이번 주에는 이 정도를 Index를 이해하기 위한 출발점으로만 사용합니다.
2. 조건에 맞는 row를 찾을 경로가 없으면 database는 table의 많은 row를 확인하는 table scan을
   수행할 수 있습니다.
3. 관계형 database에서 흔히 사용하는 B+Tree Index는 정렬된 key를 따라 범위를 좁혀 원하는
   row의 위치를 찾습니다.
4. Optimizer는 query 조건, 통계와 예상 비용을 비교해 table scan과 Index access를 포함한
   query plan을 선택합니다. Index가 있어도 항상 사용되는 것은 아닙니다.
5. Insert, update와 delete는 관련 Index도 갱신해야 하며, Index가 많을수록 추가 저장 공간과
   쓰기 작업이 필요합니다.

## 필수 키워드

1. Table, row와 primary key
2. B+Tree Index
3. Table scan과 Index access
4. Query plan
5. Read-write trade-off

## 설명의 도착점

- Table과 key의 역할을 먼저 설명한 뒤 Index가 검색 경로를 제공하는 자료구조라는 점을
  연결합니다.
- Query 조건과 데이터 분포에 따라 Index의 효과가 달라지는 이유를 설명합니다.
- 빠른 조회뿐 아니라 Index 유지에 필요한 쓰기·공간 비용까지 함께 판단합니다.

## 이번 주 제외 범위

- B+Tree page 구조와 page split의 구현 세부사항
- Optimizer cost model의 모든 계산식
- 모든 join algorithm과 optimizer hint
- 관계형 모델링, normalization과 constraint 설계
- Partitioning, replication과 distributed database

## 발표에서 이어갈 질문

1. 값의 종류가 매우 적은 column에 단일 Index를 추가해도 효과가 작을 수 있는 이유는
   무엇입니까?
2. 여러 column을 묶은 Index는 column의 순서에 따라 사용할 수 있는 query가 왜 달라집니까?

## 상위 링크

- [16주 커리큘럼 목차](./README.md)
- [Plan 1 운영 안내](../README.md)
