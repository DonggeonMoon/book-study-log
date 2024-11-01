# 1장 HTTP 개관

HTTP: 웹 서버, 웹 클라이언트가 웹 컨텐츠를 주고 받기 위해 사용하는 프로토콜

- HTTP는 신뢰성 있는 프로토콜
- 참여자: 웹 서버, 웹 클라이언트
- 교환 대상: 웹 컨텐츠

## 웹 리소스

- MIME 타입: 데이터의 종류. 메일 교환 시 사용되던 타입에서 유래.
    - 주타입(primary object type)과 부타입(specific subtype)으로 구성
    - ex) text/html, application/json
- URI: 웹 서버 리소스의 이름
    - URL: 위치(스킴, 인터넷 주소)와 리소스 이름으로 구성
    - URN: 위치에 독립적인 식별자. 아직 실험 중
    - 통상, URI라 함은 URL을 가리킨다고 보면 됨

## 트랜잭션

- 메서드: `요청`하는 동작, 명령의 종류 ex) GET, POST, PUT, DELETE, HEAD
- 상태 코드: `응답` 시 메시지와 함께 반환하는 코드. 성공 여부, 필요한 추가 조치 등 추가 정보 포함
- 웹 페이지는 하나 이상의 웹 리소스로 구성되며, 이것들을 가져오기 위해 여러 번의 HTTP 트랜잭션이 수행될 수 있음.

## 메시지

- 메시지:  `요청`, `응답`시 웹 클라이언트나 웹 서버가 상대에게 보내는 데이터.
    - 바이너리 형식이 아니라 `텍스트` 형식
    - 시작줄, 헤더, 본문으로 구성
        - 시작줄(start line): 요청이라면 무엇을 해야하는지, 응답이라면 무슨 일이 일어났는지 나타냄 (문자열)
            - 요청 시: 메서드, URI, HTTP 버전
            - 응답 시: HTTP 버전, 상태 코드, 사유구절(reason phrases)
        - 헤더(header): 콜론(:)으로 구성된 여러 개의 헤더 필드로 구성. 빈 줄로 끝남. (문자열)
        - 본문(body): 빈 줄 다음 어떤 종류의 데이터든 들어올 수 있음 (문자열, 바이너리도 가능)

## TCP 커넥션

HTTP는 애플리케이션 계층 프로토콜 -> 네트워크 세부 사항은 신경 안 씀

나머지는 TCP/IP에게 맡김

- 오류 없는 데이터 전송
- 순서에 맞는 전달(데이터는 언제나 보낸 순서대로 도착)
- 조각나지 않는 데이터 스트림(언제든 어떤 크기로든 보낼 수 있음)

HTTP는 TCP 위의 계층. 메시지 데이터 전송을 위해 TCP를 사용한다.

TCP 덕분에 HTTP는 신뢰성 있는 통신이 가능함

TCP/IP 커넥션

- IP 주소와 포트 번호를 통해 TCP/IP 커넥션 맺는 것이 가능
- DNS를 통해 URL을 IP 주소로 변환 가능

웹 브라우저가 원격 서버의 HTML 리소스를 보여주는 과정

1. URL에서 호스트명 추출
2. 서버의 호스트명을 IP 주소로 변환(DNS 이용)
3. URL에서 포트번호 추출
4. TCP 커넥션 맺기
5. 서버에 HTTP 요청
6. 서버가 HTTP 응답
7. 커넥션이 닫히면, 웹브라우저는 문서를 보여줌

텔넷이나 nc로 웹 서버와 직접 통신이 가능하다.

## 프로토콜 버전

- HTTP/1.0
    - HEAD, POST 등 메서드 추가, 멀티 미디어 개체 처리 가능
    - 웹페이지와 상호작용 가능한 폼 실현
- HTTP/1.0+
    - keep-alive 커넥션
    - 가상 호스팅 지원
    - 프록시 연결 지원
- HTTP/1.1
    - HTTP 설계의 구조적 결함 교정
    - 성능 최적화
    - 잘못된 기능 제거
    - 더 복잡해진 웹 애플리케이션 배포 지원
- HTTP/2.0
    - 구글의 SPDY 프로토콜 기반 설계

## 웹의 구성요소

- 프록시: 클라이언트와 서버 사이에 위치한 HTTP 중개자
    - 주로 보안을 위해 사용
    - 요청과 응답을 필터링
- 캐시: 많이 찾는 웹페이지 클라이언트 가까이에 보관하는 HTTP 창고
    - 웹 캐시나 캐시 프록시는 자주 찾는 문서들의 사본을 저장해두는 특별한 HTTP 프락시 서버
    - 멀리 떨어진 서버보다 근처의 캐시에서 더 빨리 문서 받을 수 있음
- 게이트웨이: 다른 애플리케이션과 연결된 특별한 웹 서버
    - 다른 서버들의 `중개자`로 동작하는 특별한 서버
    - HTTP 트래픽을 다른 프로토콜로 변환하기 위해 사용 ex) FTP <-> HTTP
- 터널: 단순히 HTTP 통신을 전달하기만 하는 특별한 프록시
    - 두 커넥션 사이에서 raw 데이터를 열어보지 않고 그대로 전달 ex) HTTP/SSL 터널링
- 에이전트: 자동화된 HTTP 요청을 만들어 주는 준지능적 웹 클라이언트
    - 웹 브라우저 이외에도 여러 가지 종류의 에이전트 존재 ex) 스파이더, 웹로봇