# 9주차: Process와 Thread는 무엇이 다르고 Blocking은 왜 비용이 되는가?

## 이번 주 한 문장

Process는 독립된 가상 주소 공간과 운영체제 자원을 가진 실행 단위이고, Thread는 그 안의
메모리와 자원을 공유하며 실행되는 흐름입니다. Blocking이 발생하면 해당 Thread는 일을
계속하지 못하므로 대기 중인 Thread가 많을수록 메모리와 scheduling 비용을 함께 고려해야 합니다.

## 답하기 위해 알아야 할 것

1. 프로그램을 실행하면 운영체제는 가상 주소 공간과 파일 같은 자원을 가진 Process를 만들고,
   Process 안에는 하나 이상의 Thread가 존재합니다.
2. 같은 Process의 Thread는 heap과 열린 자원을 공유하지만 각자 stack과 실행 상태를 가집니다.
   운영체제 scheduler는 실행 가능한 platform thread 중 실행할 대상을 선택합니다.
3. 파일이나 network I/O처럼 운영체제 기능이 필요하면 system call을 사용하며, 결과를 기다리는
   동안 Thread는 blocking되어 다음 명령을 실행하지 못할 수 있습니다.
4. Scheduler가 실행 대상을 바꾸면 register와 실행 위치를 저장하고 복원하는 context switch가
   발생합니다. 실행 가능한 Thread가 지나치게 많으면 이 전환과 cache 영향도 커질 수 있습니다.
5. Virtual Thread는 blocking I/O 중심 작업에서 적은 수의 carrier thread로 많은 작업을 다루기
   쉽게 하지만, CPU 성능이나 DB connection 같은 제한된 자원의 수를 늘려 주지는 않습니다.

## 필수 키워드

1. Process와 Thread
2. Scheduling과 context switch
3. System call과 blocking
4. Virtual Thread
5. CPU-bound와 I/O-bound

## 설명의 도착점

- Process의 격리 범위와 같은 Process 안에서 Thread가 공유하는 대상을 구분합니다.
- Blocking이 단순한 지연이 아니라 Thread와 제한된 자원을 점유하는 문제로 이어지는 과정을
  설명합니다.
- 작업 특성과 자원 상한을 먼저 밝힌 뒤 platform thread pool과 Virtual Thread를 선택합니다.

## 이번 주 제외 범위

- 운영체제별 Process 생성 과정과 scheduler algorithm
- CPU register 저장 형식과 context switch 구현 세부사항
- Virtual Thread pinning의 모든 사례와 JVM scheduler 내부 구현
- Reactive Streams와 non-blocking framework 비교

## 발표에서 이어갈 질문

1. DB connection을 기다리는 요청이 많을 때 Virtual Thread 수만 늘리면 해결되지 않는 이유는
   무엇입니까?
2. CPU 연산이 많은 작업과 blocking I/O가 많은 작업은 동시 실행 수를 어떤 기준으로 정해야
   합니까?

## 상위 링크

- [16주 커리큘럼 목차](./README.md)
- [Plan 1 운영 안내](../README.md)
