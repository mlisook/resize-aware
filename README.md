# resize-aware

Container element that is aware of, and notifies of, changes to its size.

## Why

Sometimes your component needs to be aware of changes to the size of its light dom in the <content></content> tags. You may just need to know an element's size as part of a responsive design.

Shadow DOM encapsulation prevents Mutation Observers from detecting and reporting changes in the light DOM to the shadow DOM, so that technique works only with shady DOM.

This custom control uses [procurios/ResizeSensor](https://github.com/procurios/ResizeSensor) modified to work with Polymer in both Shadow and Shady DOM.

## Install

Use Bower to install:

```
bower install --save resize-aware
```

## Include in Your Custom Component
```html
<link rel="import" href="../../bower_components/resize-aware.html" />
```

```html
<resize-aware on-element-size-changed="handleChange">
  <div>
    <p>
      Lorem ipsum.
    </p>
  </div>
</resize-aware>
 ```
 or
 ```html
<resize-aware on-element-size-changed="handleChange">
  <content></content>
</resize-aware>
```

 ## Change Notification

 You can either include a handler in the markup:
```html
<resize-aware on-element-size-changed="someHandlerName">
  stuff to watch
</resize-aware>
 ```
 or listen for the event:
 ```javascript
 this.$$('resize-aware').addEventListener('element-resize', this.someHandlerName);
 ```
