---
id: api 
title: APIs
---


- [Config parameters](#swiper-parameters)
- [Instance methods](#methods)
- [Life hooks](#life-hooks)
- [Using Plugins](#using-plugins)
- [Plugin List](#plugin-list)

## Swiper parameters

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
| passiveListeners | boolean | true | Passive event listeners will be used by default where possible to improve scrolling performance on mobile devices. But if you need to use `e.preventDefault` and you have conflict with it, then you should disable this parameter |
| resistance | boolean | true | Set to false if you want to disable resistant bounds |
| resistanceRatio | number | 0.85 | This option allows you to control resistance ratio |
| plugins | TinySwiperPlugins[] | undefined | Plugins for Tiny-Swiper instance. |
| excludeElements | HTMLElements[] | `[]` | An HTMLElement array which contains all elements that do not trigger swipe. |
| slidesPerView | number | 1 | Number of slides per view (slides visible at the same time on slider's container). |
| centeredSlides | boolean | false | If true, then active slide will be centered, not always on the left side. |

### Mousewheel Control Parameters

| Parameter | Type | default | Description |
|---|---|---|---|
| sensitivity | number | 1 | Multiplier of mousewheel data, allows to tweak mouse wheel sensitivity |
| invert | boolean | false | Set to true to invert sliding direction |


## Methods

| Method | Description |
|---|---|
| update | Update instance status if you changed DOM manually. |
| scroll(index: number, force?: boolean) | Slide to specific index. scroll will not work when instance's `scrolling` is `true` and `force` is `false`. |
| destroy | Destroy slider instance, detach all events listeners and reset style. |
| on(eventName: string, cb: function) | Register life hooks callback function. |
| off(eventName: string, cb: function) | Cancel life hooks callback function. |
| use(TinySwiperPlugin[]) | Register plugins globally. |

## Life Hooks

You can do something at special moments by registering Tiny-Swiper instance life hooks. Such as create a plugin.

| HookName | Parameters | Description |
|---|---|---|
| `before-init` | `instance: TinySwiper` | Before Tiny-Swiper instance initialize. |
| `after-init` |  `instance: TinySwiper` | After Tiny-Swiper instance initialize. |
| `before-slide` | `currentIndex: number, instance: TinySwiper, newIndex: number` | Before Tiny-Swiper instance slide changes. `index` does not change yet. |
| `after-slide` | `newIndex: number, instance: TinySwiper` | After Tiny-Swiper instance slide changes.  |
| `before-destroy` | `instance: TinySwiper` | Before Tiny-Swiper instance is destroyed. |
| `after-destroy` | `instance: TinySwiper` | After Tiny-Swiper instance is destroyed, every thing is restored. |

## Using Plugins

Tiny-Swiper instance only reserve core functions such as `init` `destroy` `LifeHooks`. So, You should load specific plugin if you need something special likes pagination.

Plugin is under `lib/modules` folder. You could import theme as ES modules:

```javascript
import { SwiperPluginPagination } from 'tiny-swiper' // Since v1.2.0

// or

import SwiperPluginPagination from 'tiny-swiper/lib/modules/pagination.min.js'
```

Or via CDN:

```html
<script src="https://unpkg.com/tiny-swiper@latest/lib/modules/pagination.min.js"></script>
```

And the most important —— initialization:

1. Register `SwiperPluginPagination` as default plugin, so every Swiper instance will be supported.

    ```javascript
    // All intances instantiated with Swiper has pagination plugin
    Swiper.use([ SwiperPluginPagination ])

    const swiper = new Swiper(
        swiperContainerElement,
        {
            // SwiperPluginPagination configuration,
            // just make sure that pagination is not equal to false.
            pagination: {
                clickable: true
            }
        }
    )
    ```

2.  Or just for current instance via the `plugin` parameter

    ```javascript
    const swiper = new Swiper(
        swiperContainerElement,
        {
            // SwiperPluginPagination configuration.
            pagination: {
                clickable: true
            },

            // Add SwiperPluginPagination plugin.
            plugins: [ SwiperPluginPagination ]
        }
    )
    ```

:::caution
Notice: Two configurations are mutually exclusive. Plugin parameter gets higher priority.
:::

Do not forget, just keep Plugin parameter at the **first level** of configuration.
