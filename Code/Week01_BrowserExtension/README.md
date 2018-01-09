
BROWSER EXTENSION TUTORIAL
====

Below is a description of the basic parts you'll need to build a browser extension, install, and test it. For more info on CSS, Javascript, and JQuery, see the *Resources* section at the bottom.

- - -

### EXTENSION FILES
While there are lots of ways to structure an extension, we need at least two files: some Javascript to run and a "manifest" file.

**EXTENSION.JS**  
Your code! This is the extension code itself, which is called by `background.js` when the button is pressed. This isn't the only way to handle this, but keeps the rest of the code tucked away and the messy bits hidden (based on [this template code](https://gist.github.com/danharper/8364399)).

**BACKGROUND.JS**  
A script that runs constantly, waiting for the extension button to be clicked. No need to change this if using our template, but if you wanted the extension to run automatically, or access other parts of the Chrome API, you'd likely need to do it here.

**MANIFEST.JSON**  
A metadata file in [json format](https://en.wikipedia.org/wiki/JSON) that lists properties and permissions for your extension. Comments aren't allowed in a json file, so here's info about each section.

* Name, description, and version: information about the extension itself and who made it  
* `browser_action`: interface elements for your extension  
  * `default_title`: popup text that appears when the user hovers over the extension's button, telling us what it does  
  * `default_icon`: path to a png icon file (should be 19x19px)  
* `permissions`: what access your extension should have  
  * `tabs`: allow access to the list of tabs, and let us change them  
  * `<all_urls>`: let us access and change any page (we could also list a specific url, or user the `*` for wildcard selection – for example, `*.gov` would only change pages with the US government TLD)  
* `background`: path to the `background.js` script (see info below)  
* `content_scripts`: extra Javascript to load that needs to be seen by the extension (in this case we need JQuery)  
* `manifest_version`: tells Chrome which version of the manifest spec this is – leave at 2

- - -

### INSTALLING YOUR EXTENSION

Once you're ready to try your extension, you'll have to add to your browser.

* In the address bar, type `chrome://extensions`  
* Check box that says *Developer mode*  
* Click *Load unpacked extension...* and navigate to the folder with your code in it  
* Check the *Enabled* box to activate your extension  
* If you make changes to the `manifest.json` file, you can reload the extension from this page – you can also delete your extension from here, if you want  

### SEEING CHANGES  
If you're just changing the `extension.js` file, you don't need to reload the extension itself. Instead:

* Save the `extension.js` file  
* Click the extension button again  
* If the page is messed up, you can refresh it before running the extension again  

- - -

### RESOURCES  
While by no means exhaustive, below are some useful resources for what properties can be manipulated through CSS, some of the ways JQuery can interact with a page's content, and 

**CSS**  
Info on what different properties are called and what values they can be changed to:

* [CSS properties](https://www.w3schools.com/cssref/default.asp)  

**JQUERY**  
Some of the ways JQuery can interact with a page's content:

* [Selecting elements](https://api.jquery.com/category/selectors)  
* [Manipulating the DOM](https://api.jquery.com/category/manipulation)  
* [Effects, including animation](https://api.jquery.com/category/effects)  

**EXTENSIONS**  
The official Chrome extension documentation (gets super complex really quickly, but might be useful):

* [Sample extensions](https://developer.chrome.com/extensions/samples)  
* [Commands to access Chrome via Javascript](https://developer.chrome.com/extensions/api_index)  
* Other (mostly fancy) things extensions can do in the [developer's guide](https://developer.chrome.com/extensions/devguide)  
* [How to publish your finished extension](https://developer.chrome.com/extensions/hosting)  

**PORTING TO FIREFOX**  
It shouldn't take too much work to get your extension to work in Firefox as well. See [this guide](https://developer.mozilla.org/en-US/Add-ons/WebExtensions/Porting_a_Google_Chrome_extension) for more info.

- - -




