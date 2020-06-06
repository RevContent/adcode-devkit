# Revcontent Ad Code - Dev Guide

Revcontents ad code allows publishers to display widgets using modern, lightweight javascript. A typical widget would look like the following:

![A typical Revcontent Widget](static/img/rc-widget.png)

This guide aims to provide you with technical documentation on how to leverage our ad code, ranging from basic use to advanced implementations. Although we've tried to make our ad code as easy as possible to use, there are certain considerations that must be taken at times to ensure that you are getting the most from your widgets.

### Contents
* [Getting Started](#getting-started)
* [Manual Renders](manual-renders.md)
* [Placing Multiple Widgets](multiple-widget-placements.md)
* [Detecting Adblockers](detecting-adblockers.md)

### Getting Started

A typical basic ad code for a Revcontent widget looks similar to the following:

    <div id="rcjs_load_x9cns"
         data-rc-widget
         data-endpoint="trends.revcontent.com"
         data-widget-id="XXXXX"></div>
    <script src="https://assets.revcontent.com/master/delivery.js" defer></script>

This div has four data attributes:

* An id, optional but recommended in case access to the element is required for custom code or logic
* An identifier of data-rc-widget, which flags the element as being a target for rendering a widget onto the page
* An endpoint, which is used to make api calls for content
* A widget id, which holds a numerical value for what widget to display

With the exception of id, these are all required attributes in order to properly render a widget on the page.
