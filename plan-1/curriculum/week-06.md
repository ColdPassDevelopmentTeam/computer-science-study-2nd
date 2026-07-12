# 6주차: Java에서 객체를 전달하고 비교할 때 실제로 무엇을 다루는가?

## 이번 주 한 문장

Java는 method argument를 항상 값으로 전달하며, 객체를 넘길 때는 객체 자체가 아니라 객체를
가리키는 reference value가 복사됩니다. 객체 비교에서는 동일한 객체인지와 같은 의미의 값인지
구분해야 합니다.

## 답하기 위해 알아야 할 것

1. Primitive variable에는 숫자나 논리값 같은 primitive value가 저장됩니다.
2. Reference variable에는 객체 자체가 아니라 객체를 가리키는 reference value가 저장됩니다.
3. Method 호출은 primitive value 또는 reference value를 parameter에 복사하므로 Java는 항상
   pass-by-value입니다.
4. `==`는 primitive value 또는 reference identity를 비교하고, `equals()`는 객체가 정의한
   logical equality를 비교합니다.
5. 같은 의미의 객체가 hash 기반 collection에서도 같게 취급되려면 `equals()`와 `hashCode()`의
   계약을 함께 지켜야 합니다.

## 필수 키워드

1. Primitive value
2. Reference value
3. Pass-by-value
4. Identity와 equality
5. `equals()`와 `hashCode()`

## 설명의 도착점

- Java의 객체 전달을 pass-by-reference라고 부르지 않고 reference value의 복사로 설명합니다.
- Parameter가 다른 객체를 가리키게 하는 것과 전달받은 객체의 상태를 변경하는 것을 구분합니다.
- `==`, `equals()`와 `hashCode()`가 각각 필요한 이유를 실제 collection 동작과 연결합니다.

## 이번 주 제외 범위

- JVM object header와 reference 압축
- `System.identityHashCode()` 구현
- 깊은 복사 library 비교
- Value Object 설계 전반

## 발표에서 이어갈 질문

1. Method 안에서 parameter에 새 객체를 대입해도 호출자의 변수가 바뀌지 않는 이유는
   무엇입니까?
2. `equals()`만 재정의하고 `hashCode()`를 재정의하지 않으면 어떤 문제가 생깁니까?

## 상위 링크

- [16주 커리큘럼 목차](./README.md)
- [Plan 1 운영 안내](../README.md)
