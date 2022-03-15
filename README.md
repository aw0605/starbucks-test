## Favicon(파비콘, favorites icon) 
웹페이지를 나타내는 아이콘, 웹페이지의 로고를 설정합니다.  
대부분의 경우 루트 경로에 `favicon.ico` 파일을 위치하면 자동으로  
로딩하기 때문에 `<link />` 를 작성할 필요가 없습니다.  
`favicon.png` 파일을 사용하려면 다음과 같이 `<link />`를 작성하세요.
```html
<link rel="shortcut icon" href="favicon.ico" /> 
<link rel="icon" href="./favicon.png" />
```
favicon.ico 64 x 64 (px) 또는 32 x 32 또는 16 x 16  
favicon.png 500 x 500 (px)

## Reset.css
> 각 브라우저의 기본 스타일을 초기화합니다.  
[jsdelivr이동](https://www.jsdelivr.com/package/npm/the-new-css-reset)
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reset-css@5.0.1/reset.min.css" />
```
## 오픈 그래프(The Open Graph protocol)
웹페이지가 소셜 미디어(페이스북 등)로 공유될 때 우선적으로 활용되는 정보를 지정합니다.  
[더 많은 오픈그래프 속성 보기](https://ogp.me/)
```html
og:type: 페이지의 유형(E.g, website, video.movie)
og:site_name: 속한 사이트의 이름
og:title: 페이지의 이름(제목)
og:description: 페이지의 간단한 설명
og:image: 페이지의 대표 이미지 주소(URL)
og:url: 페이지 주소(URL)
```
## 트위터 카드(Twitter Cards)
웹페이지가 소셜 미디어(트위터)로 공유될 때 우선적으로 활용되는 정보를 지정합니다.  
[더 많은 트위터 카드 보기](https://developer.twitter.com/en/docs/twitter-for-websites/cards/guides/getting-started)
```html
twitter:card: 페이지(카드)의 유형(E.g. summary, player)
twitter:site: 속한 사이트의 이름
twitter:title: 페이지의 이름(제목)
twitter:description: 페이지의 간단한 설명
twitter:image: 페이지의 대표 이미지 주소(URL)
twitter:url: 페이지 주소(URL)
```
## SEO (검색 엔진 최적화, Search Engine Optimization)
구글이나 네이버 등에 자신의 웹 사이트/페이지를 노출 할 수 있도록 정보를 최적화하는 작업을 말한다.
```html
<meta property="og:image" content="./images/starbucks_seo.jpg" />
<meta property="twitter:image" content="./images/starbucks_seo.jpg" />
```


## Youtube API
IFrame Player API를 통해 YouTube 동영상을 제어할 수 있습니다.  

유튜브 영상이 출력될 위치에 요소를 지정(생성)합니다.
```html
<!-- in HEAD -->
<script defer src="./js/youtube.js"></script>

<!-- in BODY -->
<div id="player"></div>
```
onYouTubePlayerAPIReady 함수 이름은 Youtube IFrame Player API에서 사용하는 이름이기 때문에 다르게 지정하면 동작하지 않습니다!  
그리고 함수는 전역(Global) 등록해야 합니다!

플레이어 매개변수(playerVars)에서 더 많은 옵션을 확인할 수 있습니다.
```javascript
// Youtube IFrame API를 비동기로 로드합니다.
var tag = document.createElement('script');
tag.src = "https://www.youtube.com/iframe_api";
var firstScriptTag = document.getElementsByTagName('script')[0];
firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

function onYouTubePlayerAPIReady() {
  // <div id="player"></div>
  new YT.Player('player', {
    videoId: 'An6LvWQuj_8', // 재생할 유튜브 영상 ID
    playerVars: {
      autoplay: true, // 자동 재생 유무
      loop: true, // 반복 재생 유무
      playlist: 'An6LvWQuj_8' // 반복 재생할 유튜브 영상 ID 목록
    },
    events: {
      // 영상이 준비되었을 때,
      onReady: function (event) {
        event.target.mute(); // 음소거!
      }
    }
  });
}
```
## 랜덤한 숫자를 생성하는 함수
```javascript
// 범위 랜덤 함수(소수점 2자리까지)
function random(min, max) {
  // `.toFixed()`를 통해 반환된 문자 데이터를,
  // `parseFloat()`을 통해 소수점을 가지는 숫자 데이터로 변환
  return parseFloat((Math.random() * (max - min) + min).toFixed(2))
}
```
## Swiper slide
> css
``` html
<link rel="stylesheet" href="https://unpkg.com/swiper@8/swiper-bundle.min.css"/>
```
> html
``` html
<!-- Slider main container -->
<div class="swiper">
  <!-- Additional required wrapper -->
  <div class="swiper-wrapper">
    <!-- Slides -->
    <div class="swiper-slide">Slide 1</div>
    <div class="swiper-slide">Slide 2</div>
    <div class="swiper-slide">Slide 3</div>
    ...
  </div>
  <!-- If we need pagination -->
  <div class="swiper-pagination"></div>

  <!-- If we need navigation buttons -->
  <div class="swiper-button-prev"></div>
  <div class="swiper-button-next"></div>

  <!-- If we need scrollbar -->
  <div class="swiper-scrollbar"></div>
</div>
```
```javascript
new Swiper('.변경 .swiper', {
    direction : 'horizontal', //방향
    loop : true, //무한반복
    autoplay : true, //자동시작
    slidesPerView : 5, //한번에 보여지는 슬라이드 개수
    spaceBetween : 30, //슬라이드간 간격
    navigation : {
        prevEl : ".변경 .swiper-prev",
        nextEl : ".변경 .swiper-next"
    },
});
```
