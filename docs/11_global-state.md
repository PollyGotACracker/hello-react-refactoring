# Global State

## 지역변수 vs 전역변수

- state 를 어떻게 관리할까?
  - 프로그래밍 관점에서 비교
    - Scope
    - Lifespan
    - Namespace Collision: 동일한 범위와 이름을 가진 여러 식별자를 구분할 수 없는 상황
  - `var` vs `let` vs `const`
- 해당 변수를 어디에서 사용하는가?
- 전역변수 설정 기준?

## 전역 상태 관리의 필요성

- [react.dev: Managing state](https://react.dev/learn/managing-state)
- [react.dev: Passing data deeply with context](https://react.dev/learn/passing-data-deeply-with-context)

### React 디자인 패턴

#### Container - Presenter 방식

- Lifting state up
  - 두 컴포넌트에서 state 를 공유하고자 할 때, 부모 컴포넌트에서 state 를 props 로 각각 전달
- Props drilling
  - 컴포넌트 트리가 복잡할 경우, 자손 컴포넌트로 props 전달 시 불필요하게 중간의 컴포넌트를 거쳐야 함

#### Flux && Redux 방식

- Using context in close children
- Using context in distant children
- context 를 사용해 트리 내부의 전체 컴포넌트에 데이터를 바로 제공할 수 있다.

### 어플리케이션 상태 관리

- Global State 를 Client 와 Server 로 각각 분리한다.
- React-Query 는 Server State 를 Client 로부터 분리하여 관리할 수 있도록 한다.

#### Client State

- Client 에서 온전히 제어 가능
- 초기값 설정이나 조작에 제약 사항 없음
- 다른 사람들과 공유되지 않으며, UI/UX 흐름이나 사용자 인터렉션에 따라 변할 수 있음
- Client 내에서 항상 최신 상태로 관리됨

#### Server State

- Client 에서 제어하지 않는 원격의 공간에서 관리되고 유지됨
- 비동기 API 를 통해 Fetching 및 Updating
- 다른 사람들과 공유되므로 사용자가 모르는 사이 변경될 수 있음
- 시간이 지나면 out of date 될 가능성이 있음

## 전역변수를 사용하지 않는 방법?

- [Toss SLASH 23](https://www.youtube.com/watch?v=NwLWX2RNVcw)
  - 페이지 routing 을 하지 않고 컴포넌트로 관리
  - 관련성 있는 코드의 “응집도"를 높이는 방식
- 그러나 개발 팀의 컨벤션을 지키는 것이 가독성에 유리하므로, 항상 이런 방식을 택할 수는 없음
