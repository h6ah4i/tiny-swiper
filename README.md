<p align="center">
    <a href="https://github.com/joe223/tiny-swiper" target="_blank"><img width="240" src="https://user-images.githubusercontent.com/10026019/67656978-59e07580-f990-11e9-8baa-63c65b1d5f0a.png"></a>
</p>
<p align="center">📦 2kb gzipped library alternative to SwiperJS with the same modern API.</p>
<p align="center">
    <a href="https://www.npmjs.com/package/tiny-swiper" target="_blank"><img alt="npm" src="https://img.shields.io/npm/v/tiny-swiper"></a>
    <a href="https://www.npmjs.com/package/tiny-swiper" target="_blank"><img src="https://img.shields.io/bundlephobia/minzip/tiny-swiper"></a>
    <a href="https://travis-ci.com/joe223/tiny-swiper" target="_blank"><img src="https://travis-ci.com/joe223/tiny-swiper.svg?branch=master"></a>
    <a href="https://coveralls.io/github/joe223/tiny-swiper?branch=dev" target="_blank"><img src="https://coveralls.io/repos/github/joe223/tiny-swiper/badge.svg?branch=dev"></a>
    <a href="https://www.npmjs.com/package/tiny-swiper" target="_blank"><img alt="NPM" src="https://img.shields.io/npm/l/tiny-swiper"></a>
    <a href="https://www.npmjs.com/package/tiny-swiper" target="_blank"><img alt="GitHub issues" src="https://img.shields.io/github/issues/joe223/tiny-swiper"></a>
</p>

***

> **Tiny-Swiper** is a small yet fully configurable and touch-enabled swiper for creating responsive, mobile-friendly sliders, one-page scrolling webpages, single-page applications, and more.

## Browsers support

| [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/edge/edge_48x48.png" alt="IE / Edge" width="24px" height="24px" />](http://godban.github.io/browsers-support-badges/)<br>IE / Edge | [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/firefox/firefox_48x48.png" alt="Firefox" width="24px" height="24px" />](http://godban.github.io/browsers-support-badges/)<br>Firefox | [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/chrome/chrome_48x48.png" alt="Chrome" width="24px" height="24px" />](http://godban.github.io/browsers-support-badges/)<br>Chrome | [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/safari/safari_48x48.png" alt="Safari" width="24px" height="24px" />](http://godban.github.io/browsers-support-badges/)<br>Safari | [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/safari-ios/safari-ios_48x48.png" alt="iOS Safari" width="24px" height="24px" />](http://godban.github.io/browsers-support-badges/)<br>iOS Safari | [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/samsung-internet/samsung-internet_48x48.png" alt="Samsung" width="24px" height="24px" />](http://godban.github.io/browsers-support-badges/)<br>Samsung | [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/opera/opera_48x48.png" alt="Opera" width="24px" height="24px" />](http://godban.github.io/browsers-support-badges/)<br>Opera |
| --------- | --------- | --------- | --------- | --------- | --------- | --------- |
| IE10, IE11, Edge| last 2 versions| last 2 versions| last 2 versions| last 2 versions| last 2 versions| last 2 versions

## Getting start

- [Getting Started Guide](#guide-to-usage)
- [API](#swiper-parameters)
- [Demos](https://joe223.github.io/tiny-swiper)
- [Changelog](./CHANGELOG.md)
- [Q&A](#qa)

### Guide to usage

Install Swiper via npm or yarn:

```shell
$ npm install tiny-swiper --save
$ yarn add tiny-swiper
```

If you prefer CDN, just make sure constructor `Swiper` is defined in browser global environment.

```html
<script src="https://unpkg.com/tiny-swiper@latest"></script>
```

Html code:

```html
<!-- Slider main container -->
<div class="swiper-container">
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
</div>
```

JavaScript/TypeScript code:

```javascript
const swiper = new Swiper(swiperContainer: HTMLElement | string, parameters?: TinySwiperParameters)
```

- `new Swiper()` - initialize swiper with options.
- `swiperContainer` - HTMLElement or string (with CSS Selector) of swiper container HTML element. Required.
- `parameters` - object with Swiper parameters. Optional.

Looking for exact example and demonstrations? [👉click me](https://joe223.github.io/tiny-swiper)

### Swiper parameters

| Parameter | Type | default | Description |
|---|---|---|---|
| direction | string | 'horizontal' | Could be 'horizontal' or 'vertical' (for vertical slider). |
| speed | number | 300 | Duration of transition between slides (in ms) |
| intermittent | number | 0 | Time to suspend between two swip actions. Only for mousewheel mode. |
| initialSlide | number | 0 | Index number of initial slide. |
| spaceBetween | number | 0 | Distance between slides in px. |
| longSwipesMs | number | 300 | Minimal duration (in ms) to trigger swipe to next/previous slide during long swipes |
| longSwipesRatio | number | 0.5 | 	Ratio to trigger swipe to next/previous slide during long swipes. |
| slidePrevClass | string | 'swiper-slide-prev' | CSS class name of slide which is right before currently active slide |
| slideNextClass | string | 'swiper-slide-next' | CSS class name of slide which is right after currently active slide |
| slideActiveClass | string | 'swiper-slide-active' | CSS class name of currently active slide |
| slideClass | string | 'swiper-slide' | CSS class name of slide |
| wrapperClass | string | 'swiper-wrapper' | CSS class name of slides' wrapper |
| touchRatio | number | 1 | Touch ratio |
| touchAngle | number | 45 | Allowable angle (in degrees) to trigger touch move. Range of values: `[0, 90]`.|
| touchStartPreventDefault | boolean | true | If disabled, `touchstart` (`mousedown`) event won't be prevented |
| touchStartForcePreventDefault | boolean | false | Force to always prevent default for `touchstart` (`mousedown`) event |
| touchMoveStopPropagation | boolean | false | If enabled, then propagation of "touchmove" will be stopped |
| mousewheel | object/boolean | false | Enables navigation through slides using mouse wheel. Object with mousewheel parameters or boolean true to enable with default settings. |
| pagination | object/boolean | false | Object with navigation parameters. |
| passiveListeners | boolean | true | Passive event listeners will be used by default where possible to improve scrolling performance on mobile devices. But if you need to use `e.preventDefault` and you have conflict with it, then you should disable this parameter |
| resistance | boolean | true | Set to false if you want to disable resistant bounds |
| resistanceRatio | number | 0.85 | This option allows you to control resistance ratio |

#### Mousewheel Control Parameters

| Parameter | Type | default | Description |
|---|---|---|---|
| sensitivity | number | 1 | Multiplier of mousewheel data, allows to tweak mouse wheel sensitivity |
| invert | boolean | false | Set to true to invert sliding direction |

#### Pagination Parameters

| Parameter | Type | default | Description |
|---|---|---|---|
| clickable | boolean | false | If true then clicking on pagination button will cause transition to appropriate slide |
| bulletClass | string | 'swiper-pagination-bullet' | CSS class name of single pagination bullet |
| bulletActiveClass | string | 'swiper-pagination-bullet-active' | CSS class name of currently active pagination bullet |

## Q&A

#### 1. Should I use Tiny-Swiper?

Tiny-Swiper keeps the core functions likes Touch/Resistance/Intermittent control, we usually did not use many features on mobile side after all. That the reason why it is smaller and the purpose I wrote it.

If you are looking for some feature special or going to create a complicate slide project. Please check [APIs](#swiper-parameters) before importing to ensure the feature you want is supported. Full-featured SwiperJS should be a better choice sometimes.

## License

Tiny-Swiper is licensed under a [MIT License](./LICENSE).
