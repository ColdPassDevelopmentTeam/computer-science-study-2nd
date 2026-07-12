# 16주차: 언제 Monolith를 MSA로 나누어야 하는가?

## 이번 주 한 문장

독립 배포·확장·변경이나 팀별 소유권에서 얻는 이익이 network failure, 데이터 일관성,
observability와 운영 복잡성보다 클 때만 Monolith 분리를 고려합니다. 서비스가 커졌다는 이유만으로
MSA가 정답이 되지는 않습니다.

## 답하기 위해 알아야 할 것

1. 먼저 현재 문제를 확인합니다. 배포 충돌, 특정 기능만의 확장 요구나 팀 간 변경 대기 없이
   modular monolith의 내부 경계를 정리하는 것으로 해결할 수 있는지 판단합니다.
2. 분리가 필요하다면 함께 바뀌는 business capability를 중심으로 높은 응집도와 낮은 결합도를
   가진 service boundary를 찾고, 책임질 team ownership을 명확히 합니다.
3. 각 service는 자신의 데이터를 소유하고 API나 event로 다른 service와 협력해야 합니다.
   하나의 database transaction으로 끝나던 작업은 분리 후 데이터 일관성 문제가 됩니다.
4. Network 경계가 생기면 timeout, retry, 중복 처리와 partial failure를 다뤄야 합니다. 문제를
   발견하려면 일관된 log, metric, trace와 alert 같은 observability가 필요합니다.
5. Migration은 한 번에 전부 나누지 않고 측정 가능한 경계부터 점진적으로 진행하며, 운영 비용과
   장애가 커지면 되돌리거나 멈출 수 있는 경로를 함께 준비합니다.

## 필수 키워드

1. Service boundary
2. Data ownership
3. Distributed failure
4. Observability
5. Migration cost

## 설명의 도착점

- 기술 유행이 아니라 해결하려는 조직·배포·확장 문제부터 제시합니다.
- 경계 분리의 이익과 network·데이터·운영 비용을 같은 조건에서 비교합니다.
- 한 번에 전환하지 않고 관찰과 rollback이 가능한 점진적 migration 순서를 설명합니다.

## 이번 주 제외 범위

- MSA를 모든 규모의 system에 적용하는 전제
- Kubernetes와 service mesh의 설치·운영 방법
- Domain-Driven Design 전체 전술 pattern
- Saga, consensus와 event sourcing의 상세 구현

## 발표에서 이어갈 질문

1. 배포 충돌이 잦은 Monolith에서 service 분리 전에 modular monolith로 확인할 수 있는 해결책은
   무엇입니까?
2. 주문과 결제를 서로 다른 service로 분리하면 기존 transaction과 장애 처리 방식이 어떻게
   달라집니까?

## 상위 링크

- [16주 커리큘럼 목차](./README.md)
- [Plan 1 운영 안내](../README.md)
