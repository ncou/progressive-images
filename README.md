#  Progressive uploading images to Vanilla Js.

![Effect](https://github.com/dudim/progressive-images/blob/master/assets/images/effect.png)


### css
Add css to project
```css
.progressive-img {
    filter: blur(15px);
    transform: scale(1.05);
    width: 100%;
}

.progressive-img-state-loaded {
    filter: none;
    transform: scale(1);
}
```
or include [/src/progressive-load.css](https://github.com/dudim/progressive-images/blob/master/src/progressive-load.css)
### html
Different images depending on the screen resolution.
```html
<picture class="js-progressive-img">
      <!-- tablet image -->
      <source
          media="(min-width: 600px) and (max-width: 768px)"
          srcset="/assets/images/1-tablet-thumbnail.jpg"
          data-srcset="/assets/images/1-tablet.jpg"
      >
      <!-- phone image -->
      <source
          media="(max-width: 600px)"
          srcset="/assets/images/1-mobile-thumbnail.jpg"
          data-srcset="/assets/images/1-mobile.jpg"
      >
      <!-- desctop image -->
      <img
          src="/assets/images/1-thumbnail.jpg"
          data-srcset="/assets/images/1.jpg"
          class="progressive-img"
      >
  </picture>
```
Images for mobile version and desktop.
```html
<picture class="js-progressive-img">
  <!-- phone image -->
  <source
      media="(max-width: 600px)"
      srcset="/assets/images/2-mobile-thumbnail.jpg"
      data-srcset="/assets/images/2-mobile.jpg"
  >
  <!-- desctop image -->
  <img
      src="/assets/images/2-thumbnail.jpg"
      data-srcset="/assets/images/2.jpg"
      class="progressive-img"
  >
</picture>
```
One image for all resolutions.
```html
<picture class="js-progressive-img">
  <img
      src="/assets/images/3-thumbnail.jpg"
      data-srcset="/assets/images/3.jpg"
      class="progressive-img"
  >
</picture>
```

### js
as a module
```js
import ProgressiveLoad from 'progressive-load';

const progresseiveLoadImages = new ProgressiveLoad({
    pictureTagClassName: 'js-progressive-img',
    pictureLoadedClassName: 'progressive-img-state-loaded',
    mediaQueries: ['(max-width: 600px)', '(min-width: 600px) and (max-width: 768px)'],
    fullImageDataAttribute: 'srcset',
});

//ajax loaded images
progresseiveLoadImages.update()
```
or donwload [/public/global.min.js](https://github.com/dudim/progressive-images/blob/master/public/global.min.js) and included in html
```html
<script src="global.min.js"></script>
<script>
var progresseiveLoadImages = new ProgressiveLoad({
    pictureTagClassName: 'js-progressive-img',
    pictureLoadedClassName: 'progressive-img-state-loaded',
    mediaQueries: ['(max-width: 600px)', '(min-width: 600px) and (max-width: 768px)'],
    fullImageDataAttribute: 'srcset'
});

//ajax loaded images
progresseiveLoadImages.update()
</script>
```