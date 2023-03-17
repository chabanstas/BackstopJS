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

![Change label and URL](https://github.com/chabanstas/BackstopJS/blob/main/screenshots/Screenshot_22.png)

Now we’re ready to run the test!

## Run the initial test
```
backstop reference
```
The URL that we are hitting is https://www.google.com/ and we have three viewports, phone, tablet, and desktop resolutions. This command will save three screenshots in bitmaps_reference folder for the three different viewports.
  
## Compare two screenshots
Since we already saved our baseline images for different device resolutions, we are ready to compare those baseline images with the newest ones. 

For example, we will change the URL to https://images.google.com/:

![Change label and URL](https://github.com/chabanstas/BackstopJS/blob/main/screenshots/Screenshot_23.png)

The command for image comparison would be:
```
backstop test
```

This is showing us that the UI has been changed and the images are different. That’s why we have 3 tests failed for all of the screenshots.

Three images are created under bitmaps_test folder.
  
Since those are the same as the previous ones then we conclude that our UI application page has not been affected by any change made by the developers.
  
Repot is automatically generated:
  
![Change label and URL](https://wki5a3.n3cdn1.secureserver.net/wp-content/uploads/2021/02/image-3-1024x480.png)
  
The report shows all the tests that have been executed as well as all of the screenshots that’ve been compared.
  
## Save new screenshot as a baseline
  
Since there are no changes in the UI, we don’t need to save the newest images but just for the purpose of showing how you can store those screenshots we are going to save them, using the command:
```
backstop approve
```
  
All of the newest screenshots from the bitmaps_test will be promoted to bitmaps_reference folder and would serve us as a baseline for upcoming test comparisons. This would be the case if the design has changed. In some situations, the UI may be broken and after we notice that the images are different, we need to coordinate with the developers and address the issue accordingly. In that case, we would not save the new screenshots since it is a bug, not a change request or a feature.
  
## Meta
Stas Chaban – [@LinkedIn](https://www.linkedin.com/in/stanislav-chaban/)
  
[github](https://github.com/chabanstas)

## Resources
  
* https://qamind.com/blog/visual-regression-tests-using-backstopjs/
* https://github.com/garris/BackstopJS
