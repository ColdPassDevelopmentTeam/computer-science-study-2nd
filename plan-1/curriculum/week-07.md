# 7주차: `List`, `Set`, `Map`은 언제 무엇을 선택해야 하는가?

## 이번 주 한 문장

순서와 중복이 필요한 값의 모음에는 `List`, 중복 없는 값의 모음에는 `Set`, key로 값을 찾는
관계에는 `Map`을 선택하고 실제 접근과 변경 패턴에 맞는 구현체를 결정합니다.

## 답하기 위해 알아야 할 것

1. 저장하려는 데이터에 순서, 중복 허용과 key 기반 조회가 필요한지 먼저 구분합니다.
2. `List`는 순서와 중복을 유지하고 index로 원소에 접근할 수 있습니다.
3. `Set`은 중복을 허용하지 않지만 중복 판단 기준은 구현체에 따라 다릅니다. `HashSet`은
   `equals()`·`hashCode()`를, 정렬된 Set은 객체의 비교 결과를 사용합니다.
4. `Map`은 key와 value의 관계를 저장하고 `HashMap`은 key의 `hashCode()`와 `equals()`를 이용해
   값을 찾습니다.
5. Generics는 collection에 넣고 꺼낼 수 있는 type을 compile time에 제한합니다.

## 필수 키워드

1. `List`
2. `Set`
3. `Map`
4. `HashMap`
5. Generics

## 설명의 도착점

- Collection을 익숙한 구현체로 고르지 않고 데이터의 의미와 접근 방식으로 선택합니다.
- `HashSet`과 `HashMap`의 중복·조회 동작을 equality 계약과 연결해 설명합니다.
- Generics가 runtime의 모든 type 문제를 해결하는 것이 아니라 compile-time type safety를
  제공한다고 설명합니다.

## 이번 주 제외 범위

- 모든 collection 구현체의 시간 복잡도 암기
- Concurrent collection
- Generic type erasure의 bytecode 세부사항
- 직접 구현하는 hash table과 tree

## 발표에서 이어갈 질문

1. 순서가 필요한 중복 없는 데이터라면 어떤 collection을 선택하겠습니까?
2. Mutable object를 `HashMap`의 key로 사용할 때 무엇을 주의해야 합니까?

## 상위 링크

- [16주 커리큘럼 목차](./README.md)
- [Plan 1 운영 안내](../README.md)
