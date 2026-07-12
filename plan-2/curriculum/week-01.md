# 1주차: Virtual Thread로 바꾸면 동시성 문제와 성능 병목이 해결되는가?

## 이번 주 판단

Virtual Thread는 blocking I/O를 처리하는 thread 비용을 줄일 수 있지만 공유 상태의 동시성
문제나 DB·외부 API의 처리 한도를 해결하지는 않습니다. 전환 여부는 workload와 실제 병목을
구분해 판단해야 합니다.

## 공개 시스템 전제

- JDK 21과 HotSpot JVM에서 동작하는 주문 API
- 고정 크기 platform thread pool에서 blocking HTTP·JDBC 작업 처리
- 여러 thread가 `volatile int count`에 `count++`를 실행해 처리 건수 기록
- CPU보다 blocking I/O 대기 비중이 높고 DB connection pool과 외부 API 처리량에는 상한 존재
- 기능은 유지한 채 요청당 Virtual Thread 방식으로 단계적 전환 검토
- 전환 전후의 부하 조건과 측정 구간은 동일

## 공개 키워드

- Java Memory Model과 happens-before
- atomicity, visibility와 ordering
- `volatile`, `synchronized`와 atomic type
- platform thread와 Virtual Thread
- thread dump와 JFR

## 답변을 확장할 방향

- 정의: 공유 상태의 안전성과 실행 모델을 설명할 때 구분해야 할 개념
- 동작: 여러 thread의 복합 연산과 blocking I/O가 실행되는 과정
- 대안: 상태를 보호하는 방법과 요청을 실행하는 방식별 이익과 비용
- 실패와 측정: 병목이 다른 자원으로 이동하는 조건과 확인할 지표
- 적용과 철회: 일부 요청부터 전환하고 기존 방식으로 되돌릴 판단 기준

## 이번 주 제외 범위

- Garbage collector별 세부 tuning flag 암기
- JVM source code 전체 추적
- reactive programming과 structured concurrency 비교
- 한 번의 benchmark로 production 성능을 확정하는 판단

## 질문자 안내

실제 질문은 면접 대상자에게 공개하지 않습니다. 제목 질문을 그대로 사용하지 말고 부하,
공유 상태 또는 downstream 실패 조건 중 하나 이상을 바꿔 스터디장에게 전달합니다.

## 상위 링크

[4주 커리큘럼 목록](./README.md) | [2안 운영 안내](../README.md)
