# Optimization 2

- 크기가 큰 이미지는 클라우드에 업로드 후 링크를 가져오는 방식을 고려

## Font 최적화

- 가장 용량이 작은 WOFF2 선택
  - [transfonter](https://transfonter.org/) 에서 폰트 포맷 변경
- CSS font-face 는 캐시 컨트롤이 불가능하므로 가급적 지양할 것
  - Serve static assets an efficient cache policy

### FontSource

- 오픈 소스 웹폰트를 패키지로 설치해 직접 호스팅 할 수 있도록 도와주는 라이브러리
- [fontsouce.org](https://fontsource.org/)
- [github.com/fontsource](https://github.com/fontsource/fontsource)

## CSS 최적화

- CSS 프레임워크 사용 시 문제 발생
  - Reduce unused CSS

1. 개발자도구에서 우상단 케밥 메뉴 아이콘 클릭
2. More tools(도구 더보기) => Coverage(범위) 선택
3. 새로고침 버튼 클릭 후 Unused Bytes(사용하지 않은 바이트) 를 확인

### PurgeCSS

- [purgecss.com](https://purgecss.com)
- [purgecss.com/CLI](https://purgecss.com/CLI.html)
- 안 쓰이는 CSS 코드를 build 과정에서 제거하여 css 파일 최적화

```json
"scripts": {
  "postbuild": "purgecss --css build/static/css/*.css --content build/index.html build/static/js/*.js --output build/static/css"
},
```
