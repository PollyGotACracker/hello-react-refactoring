# Performance Testing

## Web Vitals

- [web.dev: Web Vitals](https://web.dev/vitals/)
- Web Vitals is an initiative by Google to provide unified guidance for quality signals that are essential to delivering a great user experience on the web.
- 사용자 경험 지표
- Google 검색 순위 결정 요소

### Core Web Vitals

#### Largest Contentful Paint(LCP)

- 페이지가 로드되기 시작한 시점을 기준으로 주요 콘텐츠의 렌더링 완료 시간 측정
- 주요 콘텐츠란 viewport 내의 가장 큰 텍스트나 이미지
- 여백이 언제 없어지는가?

#### First Input Delay(FID)

- 사용자가 페이지와 처음 상호작용할 때, 이벤트 핸들러 처리를 시작하기까지의 시간 측정
- 링크나 버튼 클릭, 사용자 지정 JavaScript 기반 컨트롤 사용 등

#### Cumulative Layout Shift(CLS)

- 예기치 않은 레이아웃 이동 측정 ([링크](https://web.dev/cls))
- 크기를 지정하지 않은 이미지나 동영상, 대체 크기보다 크거나 작게 렌더링되는 글꼴, 타사 광고 또는 위젯 등

### 기타 Web Vitals

#### First Contentful Paint(FCP)

- 페이지가 로드되기 시작한 시점부터 페이지 콘텐츠 *일부*가 화면에 최초로 렌더링될 때까지의 시간 측정

#### Total Blocking Time(TBT)

- 메인 스레드가 입력 응답을 막을 만큼 오래 차단(50ms 이상)되었을 경우, FCP(First Contentful Paint) 와 TTI(Time to Interactive) 사이의 총 시간 측정
  - Time to Interactive(TTI):  
    페이지가 로드되기 시작한 시점부터 주요 하위 리소스가 로드되고 사용자 입력에 신속하고 안정적으로 응답할 수 있는 시점까지의 시간 측정

#### Speed Index

- 페이지를 로드하는 동안 콘텐츠가 표시되는 속도를 측정

## Web Performance Testing Tools

### Lighthouse

- Chrome 개발자도구 / Chrome extension 설치 / PageSpeed Insights 사이트([링크](https://pagespeed.web.dev/))
- production build 에서 확인  
  (빌드 시 최적화되어 web vital 이 개선된다: Tree Shaking, Minification)

- 주요 기능
  - Performance: 성능
  - Accessibility: 접근성
  - Best Practice: 보안 관련  
    (HTTP->HTTPS 리다이렉션 관련 오류 있음)
  - SEO: 검색 최적화
  - PWA: PWA 기준 평가

### Performance

- Chrome 개발자도구 탭
- record 또는 reload 버튼을 클릭하여 분석 시작, 새로고침 후 리로딩이 끝나면 stop 버튼을 클릭
- 페이지 렌더링 과정을 스냅샷으로 제공
- Network / Frame / Timings / Main 섹션 등
- Runtime 성능 측정
  - 렌더링 성능
  - 자바스크립트 성능
  - 메모리 관리
  - 반응성(First Input Delay)
  - 네트워크 성능
- 주요 기능
  - Loading
  - Scripting
  - Rendering
  - Painting
- Memory
  - JS Heap
  - Documents
  - Nodes
  - Listeners
  - GPU Memory

### Profiler

- [react.dev: Profiler](https://react.dev/reference/react/Profiler)
- React devtools + React 내장 API
- development 환경에서 확인
- 컴포넌트별 렌더링 시간 측정 가능
- 특정 컴포넌트에서 병목이 발생할 때 참고

---

## PWA;Progressive Web App

- 모바일 기기에서 네이티브 앱과 같은 사용자 경험 제공
- 캐시된 데이터를 사용하여 오프라인에서도 동작 가능
- Push 알림, 카메라, 마이크 등 기능 사용

## Tree Shaking

- 빌드 시 실제 사용되지 않는 코드를 제거하여 최적화하는 기술
