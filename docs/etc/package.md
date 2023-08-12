# Package

## package manager

- 패키지 매니저는 하나만 사용해야 한다.
  - 패키지 매니저 선택 시 고려사항 ([링크](https://yceffort.kr/2022/05/npm-vs-yarn-vs-pnpm))

## devDependency

- '@testing/', '@types/' 는 devDependencies 로 설치한다.

## package-lock.json

- `package.json` vs `package-lock.json` 또는 `yarn.lock`
- dependency 를 정확하게 관리해야 여러 개발자들이 같은 환경에서 개발할 수 있다.
  - package-lock.json 은 팀원들과 같은 dependency 버전을 공유하기 위한 파일이다.
  - dependency가 업데이트 되었을 경우 `npm install`(package) 이 아닌, `npm ci`(package-lock) 를 한다.
  - 버전 관리에 문제가 생겼을 경우 package-lock.json 을 직접 수정하지 말고, 파일을 지운 뒤 `npm install` 을 실행해 새로 생성한다.
  - node 버전이 다르면 package-lock.json 파일이 달라질 수 있으므로 팀원 간 node 버전을 통일하는 것이 좋다.
  - `npm dedupe` 명령어를 사용해 package-lock.json 에서 중복된 dependency 를 삭제한다.
