# 깃허브 액션 실습

> 깃허브 액션을 이용해 CI/CD를 적용해본다.


## 🎲 CI 요구사항

> 자동 빌드, 테스트를 적용한다.

- default workflow를 사용한다.
- 개인 브랜치에 pull request 트리거를 걸어야 한다.
  - ex) rinsabbit은 rinsabbit 브랜치에 PR을 올릴 때 워크플로우가 실행된다.
- 총 4단계의 스텝을 진행한다.
  1. 한 줄 이상의 커스텀 스크립트 출력
  2. gradlew에 접근 권한 부여 `chmod +x gradlew` 명령어 사용
  3. 테스트 없는 빌드
  4. 테스트용 application.yml을 이용한 테스트

## 🛹 CD 요구사항

> 자동 배포를 적용한다.

- default workflow + deploy with heroku 플러그인을 사용한다.
- 개인 브랜치에 push 트리거를 걸어야 한다.
- 깃허브에 시크릿키를 등록하여 사용한다. 등록할 요소는 다음과 같다.
  - heroku 개인 API 키
  - heroku 이메일
  - heroku 앱 이름
- 배포용 application.yml을 작성한다. `application-prod.yml`
  - 배포될 때 배포용 yml이 쓰이도록 workflow를 작성한다.
- [헤로쿠 배포 문서](https://www.notion.so/jukco/heroku-e2bd0c2b93ad446e82eab8927c09aaf1)를 참고하여 workflow를 작성한다.
- 배포가 완료되면 터미널로 배포 서버에 진입하여 로그를 확인한다.
  - `heroku logs -a [app-name]` 으로 확인할 수 있다.
  - api가 제대로 작동하는지 터미널 로그를 통해 확인해본다.
- 참고 링크 [클릭](https://malwareanalysis.tistory.com/131)

## 🎰 CD 요구사항 (옵션)

> 도메인을 등록한다. (헤로쿠에 카드 등록해야 사용 가능)

- [무료 도메인 구입처](https://xn--220b31d95hq8o.xn--3e0b707e/)에서 도메인을 등록한다.
- 헤로쿠에 도메인을 등록하고 DNS 주소를 받는다.
- 구입처에서 등록한 도메인의 별칭 란에 DNS 주소를 추가한다.
- 헤로쿠 앱 링크가 아닌 도메인으로 접근해본다.