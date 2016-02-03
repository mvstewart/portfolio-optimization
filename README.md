## Website Performance Optimization portfolio project

I accepted the challenge to optimize this online portfolio for speed! In particular, I optimized the critical rendering path and made this page render as quickly as possible by applying the techniques I've picked up in the [Critical Rendering Path course](https://www.udacity.com/course/ud884).

#### I'm still working on this project!

## How to get started:

#### Instruction for installing grunt packages using NPM:
- Open command line, proceed to the folder with the project and run "npm install". It will automatically install all needed grunt packages.

#### Instructions for running grunt tasks:
- Open command line (or terminal), proceed to the folder with the project and type "grunt". The default tasks of uglify and css-minify will run automatically.

#### Instructions for serving the app:
- Simply open the index.html file in any modern browser, like Chrome or Safari. You can optionally run a local server - instructions below.

#### Instructions for checking page speed score:
- To check the speed of the homepage, go to Pagespeed Insights and follow the instructions there.

#### Optional: run a local server
1. Check out the repository
1. To inspect the site on your phone, you can run a local server

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```

1. Open a browser and visit localhost:8080
1. Download and install [ngrok](https://ngrok.com/) to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ngrok http 8080
  ```

1. Copy the public URL ngrok gives you and try running it through PageSpeed Insights! Optional: [More on integrating ngrok, Grunt and PageSpeed.](http://www.jamescryer.com/2014/06/12/grunt-pagespeed-and-ngrok-locally-testing/)


####Part 1: Optimized PageSpeed Insights score for index.html

- Mobile speed 93/100
- Desktop speed 94/100

To optimize the website speed even more:
- Compress (losslessly) profile picture and pizza image;
- Set browser caching.

####Part 2: Optimize Frames per Second in pizza.html

I modifed views/js/main.js until the frames per second rate is 60 fps or higher. In particular, I modified the following:
- function changePizzaSizes(size): optimized for-loop by taking calculation for array length and phase declaration out of the loop condition; removed call for determinDx() in the for-loop; added switch(size) inside the changePizzaSizes;
- function updatePositions(): the for-loop is running faster since I moved the repetitive code out (scrollDivided), and declared phase outside of the for-loop to prevent it from being created every time the loop runs (that loop now runs in reverse too); changed style.left to style.transform to prevent jank with layout recalc;
- used more specific "getElementsByClassName()" instead of non-specific "querySelectorAll()".
- enabled hardware accelaration in style.css by setting backface-visibility as hidden and adding transform: translateZ(0);
- changed the max for i from 200 to 100 in the for-loop actually creates and appends all of the pizzas when the page loads;
- changed basicLeft to style.left and added (+ 'px') in the sliding pizzas generation event listener function for the proper functioning of style.transform in the updatePositions();
- reduced the number of generated sliding pizzas from 200 to 30, since at any time it displays only 30 pizzas.

I used the FPS Counter/HUD Display in Chrome developer tools described here: [Chrome Dev Tools tips-and-tricks](https://developer.chrome.com/devtools/docs/tips-and-tricks).


####Part 3: Grunt
I have created package.json file and ran grunt to minimize views/js/main.js and views/css/style.css and views/css/bootstrap-grid.css

### Optimization Tips and Tricks
* [Optimizing Performance](https://developers.google.com/web/fundamentals/performance/ "web performance")
* [Analyzing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp.html "analyzing crp")
* [Optimizing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/optimizing-critical-rendering-path.html "optimize the crp!")
* [Avoiding Rendering Blocking CSS](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css.html "render blocking css")
* [Optimizing JavaScript](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/adding-interactivity-with-javascript.html "javascript")
* [Measuring with Navigation Timing](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/measure-crp.html "nav timing api"). We didn't cover the Navigation Timing API in the first two lessons but it's an incredibly useful tool for automated page profiling. I highly recommend reading.
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/eliminate-downloads.html">The fewer the downloads, the better</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer.html">Reduce the size of text</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization.html">Optimize images</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching.html">HTTP caching</a>

### Customization with Bootstrap
The portfolio was built on Twitter's <a href="http://getbootstrap.com/">Bootstrap</a> framework. All custom styles are in `dist/css/portfolio.css` in the portfolio repo.

* <a href="http://getbootstrap.com/css/">Bootstrap's CSS Classes</a>
* <a href="http://getbootstrap.com/components/">Bootstrap's Components</a>

### Sample Portfolios

Feeling uninspired by the portfolio? Here's a list of cool portfolios I found after a few minutes of Googling.

* <a href="http://www.reddit.com/r/webdev/comments/280qkr/would_anybody_like_to_post_their_portfolio_site/">A great discussion about portfolios on reddit</a>
* <a href="http://ianlunn.co.uk/">http://ianlunn.co.uk/</a>
* <a href="http://www.adhamdannaway.com/portfolio">http://www.adhamdannaway.com/portfolio</a>
* <a href="http://www.timboelaars.nl/">http://www.timboelaars.nl/</a>
* <a href="http://futoryan.prosite.com/">http://futoryan.prosite.com/</a>
* <a href="http://playonpixels.prosite.com/21591/projects">http://playonpixels.prosite.com/21591/projects</a>
* <a href="http://colintrenter.prosite.com/">http://colintrenter.prosite.com/</a>
* <a href="http://calebmorris.prosite.com/">http://calebmorris.prosite.com/</a>
* <a href="http://www.cullywright.com/">http://www.cullywright.com/</a>
* <a href="http://yourjustlucky.com/">http://yourjustlucky.com/</a>
* <a href="http://nicoledominguez.com/portfolio/">http://nicoledominguez.com/portfolio/</a>
* <a href="http://www.roxannecook.com/">http://www.roxannecook.com/</a>
* <a href="http://www.84colors.com/portfolio.html">http://www.84colors.com/portfolio.html</a>
