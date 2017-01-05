# Responsive Images: final version #
This is project that I made during my Udacity's Responsive Images [course](https://www.udacity.com/course/responsive-images--ud882). Initially the blog looked like [this](http://udacity.github.io/responsive-images/downloads/RI-Project-Part-1-Start.zip).
Course journey involves understading responsive images, using grunt to optimize images and automate workflow, I also helped me to go deep in world of  source set `srcset` attribute and `<picture>` element :)
##Notes
I used [this](https://github.com/somerandomdude/grunt-webp) grunt plugin to convert all images in images/ folder to [webp](https://developers.google.com/speed/webp/).  
This plugin depends on WebP's cwebp encoder. You'll need to install the [WebP Package](https://developers.google.com/speed/webp/download) or use [webp-bin](https://github.com/yuanyan/node-webp-bin).  
As a side note: make sure to run `npm install webp-bin` after `npm install` (i.e. installing dependencies from package.json) otherwise it'll generate an error message `Error: Cannot find module 'webp-bin'`  
After that only run `grunt`

--> this can be also done with imagemagick command line tools. Simply used the command in terminal
>mogrify -format jpg *.png

You can read more over [here](http://www.imagemagick.org/script/mogrify.php)

<hr>
I am really sorry for the messed created here :( I think this was the based I could do with my current knowledge :)
`images_src/art_direction` I used an Image Editing tool to generate crop of the images and then used grunt to generate images as per my requirement. Naming convention for art_direction images is little different from other images but this is the only way it can be done without more mess. You'll know what I mean when you'll see Gruntfile.js  
<hr>
I thing more I would like to point here :)  
I have used `<picture>` element for all images. I had to because I am supplying webp for browser that support it and jpeg for that doesn't.  
Now here are some good general practices:  
  
  
* Only use `<picture>` element when you want to server files with diffrent format (here jpeg and webp) or you are dealing with art direction case.  
* Only use `media` attribute for resolution switching case
* Now for resolution-switching case we can simply use `srcset` with `img` with either using <mark>1x, 2x</mark> descriptor or <mark>Width</mark> descriptors. Now again there is a limitaion with 1x, 2x.. descriptors you can only have two images (say 2560px wide and 1280px wide) now It would be complete waste on a 320px wide viewport. This can be handle in two ways:  
	* We use use `media` attribure in `<picture>` to provide different images for diffrent viewport width. For our responsive blog I have used this technique. Providing large 1x, 2x images for larger viewport, medium 1x, 2x for medium sized viewport and small 1x, 2x smaller viewports. Okay I know it's not going good :( but trust me It'll get better :P . Now way we are doing it here is not recommened because we are forcing browser to choose images instead of letting browser decide what is best. So bottom line - *avoid using `media` attribute for resolution switching case*  
	* Now other way would be much simpler - Use <mark>Width</mark> descripots. Simply use `srcset` with `img` and provide images with different resolution. This is much easier and here we are letting browser decide what is best for user. In our responsive images blog it can done for resolution-switching case as: `<img src="images/default,jpg srcset="large2x.jpg 1600w, large1x.jpg 800, medium2x.jpg 1024w, medium1x.jpg 640px, small.jpg 320px" alt=""` See I told you naa.. I gets better :B. Now a simple question would "what if I want to provide webp support?" Well it's simply use `<picture>` element and there will be no requirment for `media` attribute. Simply use `<source>` with `type` specified as `image/webp` and `image/jpeg`  
* Now at last I would justify myslef why i used `media` attribute for resolution switching case. First I was asked to do so :P as Lesson:4 last Quiz asked us to do so, Second I want to keep naming of images in `images/` folder less messy (Guess what! I know it's already so0 much messy :D). For the sake of this my first **readme** I am commenting out a code for `still_life image case` in HTML. You can go there and check it how it should be done. Please note the images name I have used in the code does exist in our `images/` folder.

Congrats I you made it till here. I am open to you suggestion so let's make this better :)

——



##Udacity's `readme.md` begins here
This version uses the picture element for art direction: different image crops are loaded, depending on viewport size.

The images still use `max-width: 100%` – which means 'expand the image display size to fit the container, but no larger than the natural width of the image'. What defines the size of the body images? You can find out with the Dev Tools.

## To do ##

* Getting text size right is hard. Is the body text too big or small on some devices and window sizes? Are the headings the right size relative to the body text?
* In GPRS emulation mode, this page still takes nearly a minute to load. Images load randomly – and the image captions load first and don't make sense without the images. How might image loading be accomplished more efficiently? Take a look at the [Resource Priorities](https://dvcs.w3.org/hg/webperf/raw-file/tip/specs/ResourcePriorities/Overview.html#attr-lazyload) editor's draft. What about JavaScript alternatives, such as the jQuery [Lazy Load Plugin](http://www.appelsiini.net/projects/lazyload)? Any potential problems?
* The markup is verbose! We've gone from around 7,000 characters to over 14,000. That's twice the download size – just to start displaying text. How could we improve this?
* Check the page with [Page Speed Insights](https://developers.google.com/speed/pagespeed/insights/?url=http%3A%2F%2Fudacity.github.io%2Fresponsive-images%2Fproject%2Ffinal%2F&tab=mobile): the images are still unoptimized.

Check the page with the Chrome Dev Tools:

* Open the tools, open the Network tab, reload the page and look at the number of requests, total transfer size and time to load.
* Change to device emulation mode by clicking the phone icon in the Dev Tools (at the top left next to the magnifying glass icon). Try the various throttling options to emulate a GPRS mobile phone cell connection – now look at the Network tab. Total page weight is now less than 300KB, and page load is less than 1.5s on DSL – a lot better than the very first version, which was over 3MB in size and took several minutes to load on DSL.

The page takes several minutes to complete loading. (Remember that studies by Amazon, Google and others show an increased drop off in revenue with delays of less than 0.1 seconds!) Even with a good DSL connection, load time is still over 10 seconds.
* Try out emulation on different devices, portrait and landscape (click the icon next to the dimensions). What problems do you notice with each image? Which ones look worse?

Check the page from Page Speed Insights – lots more problems!



-----------------------------------------------------
**Initial Readme me**
# Responsive Images: Project Part 3 #

## Your Goals: ##

* Replace all of your images with `<picture>` elements!
* Include `alt` attributes to be a better netizen.
* (Optional) Add a custom font and try styling the text better!

## How you know you're done ##

A code will appear in the Udacity Feedback when all Project Part 3 tests pass. Paste the code in to the Udacity classroom to complete the quiz!

[More on the Udacity Front-End Grading Engine](https://github.com/udacity/frontend-grading-engine)

## Current Problems with the Page ##

* The `<picture>` element allows browsers to decide which image to display based on media queries and device pixel ratios. Right now, the page is downloading images that are simply too big and waste too many bytes. How low can you get the page weight once the browser starts downloading images that are as small as possible?
* `alt` attributes make your sites accessible to the vision impaired and anyone surfing the web on a screen reader. Make sure to include them!
* The blog is visually simple. What can you do to make it look better?

## General Advice ##

Share your finished blog in the Udacity forums!
