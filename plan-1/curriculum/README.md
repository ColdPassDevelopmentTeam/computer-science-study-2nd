# 1안 16주 커리큘럼

[1안 운영 규칙](../README.md)

## 커리큘럼 개요

매주 용어 목록이 아니라 실제로 답해야 할 질문 하나에서 시작합니다. Spring처럼 현재 사용하는
기술에서 compiler·JVM·OS·network·database 기반으로 내려가고, 다시 JPA·Security·architecture
판단으로 올라옵니다.

각 주차의 필수 범위만 공부하며 제외 범위를 추가 과제로 만들지 않습니다. 16주는 완료한 16개
세션을 뜻하므로, 세션이 취소되면 주차를 건너뛰지 않고 다음 일정에 이어서 진행합니다.

## 매주 읽는 순서

1. 주차 제목의 질문에 자료 없이 한 문장으로 먼저 답합니다.
2. `이번 주 한 문장`과 내 답이 어떻게 다른지 확인합니다.
3. 필수 키워드 3~5개로 결론의 동작과 조건을 설명합니다.
4. 개인 TIL에 내 설명과 헷갈리는 점을 짧게 누적합니다.
5. 주말 발표에서 결론부터 말하고 동작과 조건을 이어서 설명합니다.

각 주차의 선택 질문은 발표 후 대화가 자연스럽게 이어질 때만 참고합니다. 미리 준비하거나
모두 질문할 의무는 없습니다.

## 1~4주: Spring에서 질문 시작하기

| 주차 | 이번 주 질문 | 설명의 도착점 |
|---:|---|---|
| [1주차](./week-01.md) | Spring과 Spring Boot는 무엇이 다른가? | Framework의 책임과 Boot가 추가하는 자동 구성·실행 편의 구분 |
| [2주차](./week-02.md) | Spring은 객체를 어떻게 만들고 연결하는가? | IoC·DI와 객체 설계의 관계를 생성 순서로 설명 |
| [3주차](./week-03.md) | HTTP 요청은 어떻게 Controller까지 도착하는가? | Web server부터 Spring MVC 응답·예외 처리까지 연결 |
| [4주차](./week-04.md) | `@Transactional`을 붙이면 어디까지 하나의 작업이 되는가? | Proxy가 만드는 method 경계와 적용되지 않는 호출 구분 |

## 5~8주: Java 코드 아래로 내려가기

| 주차 | 이번 주 질문 | 설명의 도착점 |
|---:|---|---|
| [5주차](./week-05.md) | Java 코드는 컴파일러와 JVM을 거쳐 어떻게 실행되는가? | token·syntax tree·type check부터 JDK 21 HotSpot의 bytecode 실행·JIT까지 연결 |
| [6주차](./week-06.md) | Java에서 객체를 전달하고 비교할 때 실제로 무엇을 다루는가? | pass-by-value와 `==`·`equals()`·`hashCode()` 계약 설명 |
| [7주차](./week-07.md) | `List`, `Set`, `Map`은 언제 무엇을 선택해야 하는가? | 접근·변경 패턴과 type safety를 기준으로 collection 선택 |
| [8주차](./week-08.md) | GC가 있는데도 메모리가 계속 늘어나는 이유는 무엇인가? | reachability, allocation과 memory leak 구분 |

## 9~12주: OS·동시성·Network·Database 기초

| 주차 | 이번 주 질문 | 설명의 도착점 |
|---:|---|---|
| [9주차](./week-09.md) | Process와 Thread는 무엇이 다르고 Blocking은 왜 비용이 되는가? | OS 실행 단위와 platform·virtual thread의 비용 구분 |
| [10주차](./week-10.md) | 여러 Thread가 같은 값을 바꾸면 왜 결과가 달라지는가? | atomicity와 같은 volatile 변수의 write-read happens-before 구분 |
| [11주차](./week-11.md) | 브라우저에 URL을 입력하면 서버 응답까지 어떤 일이 일어나는가? | DNS·TCP·TLS·HTTP를 하나의 요청 흐름으로 설명 |
| [12주차](./week-12.md) | B+Tree Index를 추가하면 조회는 왜 빨라지고 쓰기는 왜 느려지는가? | 관계형 table, B+Tree와 query plan을 비용으로 연결 |

## 13~16주: Data와 운영 판단으로 다시 올라오기

| 주차 | 이번 주 질문 | 설명의 도착점 |
|---:|---|---|
| [13주차](./week-13.md) | 두 요청이 같은 데이터를 바꾸면 DB는 어떻게 일관성을 지키는가? | transaction·isolation·MVCC·lock의 역할 구분 |
| [14주차](./week-14.md) | JPA Entity의 변경은 언제 SQL이 되고 DB에 반영되는가? | persistence context·dirty checking·flush·commit 연결 |
| [15주차](./week-15.md) | 로그인과 권한 확인은 서버 안에서 어떻게 이어지는가? | authentication·authorization과 session·token 흐름 구분 |
| [16주차](./week-16.md) | 언제 Monolith를 MSA로 나누어야 하는가? | 경계·data ownership·분산 실패·운영 비용을 근거로 선택 |

## 4주 단위 점검

4, 8, 12, 16주차 세션 마지막 10분에는 문서를 추가하지 않고 다음만 말로 확인합니다.

1. 주차 질문에 결론부터 1~2문장으로 답할 수 있는가?
2. 필수 키워드를 나열하지 않고 하나의 동작 흐름으로 연결할 수 있는가?
3. 조건이 달라지면 결론도 달라질 수 있음을 설명할 수 있는가?

4, 8, 12주차에는 범위를 늘리지 않고 어려웠던 용어만 다음 주 설명에서 짧게 연결합니다.
16주차에는 [2안](../../plan-2/)으로 전환, 1안 반복 또는 종료 중 하나를 정합니다.
