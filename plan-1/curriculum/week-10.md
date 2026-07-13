# 10주차: 여러 Thread가 같은 값을 바꾸면 왜 결과가 달라지는가?

## 이번 주 한 문장

공유 값을 바꾸는 여러 Thread의 실행 순서가 매번 달라질 수 있고, 동기화가 없으면 한 Thread의
변경을 다른 Thread가 언제 보게 될지도 보장되지 않습니다. Java Memory Model은 이 문제를
atomicity, visibility와 happens-before 관계로 설명합니다.

## 답하기 위해 알아야 할 것

1. 여러 Thread가 같은 mutable state를 읽고 쓰면 실행 순서에 따라 결과가 달라지는 race
   condition이 생길 수 있습니다.
2. `count++`는 하나의 동작처럼 보이지만 실제로는 값을 읽고, 계산하고, 다시 쓰는 복합
   연산이므로 두 Thread의 단계가 섞이면 변경이 유실될 수 있습니다.
3. Java Memory Model은 Thread 사이에서 어떤 값이 보여야 하는지와 연산 순서를 언제 보장하는지
   정의하며, happens-before 관계가 그 판단 기준이 됩니다.
4. `synchronized`는 같은 monitor를 사용하는 구간에 mutual exclusion을 제공하고 unlock 이후의
   변경이 다음 lock에 보이도록 합니다.
5. 같은 변수에 대한 volatile write는 이후 volatile read보다 happens-before입니다. 이 관계는
   write 이전 변경의 visibility와 관련 재배치 제한을 제공하지만 `count++` 전체를 atomic하게
   만들지는 않으므로, 복합 연산에는 lock이나 atomic class가 필요합니다.

## 필수 키워드

1. Race condition
2. Atomicity
3. Visibility와 happens-before
4. `synchronized`
5. `volatile`

## 설명의 도착점

- 실행 순서 문제와 다른 Thread의 변경을 보지 못하는 문제를 구분합니다.
- `count++`의 read-modify-write 단계를 이용해 변경 유실을 설명합니다.
- `synchronized`, volatile write-read happens-before와 atomic class가 각각 보장하는 범위를
  비교합니다.

## 이번 주 제외 범위

- CPU cache coherence protocol과 memory barrier의 기계어 구현
- Java Memory Model의 모든 happens-before 규칙 암기
- JVM monitor와 lock optimization 내부 구현
- 모든 concurrent collection과 lock-free algorithm

## 발표에서 이어갈 질문

1. `volatile int count`에 여러 Thread가 `count++`을 실행하면 값이 유실될 수 있는 이유는
   무엇입니까?
2. 공유 상태를 없애는 설계는 lock을 추가하는 방식과 비교해 어떤 장점이 있습니까?

## 상위 링크

- [16주 커리큘럼 목차](./README.md)
- [Plan 1 운영 안내](../README.md)
