# Multiple Widget Placements

It's possible to have more than one widget on a page. If you require this behavior, you can simply duplicate the div example shown above. However, you will only need to add the script tag to the page one time. The Revcontent JavaScript file will find any elements on the page that have the `data-rc-widget` attribute on them and render each widget using the respective data set on them. Following this pattern, your markup would look similar to the following:

    <!DOCTYPE html>
    <html lang="en">
      <head>
        <meta charset="UTF-8">
        <title>Example Page</title>
      </head>
      <body>
        <div class="content">
          <div id="rcjs_load_x9cns"
               data-rc-widget
               data-endpoint="trends.revcontent.com"
               data-widget-id="XXXXX"></div>
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse vitae dui porta, varius arcu eget, porttitor purus. Quisque auctor blandit risus sollicitudin accumsan. Aenean lorem diam, molestie at lectus a, posuere sodales leo. Suspendisse placerat libero vel tortor aliquet, non varius diam lacinia. Suspendisse potenti. Pellentesque in viverra justo, vel convallis purus. Cras ante lorem, viverra a congue vel, feugiat eget lorem. Proin vel euismod risus.</p>
          <div id="rcjs_load_zs8af"
               data-rc-widget
               data-endpoint="trends.revcontent.com"
               data-widget-id="XXXXX"></div>
          </div>
    
        <script src="https://assets.revcontent.com/master/delivery.js" defer></script>
      </body>
    </html>

Here we have a simple HTML page that has widget placements above and below the paragraph element. At the bottom of the body, we have a script tag that will defer execution until the DOM has finished rendering. If your widget widget attributes are configured correctly, you will see each widget rendered on your page.
