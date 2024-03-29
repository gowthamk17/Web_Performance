# Web Performance

## Why speed matters?
+ for retaining users
+ for online business improving conversions
+ for better user experience

## HTML performance considerations
+ html document is the first content to load on a site 
+ very low Time To First Byte (TTFB) ensure good other metricks LCP, FCP
+ very less redirects
+ caching html responses
    + E-tag
    + Last-Modified
    + max-age
+ Measure server response timing Server-Timing header
+ use compressions
+ use CDN's

## Understanding the critical path
+ render blocking resourced like css in the head
    + browser will pause the render and wait for the blocking resource to receive but in the mean it still parses the remaining content
+ parse blocking content which is a synchronouse js will blocking the whole parsing because it may containt script the changes cssdom or dom

## Optimize Resource Loading
+ CSS
    + minification
    + remove unused css
    + avoid using @import 
+ Javascript
    + using async and defer
        + async script always run as soon as they are fetched
        + defer script alwasy run after all the parsigns are done
    + reduce client side rendering 
    + minification

## Resource hints
+ preconnect
    + informing browser about a cross origin which will be requested in the near future
    + a common case is google fonts
+ dns-prefetch
    + an inexpense verion of preconnect but it donesn't fetch content only does dns loop for the link
+ preload
    + Initiate an early request for the content 
+ prefetch
    + Informing a browser a future request may be on the origin
+ fetchpriority
    + set priority for a resource

## Image Performance
+ using proper image size according to the device size
+ srcset attribute in img helps browser to get correct image with dpr of the screen
+ sizes gives browser instruction on image size with media query condition 
+ use latest image formats such as avif and webp
+ use compression 
+ use picture tag to give browser optional images
+ using Accept key in request attribute server can serve the exact image format the browser supports
+ set loading attribute to lazy to keep the image from loading util in comes into viewport
+ add decoding attribute to the img tag

## Video Performance
+ use ffmpeg for compression
+ use source tag to enable mutiple formats
+ use postter attibute to show image before video loads
+ set preload=none to keep video from loading until the user intiates playback

## Optimize for web fonts
+ use preload to get font-face font
+ add font face as inline in head prefer this over preload
+ add preconnect to fetch font before hand faster
+ use woff2 font format only
+ use subsetting to only fetch the character needed

## Code Splitting
+ use bundlers to convert modules to other module syntax since modules doesn't have streamlining compilation
+ if we used modules use .mjs extension which will uses streamlining compilation

## lazy loading
+ lazy load all the iframes which are not in view port
+ don't lazy load the image which is in viewport like hero
+ prefer video over gif

## prefetching and prerendering
+ use prefetch hint on resources to fetch with low priority
+ use as=document attribute to prefetch the next possible loading page

## Web Workers
+ web workers are runs on a separate thread and has to no direct acess to window or dom
+ it can access to window by a messaging pipeline