# 9장 웹 로봇

## 크롤러와 크롤링

- 루트 집합에서 시작
- 링크추출과 상대 링크 정상화
- 순환 피하기
- 루프와 중복
- 빵 부스러기의 흔적
- 별칭과 로봇 순환
- URL 정규화하기
- 파일시스템 링크 순환
- 동적 가상 웹 공간
- 루프와 중복 피하기
    - 너비 우선 크롤링
    - 스로틀링
    - URL 크기 제한
    - URL/사이트 블랙리스트
    - 패턴 발견
    - 컨텐츠 지문
    - 사람의 모니터링

## 로봇의 HTTP

- 요청 헤더 식별하기
    - User-Agent
        - From
        - Accept
        - Referer
    - 가상 호스팅
    - 조건부 요청
    - 응답 다루기
        - 상태 코드
        - 엔티티
    - User-Agent 타기팅

## 부적절하게 동작하는 로봇들

- 폭주하는 로봇
- 오래된 URL
- 길고 잘못된 URL
- 호기심이 지나친 로봇

## 로봇 차단하기

- 로봇 차단 표준
- 웹사이트와 robot.txt 파일들
    - robots.txt 가져오기
    - 응답코드
- robots.txt 파일 포맷
    - User-Agent 줄
    - Disallow와 Allow 줄들
    - Disallow/Allow 접두 매칭
- 그외 알아둘 점
- robots.txt의 캐싱과 만료
- HTML 로봇제어 META 태그
    - 로봇 META 지시자
        - NOINDEX
        - NOFOLLOW
        - INDEX
        - FOLLOW
        - NOARCHIVE
        - ALL
        - NONE
    - 검색엔진 META 태그

## 로봇 에티켓

## 검색 엔진

- 넓게 생각하라
- 현대적인 검색엔진의 아키텍처
- 풀 텍스트 색인
- 질의 보내기
- 검색 결과를 정렬하고 보여주기
- 스푸핑
