# 11주차: 브라우저에 URL을 입력하면 서버 응답까지 어떤 일이 일어나는가?

## 이번 주 한 문장

이번 주의 HTTP/1.1·HTTP/2 기반 HTTPS 요청에서 브라우저는 URL의 접속 대상을 확인하고, DNS로
주소를 찾은 뒤 TCP와 TLS 연결을 거쳐 HTTP 요청을 보냅니다. Cache나 재사용할 연결이 있다면
일부 단계는 생략될 수 있습니다.

## 답하기 위해 알아야 할 것

1. 브라우저는 URL의 scheme, host, port와 path를 구분하고, 먼저 사용할 수 있는 cache와 기존
   connection이 있는지 확인합니다.
2. 새 연결이 필요하면 DNS가 domain name을 서버의 IP address로 바꿉니다.
3. 이번 주에 다루는 HTTP/1.1·HTTP/2 기반 HTTPS 연결에서는 TCP가 신뢰할 수 있는 byte 전달
   경로를 만들고, TLS가 서버 인증서 확인과 암호화된 통신 조건을 협상합니다.
4. 연결이 준비되면 브라우저가 HTTP request를 보내고, 서버는 status, header와 body로 구성된
   HTTP response를 돌려줍니다.
5. DNS 조회, connection, TLS와 response 대기는 서로 다른 단계이므로 장애 원인과 timeout도
   단계별로 구분해야 합니다.

## 필수 키워드

1. URL과 DNS
2. TCP connection
3. TLS
4. HTTP request와 response
5. Cache와 connection reuse

## 설명의 도착점

- DNS, TCP, TLS와 HTTP가 각각 해결하는 문제를 순서대로 설명합니다.
- Cache hit나 기존 connection 재사용으로 생략되는 단계를 구분합니다.
- 요청 실패를 하나로 묶지 않고 주소 조회, 연결, 암호화와 응답 대기 중 어느 단계인지 나눕니다.

## 이번 주 제외 범위

- BGP와 인터넷 routing protocol의 세부 동작
- TLS cipher와 공개키 암호의 수학적 원리
- HTTP/2 frame, HTTP/3와 QUIC의 세부 구현
- HTML parsing, rendering과 JavaScript 실행 과정

## 발표에서 이어갈 질문

1. 같은 서버에 두 번째 HTTPS 요청을 보낼 때 첫 요청보다 생략될 수 있는 단계는 무엇입니까?
2. TCP가 전송을 보장해도 서버가 같은 요청을 두 번 처리할 수 있는 이유는 무엇입니까?

## 상위 링크

- [16주 커리큘럼 목차](./README.md)
- [Plan 1 운영 안내](../README.md)
