# Using Subids

Sometimes, publishers find that they need to be able to gather additional information about where a widget loaded on their site (categories, metadata, etc.). This data could contain information such as the category in which news is posted or getting url parameters. To accomplish this, Revcontent provides the ability to send key value pairs called subids.

**Note**: For more information on key value pairs and how they're used in subids, [see here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/entries).


 ### Parameters
Subids only require one additional parameter to be added to your ad code.
 
 #### data-sub-ids
 > Consumes a JSON object. Passes data to the widget for use in stats tracking.

### Usage
Subids can be set inline by following the pattern shown below:

```html
<div id="rcjs_load_x9cns"
     data-rc-widget
     data-endpoint="trends.revcontent.com"
     data-widget-id="XXXXX"
     data-sub-ids='{"key":"value"}'></div>
```

_Note the use of single quotes for the subids data attribute. Single quotes allow for the use of valid JSON here. For more information on attribute syntax, [see here](https://html.spec.whatwg.org/#attributes-2)_


Subids can also be set programmatically (recommended):

```javascript
// Example variable of getting document referrer
var referrer = document.referrer;

var subids = {
  key: 'value',
  referring_url: referrer 
}

var el = document.getElementById('my-widget-div');
if (el) {
  el.setAttribute('data-sub-ids', JSON.stringify(subids));
}
```
**Note**: It is important that when using this method, you convert your sub ids object into JSON prior to setting itor during setting it (as shown above) on the widget div. Failing to do this will pass your ids as an object rather than a JSON string. Failing to convert this to JSON will result in your sub ids not being tracked correctly.
