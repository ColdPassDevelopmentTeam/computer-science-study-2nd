# 4주차: MSA로 나누면 배포·장애·보안 문제가 실제로 줄어드는가?

## 이번 주 판단

MSA는 경계와 운영 역량이 준비된 경우 독립 배포와 장애 격리에 도움이 될 수 있지만 분산 통신,
데이터와 보안 운영 비용을 늘립니다. 시스템과 조직 조건 없이 서비스 분리 자체를 해답으로
볼 수 없습니다.

## 공개 시스템 전제

- 하나의 backend에서 여러 팀의 배포 충돌과 큰 장애 영향 범위 발생
- 현재 모듈 경계와 DB table 소유권은 일부만 분리
- 배포·관측·온콜 자동화 수준은 측정 가능
- 즉시 전면 재작성 대신 modular monolith 유지 또는 점진적 MSA 전환 검토
- 현재 Monolith의 인증과 권한 정책을 service 사이의 trust boundary에도 적용해야 함
- Service 분리 뒤에는 최소 권한, service-to-service 인증과 접근 권한의 소유 주체를 다시 정해야 함

## 공개 키워드

- quality attribute, service boundary와 data ownership
- coupling, deployment autonomy와 distributed cost
- SLI·SLO, observability와 failure isolation
- rollback, graceful degradation과 incident response
- trust boundary, authentication·authorization와 least privilege

## 답변을 확장할 방향

- 정의: 배포·runtime·데이터·신뢰 경계와 책임 주체
- 동작: 서비스 분리 뒤 요청, 장애, 인증 정보와 데이터가 경계를 지나는 과정
- 대안: monolith, modular monolith와 MSA의 이익과 비용
- 실패와 측정: 분산 전환 또는 trust boundary 설계가 실패하는 조건과 확인할 지표
- 적용과 철회: 작은 범위부터 전환하고 기능을 축소하거나 이전 구조로 돌릴 기준

## 이번 주 제외 범위

- 서비스 개수나 회사 규모만으로 MSA 필요 여부 결정
- 특정 cloud 제품 이름 나열
- 개인 책임 추궁과 합격·불합격 판정
- 특정 보안 사고의 완전한 incident runbook 작성

## 질문자 안내

실제 질문은 면접 대상자에게 공개하지 않습니다. 제목 질문의 조직 규모, traffic, 장애 영향,
data ownership 또는 trust boundary 중 하나 이상을 바꿔 스터디장에게 전달합니다.

## 상위 링크

[4주 커리큘럼 목록](./README.md) | [2안 운영 안내](../README.md)
