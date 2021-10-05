# Snap Slider Performance Tests

Comparing [Snap Slider](https://github.com/tannerhodges/snap-slider#readme) to other popular slider libraries:

- [Flickity](https://flickity.metafizzy.co)
- [Owl Carousel 2](https://owlcarousel2.github.io/OwlCarousel2/)
- [Slick](https://kenwheeler.github.io/slick/)
- [Swiper](https://swiperjs.com)
- [Tiny Slider 2](https://github.com/ganlanyuan/tiny-slider#readme)

## Demos

See all demos in the `docs/` folder:

- [flickity.html](https://tannerhodges.github.io/snap-slider-perf/flickity.html)
- [owl-carousel-2.html](https://tannerhodges.github.io/snap-slider-perf/owl-carousel-2.html)
- [slick.html](https://tannerhodges.github.io/snap-slider-perf/slick.html)
- [snap-slider.html](https://tannerhodges.github.io/snap-slider-perf/snap-slider.html)
- [swiper.html](https://tannerhodges.github.io/snap-slider-perf/swiper.html)
- [tiny-slider-2.html](https://tannerhodges.github.io/snap-slider-perf/tiny-slider-2.html)

## Results

Overall:

1. 🥇 **Snap Slider**: Lowest cost overall. Best for flexible styling.
2. 🥈 **Flickity**: Very close second. Best for rich interactions.
3. 🥉 **Tiny Slider 2**: Good minimal library. Best for legacy browser support.

Breakdown:

| Metric                       | 🥇              | 🥈             | 🥉             | Notes |
| ---------------------------- | -------------- | ------------- | ------------- | ------ |
| **Largest Contentful Paint** | Owl Carousel 2 | Flickity      | Slick         | ⚠️ Libraries that defer CSS calculations have a faster initial paint, but a slower Speed Index. |
| **Speed Index**              | Slick          | Tiny Slider 2 | Snap Slider   | (See above.) |
| **Cumulative Layout Shift**  | -              | -             | -             | No libraries produced significant layout shifts. |
| **Total Blocking Time**      | Snap Slider    | Flickity      | Tiny Slider 2 | Libraries with more DOM manipulation had more blocking time. |
| **Document Complete**        | Snap Slider    | Flickity      | Swiper        | In general, libraries with the least blocking time also finished loading first. (Fully Loaded follows same order.) |
| **Bytes In**                 | Snap Slider    | Tiny Slider 2 | Flickity      | Libraries with the least blocking time also happened to be the lowest file size overall. |

### WebPageTest Runs

Here are the sample WebPageTest runs that each demo's results were taken from. Each demo was tested in Chrome on a Moto G4 with a 3GFast connection in Virginia. Results are based on the median run of 9 total runs per demo.

- Flickity: https://webpagetest.org/result/211005_AiDcX6_c40d791a656bed8393de2597e404c0dc/
- Owl Carousel 2: https://webpagetest.org/result/211005_AiDc8H_d304a765f0baa836a42afd50503f4469/
- Slick: https://webpagetest.org/result/211005_AiDcR8_1f704663b82218d083232544521efb00/
- Snap Slider: https://webpagetest.org/result/211005_AiDc45_c65bca3277cf6443eb84cbd5799adb97/
- Swiper: https://webpagetest.org/result/211005_AiDcBJ_fc80bd25977b30448300c7201cacac7e/
- Tiny Slider 2: https://webpagetest.org/result/211005_AiDc5Q_62b221a807d8d15fdd8d0d8e68047d68/

### Largest Contentful Paint

> **Note**: LCP times are very interesting. Owl Carousel 2, in particular, reports the fastest LCP of the bunch but has the *slowest* Speed Index of them all. In fact, comparing Speed Index to LCP, the results are nearly reversed: the plugins with teh two fastest LCP times also have the slowest Speed Index. Theory: it seems like libraries that do all their CSS style calculations up front take ≈50–100ms longer to render their first paint than those that do a quick initial paint, then re-calculate styles later after they modify the DOM.

1. 0.762s Owl Carousel 2
2. 0.791s Flickity
3. 0.797s Slick
4. 0.814s Tiny Slider 2
5. 0.867s Snap Slider
6. 0.893s Swiper

### Speed Index

1. 0.820s Slick
2. 0.845s Tiny Slider 2
3. 0.900s Snap Slider
4. 0.914s Swiper
5. 0.928s Flickity
6. 2.368s Owl Carousel 2

### Cumulative Layout Shift

All CLS scores were essentially 0.

(The only library to report any shifts was Swiper, but that was only 0.002—almost nothing.)

### Total Blocking Time

1. 0.030s Snap Slider
2. 0.121s Flickity
3. 0.209s Tiny Slider 2
4. 0.300s Swiper
5. 0.569s Owl Carousel 2
6. 0.592s Slick

### Document Complete

1. 1.667s Snap Slider
2. 1.689s Flickity
3. 2.200s Swiper
4. 2.259s Tiny Slider 2
5. 2.342s Owl Carousel 2
6. 2.654s Slick

### Bytes In

> **Note**: These measurements show the total file size of my demos, not just the strict size of each library. Hopefully they show a more realistic idea of how much additional data (beyond the core library) would be included on your own projects.

1. 16 KB Snap Slider
2. 19 KB Tiny Slider 2
3. 21 KB Flickity
4. 47 KB Swiper
5. 50 KB Owl Carousel 2
6. 55 KB Slick
