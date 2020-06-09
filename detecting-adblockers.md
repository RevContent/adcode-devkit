# Detecting Adblockers

Sometimes, our publishers will need the ability to detect if an ad blocker is running so that they can show an alternate, ad block safe widget. To do this, a standard ad code will not suffice and as such you will need to rely on a different strategy to show widgets on your site.


### Adblocker Detection

Prior to adding any ad code to a page, a check must be performed to see if ads are blocked. To do this, we can create a function that attempts to insert a DOM element with a blacklisted id as follows:

```javascript
function testAdblocker(func) {
  var element = document.createElement('div');
  
  element.id = 'sponsorText';
  element.appendChild(document.createTextNode('&nbsp;'));
  element.style.left = '-999px';
  element.style.position = 'absolute';
  
  document.body.appendChild(element);
  
  setTimeout(function() {
    if (element) {
      var isBlocked = element.clientHeight === 0;
      func(isBlocked);
    }
  }, 100);
}
```

### Calling Adblocker Detection 
As mentioned above, this function attempts to create a pseudo ad by placing a div into the DOM that uses a blacklisted id. From there, it creates a 100 millisecond timeout and then checks the client height of the element to see if it were rendered successfully or not. If the client height is 0, then we can tell that it was blocked from being shown. That value is then consumed by a callback. To use this function, we can use logic like the following:

```javascript
testAdblocker(function(isBlocked) {
  var id = isBlocked ? BLOCKED_WIDGETID : WIDGETID;
  
  // Logic to get a pre-existing DOM element
  var target = document.getElementById('my-widget-placement');
  
  // Does the target exist?
  if (target) {
    target.setAttribute('data-rc-widget', '');
    target.setAttribute('data-endpoint', 'trends.revcontent.com');
    target.setAttribute('data-widget-id', id);
  }
  
  // Is the js file loaded in the DOM already? If not, add it as a
  // script element. If so, call renderRCWidget
  if (typeof renderRCWidget !== 'function') {
    var script = document.createElement('script');
    script.src = 'https://assets.revcontent.com/master/delivery.js';
    script.defer = true;
    target.appendChild(script);
  }
  else {
    renderRCWidget(target);
  }
});
```

When executing these, you can opt to execute these immediately via an [immediately invoked function expression](https://developer.mozilla.org/en-US/docs/Glossary/IIFE) (IIFE) as follows:

```html
<script>
  (function() {
    function testAdblocker(function) {
      var element = document.createElement('div');
      
      element.id = 'sponsorText';
      element.appendChild(document.createTextNode('&nbsp;');
      element.style.left = '-999px';
      element.style.position = 'absolute';
      
      document.body.appendChild(element);
      
      setTimeout(function() {
        if (element) {
          var isBlocked = element.clientHeight === 0;
          function(isBlocked);
        }
      }, 100);
    }
    
    testAdblocker(function(isBlocked) {
      var id = isBlocked ? BLOCKED_WIDGETID : WIDGETID;
      
      // Logic to get a pre-existing DOM element
      var target = document.getElementById('my-widget-placement');
      
      // Does the target exist?
      if (target) {
        target.setAttribute('data-rc-widget', '');
        target.setAttribute('data-endpoint', 'trends.revcontent.com');
        target.setAttribute('data-widget-id', id);
      }
      
      // Is the js file loaded in the DOM already? If not, add it as a
      // script element. If so, call renderRCWidget
      if (typeof renderRCWidget !== 'function') {
        var script = document.createElement('script');
        script.src = 'https://assets.revcontent.com/master/delivery.js';
        script.defer = true;
        target.appendChild(script);
      }
      else {
        renderRCWidget(target);
      }
    });
    
  })();
</script>
```

If your widget ids are valid, you should be able to test this by loading your page with an ad blocker and without an ad blocker.
