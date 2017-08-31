# resize-aware

Container element that is aware of, and notifies of, changes to its size.

## Why

Sometimes you may need to take some action when the rendered size of an element changes. This element provides the 
something like the window resize event but for an individual element.

There are many reasons an element's size could change - CSS or class changes, content changes, content of other elements affecting
the flow, viewport changes, etc.  This element detects the size changes without polling or loops.

This custom control uses code from [procurios/ResizeSensor](https://github.com/procurios/ResizeSensor) modified to work with Polymer in both Shadow and Shady DOM.

## demo
<!--
```
<custom-element-demo>
  <template>
     <div style="display: -webkit-flex; display: flex; max-width: 500px; min-height: 80px;">
        
        <next-code-block></next-code-block>
        
        <script>
            window.addEventListener('WebComponentsReady', function (e) {
                document.querySelector('resize-aware').addEventListener('element-resize', function (e) {
                    var li = document.createElement('li');
                    li.innerHTML = 'Changed to ' + e.detail.width + ' x ' + e.detail.height;
                    document.querySelector('#chglist').appendChild(li);
                });
            });

            setTimeout(function () {
                var t = document.querySelector('#tester');
                t.innerHTML =
                '<p>This azure area is resize-aware.</p><p>It fires an event when its size changes. For example, if the content size changes.</p>';
            }, 5000);
            setTimeout(function () {
                var t = document.querySelector('#col2info');
                t.innerHTML =
                '<p>... Or if other elements in the layout change the available space.</p>';
            }, 10000);
            setTimeout(function () {
                var t = document.querySelector('#tester');
                t.innerHTML =
                    '<p>This azure area is resize-aware.</p><p>It fires an event when its size changes. For example, if the content size changes.</p><p>Or, of course, if the viewport changes. (try resizing the window).</p>';
            }, 15000);
            setTimeout(function () {
                var t = document.querySelector('#tester');
                t.innerHTML =
                    '<p>This azure area is resize-aware.</p><p>It fires an event when its size changes. For example, if the content size changes.</p><p>Or, of course, if the viewport changes. (try resizing the window).</p><p>The control is event driven, no polling loops.</p>';
            }, 19000);
            </script>
        </div>
    </template>
</custom-element-demo>
```
-->
```html
<resize-aware>
    <div id="tester" style="background-color: azure; margin: 5px; padding: 5px;">
    <p>
        This azure area is resize-aware.
    </p>
    </div>
</resize-aware>
<div id="col2info" style=" margin: 5px; padding: 5px;"></div>
</div>
<ul id="chglist"></ul>
```

## How to Use
```html
<link rel="import" href="../../bower_components/resize-aware.html" />
```

```html
<resize-aware on-element-size-changed="handleChange">
    <p>
      [[theReview]]
    </p>
    <img src="[[thePic]]">
</resize-aware>
 ```
 or
 ```html
<resize-aware>
  any content that could have been in a div
</resize-aware>
```
```javascript
this.$$('resize-aware').addEventListener('element-resize', this.someHandlerName);
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

## License

MIT license
