# 15주차: 로그인과 권한 확인은 서버 안에서 어떻게 이어지는가?

## 이번 주 한 문장

서버는 filter chain에서 session이나 token으로 사용자의 신원을 확인한 뒤 현재 요청의 인증
정보를 만들고, 보호할 기능이나 데이터에 접근할 권한이 있는지 별도로 판단합니다.

## 답하기 위해 알아야 할 것

1. 요청은 controller에 도착하기 전에 security filter chain을 지나며, 각 filter가 인증 정보의
   추출과 확인 또는 다음 filter로의 전달을 담당합니다.
2. 최초 로그인에서는 ID와 password 같은 credential을 확인합니다. 이후 session 방식은 cookie의
   session ID로 server-side 인증 상태를 찾고, bearer token 방식은 요청마다 token을 확인합니다.
3. Authentication이 성공하면 서버는 사용자의 identity와 role 같은 정보를 현재 요청의 security
   context에 연결합니다.
4. Authorization은 인증된 사용자가 URL, method 또는 특정 domain resource에 접근할 권한이
   있는지 판단합니다. 로그인 성공이 모든 작업의 허용을 뜻하지는 않습니다.
5. 인증 정보가 없거나 유효하지 않은 경우와 인증은 됐지만 권한이 부족한 경우는 실패 원인과
   응답을 구분해야 합니다.

## 필수 키워드

1. Authentication과 authorization
2. Security filter chain
3. Session과 cookie
4. Bearer token
5. Security context

## 설명의 도착점

- 최초 로그인과 이후 요청에서 인증 상태를 확인하는 과정을 구분합니다.
- Session 방식의 server-side 상태와 token 방식의 요청별 확인 흐름을 비교합니다.
- Authentication 성공 이후 authorization이 별도로 수행되는 이유를 설명합니다.

## 이번 주 제외 범위

- OAuth 2.0 authorization grant 전체
- JWT signature algorithm과 key rotation 구현
- CSRF와 CORS의 상세 설정
- Password hashing algorithm의 내부 수학

## 발표에서 이어갈 질문

1. Session 방식과 bearer token 방식에서 서버가 다음 요청의 사용자를 알아내는 과정은 어떻게
   다릅니까?
2. 로그인한 사용자가 다른 사용자의 게시물을 수정하지 못하게 하는 검사는 어디에서 해야
   합니까?

## 상위 링크

- [16주 커리큘럼 목차](./README.md)
- [Plan 1 운영 안내](../README.md)
