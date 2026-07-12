# 5주차: Java 코드는 컴파일러와 JVM을 거쳐 어떻게 실행되는가?

## 이번 주 한 문장

Java compiler는 source code의 구조와 type을 검사해 bytecode를 만들고, JVM은 그 bytecode를
검증하고 class를 준비한 뒤 interpreter와 JIT compiler로 실행합니다.

## 답하기 위해 알아야 할 것

1. Compiler는 source code를 의미 있는 최소 단위인 token으로 나누고, 문법 구조를 AST로
   표현한다고 개념적으로 이해합니다.
2. Compiler가 type이 맞는지 검사한 뒤 `javac`가 JVM이 이해할 수 있는 class file의 bytecode를
   만듭니다.
3. Class loader가 class file을 loading하면 JVM이 linking 과정에서 verification·preparation과
   필요 시 resolution을 수행하고, active use 전에 class를 initialization합니다.
4. Interpreter가 bytecode를 한 명령씩 실행하며 method 호출에는 stack frame, 객체 생성에는
   주로 heap을 사용합니다.
5. JVM은 자주 실행되는 code와 runtime 정보를 바탕으로 JIT compilation을 수행해 native code로
   실행할 수 있습니다.

## 필수 키워드

1. Token과 AST
2. Type check
3. Bytecode
4. Class loading
5. Interpreter와 JIT compiler

## 설명의 도착점

- Source code가 바로 CPU에서 실행되는 것이 아니라 compiler와 JVM 단계를 거친다고
  설명합니다.
- Compile-time type check, bytecode verification과 class loading의 책임을 구분합니다.
- Interpreter 실행과 runtime 정보를 이용한 JIT compilation의 차이를 설명합니다.

## 이번 주 제외 범위

- Compiler 제작과 parser 구현
- JVM bytecode instruction 전체 암기
- C1·C2 compiler phase와 최적화 세부사항
- GC 알고리즘과 tuning

## 발표에서 이어갈 질문

1. Java compiler의 type check와 JVM의 bytecode verification은 무엇이 다릅니까?
2. Java가 bytecode와 JIT compiler를 함께 사용하는 이유는 무엇입니까?

## 상위 링크

- [16주 커리큘럼 목차](./README.md)
- [Plan 1 운영 안내](../README.md)
