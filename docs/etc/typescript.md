# Typescript

## type 선언

- 기존의 타입과 key 가 중복되는 새로운 타입을 선언하는 방법: `extends` 키워드, `Pick`
- `enum` 사용은 최소화 한다: Tree-shaking 어려움, 예기치 않은 동작이나 이름의 충돌 발생 가능성
  - 대신 `keyof` 키워드, `Union` 을 사용하는 것이 효율적일 수 있다.

## 컴포넌트 props

```ts
function MyComponent({ foo, bar }) {
  return (
    <div>
      {foo}
      {bar}
    </div>
  );
}

MyComponent.propTypes = {
  foo: PropTypes.string.isRequired,
  bar: PropTypes.string,
};

MyComponent.defaultProps = {
  bar: "some default",
};
```

```ts
type Props = {
  foo: string;
  bar?: string;
};

function MyComponent(props: Props) {
  return (
    <div>
      Hello {props.foo} {props.bar}
    </div>
  );
}

MyComponent.defaultProps = {
  bar: "some default",
};
```

- Optional prop(`?:`)은 `defaultProps` 를 넣어주는 것이 좋다.
  - [github.com/jsx-eslint: eslint-plugin-react](https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/require-default-props.md)
