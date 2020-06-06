# Manually Rendering a Widget

Sometimes you may need to render a widget after the javascript bundle for Revcontents widgets has loaded. For these use cases, we provide a function attached to the window object that allows you to render a widget called `renderRCWidget`.

### Parameters

#### Target
> Consumes an [Element](https://developer.mozilla.org/en-US/docs/Web/API/Element) that is used to render the markup for the widget.


### Example Usage

When using `renderRCWidget`, there's a couple of options available to you in regards to the element you need to pass to it. Since Element is simply a DOM element, you have the option of searching for one on the page already via one of the following options:

* [getElementById](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById)
* [getElementsByClassName](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByClassName)
* [getElementsByTagName](https://developer.mozilla.org/en-US/docs/Web/API/Element/getElementsByTagName)
* [querySelector](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector)
* [querySelectorAll](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll)

**Note**: Your situation may vary and because of this, it's important to understand how each of these selectors work prior to using them. In most cases, `querySelector` or `getElementById` will be the preferred method of getting a DOM element.

Using one of these methods, you can render a widget by using the following pattern:


    var el = document.getElementById('my_element_id');
    if (el) {
      el.setAttribute('data-rc-widget', '');
      el.setAttribute('data-endpoint', 'trends.revcontent.com');
      el.setAttribute('data-widget-id', 'MY_WIDGET_ID');
      
      if (typeof renderRCWidget === 'function') {
        renderRCWidget(el);
      }
    }

In this example, we start by looking for a DOM element that matches `my_element_id`. If it was found, we need to set up some configuration data via the [setAttribute](https://developer.mozilla.org/en-US/docs/Web/API/Element/setAttribute) command so that the widget can successfully render. Finally, we check to make sure that `renderRCWidget` is available to call by checking the type of it using [typeof](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof). If the value matches "function", then it is safe to call the function and pass our element to it.
Assuming that your widget id is correct, you will see a widget rendered in the element you specified.
