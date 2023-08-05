# React Test Code

- Jest with RTL, Nock

## Jest 설치(React)

- [jestjs.io](https://jestjs.io/)
- [jestjs.io: Testing React Apps](https://jestjs.io/docs/tutorial-react)
- CRA 를 사용하여 프로젝트를 생성했을 경우 기본적으로 설치되어 있다.

1. Jest 라이브러리를 devDependency 로 추가

```shell
npm install --save-dev jest babel-jest @babel/preset-env @babel/preset-react react-test-renderer
# For TypeScript
npm install --save-dev @babel/preset-typescript
```

2. package.json 에서 test 스크립트 추가

- 또는 빌드 전 테스트 자동화를 위한 CI/CD pipeline 구축

```json
 "scripts": {
    "test": "jest"
  },
```

3. babel.config.js 설정

```js
module.exports = {
  presets: [
    ["@babel/preset-env", { targets: { node: "current" } }],
    "@babel/preset-typescript", // For TypeScript
    ["@babel/preset-react", { runtime: "automatic" }],
  ],
};
```

4. < component-name >.test.js 파일 생성 및 테스트 케이스 작성
5. 테스트 코드 실행

```shell
npm run test
```

## Testing Library(RTL) 설치(React)

### [@testing-library/react](https://github.com/testing-library/react-testing-library)

- [testing-library.com/React Testing Library](https://testing-library.com/docs/react-testing-library/intro/)
- `render`, `fireEvent`, `screen` 등 React 를 테스트 하는 데 필요한 메서드 제공

### [@testing-library/jest-dom](https://github.com/testing-library/jest-dom)

- [testing-library.com/jest-dom](https://testing-library.com/docs/ecosystem-jest-dom)
- `toBeDisabled`, `toBeEmptyDOMElement` 등 DOM node 를 테스트 하기 위한 커스텀 Jest matcher 제공

### [@testing-library/user-event](https://github.com/testing-library/user-event)

- [testing-library.com: User Interactions](https://testing-library.com/docs/user-event/intro/)
- `click`, `upload` 등 user event 시뮬레이션 메서드 제공
- `fireEvent` 대신 구체적인 사용자 상호 작용 설명 가능

```shell
npm install --save-dev @testing-library/react
npm install --save-dev @testing-library/jest-dom
npm install --save-dev @testing-library/user-event
```

2. jest-setup.js 설정

```js
import "@testing-library/jest-dom";
```

3. jest.config.js 설정

```js
setupFilesAfterEnv: ["<rootDir>/jest-setup.js"];
```

4. TypeScript 를 사용할 경우, tsconfig.json 설정

```json
  "include": [
    "./jest-setup.ts"
  ],
```

## Nock 설치

- HTTP Mocking 라이브러리
- [github.com/nock](https://github.com/nock/nock)

```shell
npm install --save-dev nock
```

## API

### `test()` :Jest

- 하나의 특정한 동작을 수행하기 위한 함수
- 테스트 내용을 영어로 작성할 경우 "should..." 로 작성하는 것이 일반적이다.
- `it()` 과 구별: `test()` 와 같은 역할이나 `describe()` 내에서 사용

```js
import { render, screen } from "@testing-library/react";

test("should show login form", () => {
  render(<Login />);
  const input = screen.getByLabelText("Username");
  // Events and assertions...
});
```

### `fireEvent` :RTL

```js
fireEvent[eventName](node: HTMLElement, eventProperties: Object)
```

- DOM event 를 발생시키는 메서드
- `target`: event 를 받는 node 에 할당되는 property 값을 객체(Object)로 지정

```js
const emailInput = screen.getByLabelText(/email/i);
const passwordInput = screen.getByLabelText(/password/i);

fireEvent.change(emailInput, { target: { value: "registered" } });
fireEvent.change(passwordInput, { target: { value: "password" } });
```

### `act()`: RTL

- 컴포넌트 렌더링 및 갱신 코드인 callback 을 실행시켜 가상 DOM에 적용하는 메서드
- 브라우저에서 실행될 때와 최대한 비슷한 환경에서 테스트할 수 있다.
- `render()` 와 `fireEvent` 는 이미 `act()` 로 wrapping 되어 있는 메서드이다.

```js
act(() => {
  ReactDOM.createRoot(container).render(<Counter />);
});
```

### `nock()` :Nock

- HTTP mocking object 를 설정하는 메서드
- 코드의 서순이 중요: 사용자 동작 이벤트(버튼 클릭) 후 API 호출(nock)

```js
nock("https://api.base-url.com")
  .post("/user/login", { username: "registered", password: "password" })
  .reply(200, { token: "AUTH_TOKEN" });
```

### `waitFor()` :RTL

```js
function waitFor<T>(
  callback: () => T | Promise<T>,
  options?: {
    container?: HTMLElement
    timeout?: number
    interval?: number
    onTimeout?: (error: Error) => Error
    mutationObserverOptions?: MutationObserverInit
  },
): Promise<T>
```

- callback 의 expect 가 PASS 되기까지 대기
- `timeout` 시간이 경과할 때까지 callback 을 여러 번 실행할 수 있다. `interval` 옵션으로 호출 횟수를 지정한다.
- option 의 `interval` 기본값은 `50ms`, `timeout` 기본값은 `1000ms` 이다.

```js
await waitFor(async () => {
  expect(history.location.pathname).toBe("/");
});
```

### `expect()` :Jest

- matcher 함수와 함께 사용하여 값을 예측하는 메서드
- `test()` 의 callback 안에 여러 `expect()` 를 호출할 수 있다.

```js
expect(result.current.data).toEqual({ token: "AUTH_TOKEN" });
```
