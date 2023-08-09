# Optimization

## Code Splitting

- Bundle size를 줄이는 방법
  - 전체 크기를 줄이는 것이 아닌 하나의 번들을 여러 개의 chunk 로 잘게 쪼개는 것
  - `React.lazy` 와 `Suspense` 사용
    - [web.dev: Code splitting with React.lazy and Suspense](https://web.dev/code-splitting-suspense/)
    - [react.dev: React.lazy](https://react.dev/reference/react/lazy)
    - [react.dev: Suspense](https://react.dev/reference/react/Suspense)
- 최초 로딩시간이 단축되는 이점이 있음
  - FCP, LCP, FID 개선 가능
  - [jasonkang14.github.io: 리액트 빌드 최적화](https://jasonkang14.github.io/react/optimzation-with-chat-gpt)
- 브라우저 caching
  - 각 chunk 파일의 id 를 사용

## Lazy Loading

- Lighthouse 측정 점수가 좋다고 해서 최적화가 끝난 것이 아니다.
- `IntersectionObserver` API 사용
- [jasonkang14.github.io: Lazy Loading](https://jasonkang14.github.io/react/lazy-loading-to-improve-web-vitals)
