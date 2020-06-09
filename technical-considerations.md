# Technical Considerations

When using Revcontents ad code, there are certain technical considerations you must take to ensure that you will get the most out of our  ad code. This document contains some considerations to take when working with our ad code.

#### Load the JavaScript file a single time
The JavaScript we use to render widgets on a page was developed so that it only needs to be loaded one time in the DOM. Once loaded, it will aggregate all valid widget placements (this is achieved via [querySelectorAll](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll)) and then render them all automatically. Because of this, it is important that this is only loaded single time in the DOM. If you have a scenario where you need to render another widget after this file has been loaded, consider using the process for [manually rendering a widget](manual-renders.md).

#### Defer JavaScript execution until ready
We recommend deferring the load of the JavaScript file when adding it to the DOM. Flagging the script as deferred ensures that the DOM has ample time to finish rendering prior to it being executed. This strategy becomes especially important when needing to modify the widget placement in any way (such as using ad blocker functionality, setting sub-ids, etc.). For more information on the technical behaviors behind deferring a script, see [this article](https://flaviocopes.com/javascript-async-defer).

#### Avoid using localhost when testing widget code
Due to CORS policies, our backend services reject any origin that includes localhost. To avoid this, we recommend using a service like [codepen](https://codepen.io) or running a development server so that api calls can be successfully completed. We have created a simple docker setup to aid in this process that can be access [here](https://github.com/RevContent/Simple-Docker-Setup).
