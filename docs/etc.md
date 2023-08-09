# Etc

## 무엇을 공부할 것인가?

- 최신 동향 파악
- 채용공고 분석

## 기술면접 대비

- 프로그래머스
- Leetcode
- 면접 스터디
- 실전 면접 경험

## CS

- 네트워크

  - HTTP, HTTPS
  - TCP/IP
  - Web Socket
  - Handshake

## 포스트 구독 서비스

- 요즘IT
- 코드너리
- 커리어리
- 기타 프론트엔드 번역 블로그 구독

## [GoQuality Dev Contents](https://github.com/Integerous/goQuality-dev-contents)

## Atomic Design Pattern 예제

- [github.com/sendbird/quickstart-calls-reactjs](https://github.com/sendbird/quickstart-calls-reactjs)

## Memoization

- [d2.naver.com: Memoization](https://d2.naver.com/helloworld/9223303?ref=codenary)
- [velog.io/@lky5697](https://velog.io/@lky5697/stop-using-usememo-now)
- 불필요한 캐싱을 위한 연산은 오히려 성능 저하
- memoization 이 필요한 경우
  - 비용이 많이 드는 계산
  - 자식 컴포넌트에 함수를 prop 으로 넘길 때
  - 다른 hook(`useEffect` 등) 의 의존성에 사용될 때
- memoization 이 필요하지 않은 경우
  - 간단하고 빠르게 처리되는 계산
  - 매우 자주 렌더링되는 컴포넌트
  - 작고 간단한 컴포넌트

## useEffect 완벽 가이드 요약

- [velog.io/@khy226](https://velog.io/@khy226/useEffect-%EC%99%84%EB%B2%BD-%EA%B0%80%EC%9D%B4%EB%93%9C-%EC%9A%94%EC%95%BD)

## FontSource

- 오픈 소스 웹폰트를 패키지로 설치해 직접 호스팅 할 수 있도록 도와주는 라이브러리
- [fontsouce.org](https://fontsource.org/)
- [github.com/fontsource](https://github.com/fontsource/fontsource)

## AWS 에서 React 배포

- [jasonkang14.github.io: AWS에서 React.js 배포](https://jasonkang14.github.io/aws/aws-amplify-with-react)

## 화면 렌더링 최적화

### css property 확인

- [csstriggers.com](https://csstriggers.com/)  
  css 의 각 property 가 어떤 pipeline 을 trigger 하는지 정리한 사이트

### 최적화 방법

- 효율적인 Layout 을 위해 DOM Element 의 개수는 약 1000개 정도로 제한
- 애니메이션 처리 시 css transform, web animations 를 사용
- GPU Rasterization: meta name 에 viewport 를 작성하면 컨텐츠를 GPU 를 통해 렌더링하여 약 10배의 속도 개선  
  `<meta name="viewport" content="width=device-width, minimum-scale=1.0">`
- Layer 는 30개 정도로 구성하여 Composite 과정에서 과도한 메모리 사용 방지
- JS(DOM + CSSOM) - Layout - Paint - Composite 과정을 하나의 VSync tick 안에서 처리  
  (VSync;수직동기화: 그래픽 카드의 프레임 생성과 모니터의 프레임 출력 동기화)

## `npm dedupe`

- deduplicate
- package-lock.json 의 라이브러리 중복 줄이기

## 네트워크 용어

- Bandwidth(대역폭; 파이프의 내경):  
  특정 시간 내에 송수신할 수 있는 데이터 패킷의 수
  병목 현상과 연관
- Latency(지연 시간; 파이프의 길이):  
  하나의 데이터 패킷이 전송되어 목적지에 도달하는 데 소요되는 시간
- Throughput(처리량; 파이프 안에서 흐르는 물):  
  특정 시간 내에 성공적으로 송수신된 패킷의 실제 수
