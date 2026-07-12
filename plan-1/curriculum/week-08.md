# 8주차: GC가 있는데도 메모리가 계속 늘어나는 이유는 무엇인가?

## 이번 주 한 문장

GC는 더 이상 도달할 수 없는 객체만 수거하므로, 애플리케이션이 필요 없는 객체를 계속
참조하면 그 객체는 사용되지 않아도 메모리에 남습니다.

## 답하기 위해 알아야 할 것

1. Java 애플리케이션은 객체를 만들 때 heap의 메모리를 사용합니다.
2. GC는 현재 실행 중인 thread, static field 같은 GC root에서 객체에 도달할 수 있는지
   추적합니다.
3. Root에서 더 이상 도달할 수 없는 객체는 수거 대상이 되지만 도달 가능한 객체는 사용 여부와
   관계없이 남을 수 있습니다.
4. Cache, listener, `ThreadLocal`이나 계속 커지는 collection이 불필요한 reference를 유지하면
   memory leak이 발생할 수 있습니다.
5. 메모리 증가를 볼 때는 객체 생성 속도, GC 후 남는 heap 크기와 어떤 객체가 reference를
   유지하는지 구분해서 판단합니다.

## 필수 키워드

1. Heap
2. GC root
3. Reachability
4. Memory leak
5. Allocation rate

## 설명의 도착점

- GC를 사용하지 않는 객체를 자동으로 찾아 지우는 기능이라고 설명하지 않습니다.
- 도달 가능성과 실제 사용 여부의 차이로 Java의 memory leak을 설명합니다.
- 메모리 사용량 증가를 높은 allocation과 살아남는 객체 증가로 나누어 설명합니다.

## 이번 주 제외 범위

- G1, ZGC와 다른 collector의 내부 알고리즘 비교
- GC option과 heap size tuning
- Off-heap과 native memory leak
- Heap dump 도구 사용 절차

## 발표에서 이어갈 질문

1. 더 이상 사용하지 않는 객체가 GC 대상이 되지 않을 수 있는 이유는 무엇입니까?
2. 요청이 많을 때만 heap 사용량이 빠르게 늘어난다면 memory leak이라고 단정할 수 있습니까?

## 상위 링크

- [16주 커리큘럼 목차](./README.md)
- [Plan 1 운영 안내](../README.md)
