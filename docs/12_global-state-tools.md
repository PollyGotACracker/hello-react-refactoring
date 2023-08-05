# Global State Tools

## Context API

- 특징
  - state 를 Provide 하는 방식
  - React 내장 기능이므로 별도 라이브러리 설치가 필요하지 않음
  - HTTP Request 도 context 에서 모두 관리
    - 해당 관심사와 관련된 모든 것을 context 가 처리
- 단점
  - 비즈니스 로직이 복잡해지는 경우, 관심사의 수만큼 Provider 생성 필요
  - 단 하나의 Provider 에도 설정할 것들이 많음
  - 떨어지는 렌더링 효율: 특정 데이터 업데이트 시 context 내 모든 데이터를 업데이트

## Redux

- 특징
  - Flux 패턴을 적용함
  - Store 하나에서 변수를 관리하기 때문에 여러 Provider 를 선언하지 않아도 됨
  - Thunk, Saga 등의 Middleware 를 통한 비동기 처리
- 단점
  - 설정할 것이 많음
  - Context API 와 크게 다르지 않음
  - 요즘 새로운 프로젝트에서 잘 안 쓰는 편
    - Recoil: 클라이언트 상태 관리
    - React-query: 서버 상태 관리
    - 그리고 zustand, jotai, mobX...

## Recoil

- React와 유사한 syntax
- 내가 필요한 값만 subscribe
- atoms 와 selectors
  - atom 은 state 와 유사한 개념
  - selector 는 atom 을 Manipulate 하는 경우 사용
- 장점
  - 구조가 간단해서 적용하기 쉬움
  - Context API의 rendering 비효율을 개선함
    - Concurrent mode 지원
- 단점
  - atom 의 수가 매우 많아질 가능성이 있음

### Recoil API

- selector:  
  atom 을 직접 변경하지 않고, atom 값을 가져와서 새로운 값을 리턴하는 역할(복사본 사용)
- useSetRecoilState:  
  atom 을 직접 변경
- atomFamily:  
  전달받은 파라미터에 기반한 다른 상태의 atom 을 반환하는 함수

## React Query

- Server State 관리: 서버에서 불러온 값(상태)들을 클라이언트가 관리하지 않도록 함
- 비즈니스 로직들을 대부분 백엔드에서 관리
  - 많은 변수들이 서버에서 불러온 값을 관리하기 위해 사용

### React Query 최적화

#### Cache 된 데이터의 상태

- Fresh
- Stale
- Inactive

#### staleTime, cacheTime

- `staleTime`:
  - 데이터가 fresh 에서 stale 상태로 변경되는 데 걸리는 시간
  - 지정된 시간 동안 캐싱된 값을 사용한다.
  - 시간이 지나면 서버로부터 데이터가 새롭게 갱신된다.
  - `staleTime` 을 `infinity` 로 설정하면 stale 상태가 되지 않는다.
  - default 0
- `cacheTime`:
  - 캐시된 데이터가 inactive 상태가 됐을 때 데이터를 유지하는 시간
  - 시간이 지나면 데이터를 제거한다(Garbage Collecting).
  - default 5분

#### stale 한 쿼리가 백그라운드에서 refetch 되는 상황

- 쿼리에 새 인스턴스가 mount 되었을 때
- 브라우저 창이 다시 focus 되었을 때
- 네트워크가 끊겼다가 재연결 되었을 때
- 쿼리에 refetch interval 을 설정했을 때

### Optimistic Update(낙관적 업데이트)

- 서버 업데이트 시 UI도 업데이트 될 것을 낙관적으로 가정하여 미리 업데이트
- 서버 업데이트(Mutation)를 하기 전 미리 화면의 UI를 업데이트 후, 서버 응답에 따라 UI 업데이트의 확정 또는 롤백 결정
- [tanstack.com: Optimistic updates](https://tanstack.com/query/v5/docs/react/guides/optimistic-updates)
- [youtube.com/Codevolution](https://www.youtube.com/watch?v=rnN5ng6aoAc&ab_channel=Codevolution)
- [uncertainty.oopy.io](https://uncertainty.oopy.io/optimistic-ui-with-react-query)
