# BackstopJS
> BackstopJS is an automated test framework that is written in JavaScript. It servers the purpose of automating visual regression tests, it is simple to set up and configure, and easy to understand. It has many components including the ability to render the DOM and all the elements through the command line, the ability to interact with the page as well as compare images in pixel differentiation.

> In this project, I will provide a quick overview of the framework, how to set it up and how I use it.

## How it works
Visual regression tests or visual testing is an activity performed by the testers to compare different versions of the screenshots taken from the application. A typical visual test would look like this:

![Visual test flow](https://wki5a3.n3cdn1.secureserver.net/wp-content/uploads/2021/02/basckstopjs.png)

* Take a screenshot of the application you are testing
* Save the screenshot and set it as a baseline
* Deploy the newest application version of the UI
* Open the application where you took the screenshot and compare it with the older screenshot
* If there are changes, save the newest screenshot as a baseline, if not, the initial baseline would be still valid

## Install BackstopJS
Assume that you already have Chrome and node.js installed on your computer, lets see how you can install BackstopJS. Globally install it on your computer using this command:
```
npm install -g backstopjs
```

## Setup and configure BackstopJS
Create a new folder structure, navigate to the project directory and run:
```
backstop init
```
This command creates a folder called backstop_data and also, will create a JSON file called backstop.json.

By default, BackstopJS places backstop.json in the root of your project. And also by default, BackstopJS looks for this file when invoked.
Pass a --config=<configFilePathStr> argument to test using a different config file.
Example: Create a backstop.config.js
```
backstop test --config="backstop.json"
```
But if it new project the JSON file will serve as the main confrontation for our tests. This would be the outcome of the command above:

![BackstopJS folder structure](https://wki5a3.n3cdn1.secureserver.net/wp-content/uploads/2021/02/2021-02-01-12_15_20-Untitled-Workspace-Visual-Studio-Code.png)

The viewports are different screen resolutions that the visual test would run for a particular website URL. You can re-configure them.

View [viewports.txt](https://github.com/chabanstas/BackstopJS/blob/main/viewports.txt) to choose from available sizes or create your own.

bitmaps_reference is the folder where our baseline screenshots are saved. 
bitmaps_test is the folder where comparisons of two screenshots take place and it also stores any potential differences highlighting them with squared shape.

The last thing we need to do here is adding the scenarios. 
As you can see the initial scenario is the default one and it is created after we initialize the project. 
We can change the `label` and `URL` to what we want. 
We can add a new scenario for a specific URL within the particular website or a totally different website URL. For this post, we will change `label` and `URL`:

![Change label and URL](https://github.com/chabanstas/BackstopJS/blob/main/Screenshot_22.png)

Now we’re ready to run the test!

## Meta
Your Name – [@YourTwitter](https://twitter.com/dbader_org) – YourEmail@example.com
Distributed under the XYZ license. See ``LICENSE`` for more information.
[https://github.com/yourname/github-link](https://github.com/dbader/)
[npm-image]: https://img.shields.io/npm/v/datadog-metrics.svg?style=flat-square
[npm-url]: https://npmjs.org/package/datadog-metrics
[npm-downloads]: https://img.shields.io/npm/dm/datadog-metrics.svg?style=flat-square
[travis-image]: https://img.shields.io/travis/dbader/node-datadog-metrics/master.svg?style=flat-square
[travis-url]: https://travis-ci.org/dbader/node-datadog-metrics
