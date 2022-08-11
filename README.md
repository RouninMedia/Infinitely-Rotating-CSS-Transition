# Infinitely Rotating CSS Transition
Infinitely Rotating CSS Transition - this requires a small amount of javascript but it demonstrates how to get a CSS Transition to act like a CSS Animation with an `animation-iteration-count` value of `infinite`.

## HTML
```html
<div class="loadingSpinner"></div>
```

## CSS
```css
:root {
  --rotation: rotate(0deg);
}

.loadingSpinner {
  width: 50px;
  height: 50px;
  border: 5px solid #3498db;
  border-top-color: rgba(0, 0, 0, 0);
  border-left-color: rgba(0, 0, 0, 0);
  border-radius: 50%;
  transform: var(--rotation);
  transition: transform 0.7s linear;
}
```

## JS
```js
const loadingSpinner = document.querySelector('.loadingSpinner');

const rotateSpinner = () => {

  let loadingSpinnerStyles = window.getComputedStyle(loadingSpinner);
  let rotation = loadingSpinnerStyles.getPropertyValue('--rotation');
  rotation = parseInt(rotation.replace('rotate(', '').replace('deg)', '')) + 360;
  rotation = 'rotate(' + rotation + 'deg)';
  loadingSpinner.style.setProperty('--rotation', rotation);
}

loadingSpinner.addEventListener('transitionend', rotateSpinner);
window.addEventListener('load', rotateSpinner);
```
