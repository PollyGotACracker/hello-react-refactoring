# Rendering Optimization

## css property 확인

- [csstriggers.com](https://csstriggers.com/)  
  css 의 각 property 가 어떤 pipeline 을 trigger 하는지 정리한 사이트

## 최적화 방법

- 효율적인 Layout 을 위해 DOM Element 의 개수는 약 1000개 정도로 제한
- 애니메이션 처리 시 css transform, web animations 를 사용
- GPU Rasterization: meta name 에 viewport 를 작성하면 컨텐츠를 GPU 를 통해 렌더링하여 약 10배의 속도 개선  
  `<meta name="viewport" content="width=device-width, minimum-scale=1.0">`
- Layer 는 30개 정도로 구성하여 Composite 과정에서 과도한 메모리 사용 방지
- JS(DOM + CSSOM) - Layout - Paint - Composite 과정을 하나의 VSync tick 안에서 처리  
  (VSync;수직동기화: 그래픽 카드의 프레임 생성과 모니터의 프레임 출력 동기화)
