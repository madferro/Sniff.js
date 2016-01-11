<a href="http://www.alessandroferrini.it/lab/sniff" target="_blank">Sniff.js</a> - detect and inject browser infos
========
<small><em>version 1.0</em></small>
<ul>
	<li><a href="https://github.com/madferro/Sniff.js#what-is-it">What is it</a></li>
	<li><a href="https://github.com/madferro/Sniff.js#how-to-use-it">How to use it</a></li>
	<li><a href="https://github.com/madferro/Sniff.js#example">Example</a></li>
	<li><a href="https://github.com/madferro/Sniff.js#detectable-browsers-and-mobile-os">Detectable browsers and mobile OS</a></li>
	<li><a href="https://github.com/madferro/Sniff.js#javascript-object">Javascript Object</a></li>
</ul>
##What is it?
<strong>Sniff.js</strong> is an ultralightweight javascript browser sniffer that detects user's browser type, version and eventually mobile OS type injecting this informations directly in the <code>class</code> attribute of the <code>html</code> element.
<br/><br>
This informations can be very useful for CSS styling purpose, because you will be able to write different styling rules according to the browser you're using <strong>in the same CSS stylesheet</strong>. 
<br><br>
You will need no more to create different stylesheets for different browsers (am i meaning IE?) and load them separately, you can put the rules all together.
##How to use it
To use <strong>sniff</strong> you only have to put a reference to the js script in your HTML document's <code>head</code> element, like this:

```html
<!DOCTYPE html>
<html>
	<head>
		<script src="sniff.js" type="text/javascript"></script>;
	</head>
	...
```

Finished!


You don't have to link any type of library or call any function, <strong>sniff</strong> will fire up on it's own.

After being fired up <strong>sniff</strong> will add two or three special classes to you <code>html</code> element:
<ul>
	<li><code>&lt;browser name&gt;</code></li>
	<li><code>v&lt;browser version&gt;</code> (note there's a "v" before the version number)</li>
	<li><code>&lt;mobile OS type&gt;</code> (this class is added only if running on a mobile device)</li>
</ul>
Obviously &lt;browser name&gt;, &lt;browser version&gt; and &lt;mobile OS type&gt; will be replaced by the detected values.
##Example
Suppose you have a supersimple web page like this:

```html
<html>
	<head>
		<title>Your title</title>
		<link rel="stylesheet" href="style.css" type="text/css" />
		<script src="sniff.js" type="text/javascript"></script>
	</head>
	<body>
		<p>Some text</p>;
	</body>
</html>
```
And suppose you want (for unknown reasons) the <code>p</code> element background to be <code>red</code> <u>ONLY WHEN the page is viewed with an IE 10 browser</u>.

When you load the page with an IE 10 browser your <code>html</code> will be transformed into:
```html
<html class="msie v10">
```
So you'll be able to write a specific CSS rule (in your CSS stylesheet file) that applies only to that case. In our example you can put this simple rule in the <code>style.css</code> file :
```css
.msie.v10 p{
	background:red;
}
```

##Detectable browsers and mobile OS
<strong>Sniff</strong> can detect the following browsers and mobile OS:

| Browser name  | Generated classname |
| :------------- | :------------------- |
| Google Chrome  | <code>chrome</code>  |
| Mozilla Firefox  | <code>firefox</code>  |
| Apple Safari  | <code>safari</code>  |
| Opera  | <code>opera</code>  |
| Internet Explorer | <code>msie</code>  |
| Microsoft Edge | <code>edge</code>  |

| Mobile OS | Generated classname |
| :------------- | :------------------- |
| iOS iPad | <code>ipad</code>  |
| iOS iPhone | <code>iphone</code>  |
| iOS iPod | <code>ipod</code>  |
| Android  | <code>android</code>  |
| BlackBerry  | <code>blackberry</code>  |
| Opera Mini  | <code>operamini</code>  |
| Windows Mobile  | <code>iemobile</code>  |

##Javascript object
<strong>Sniff</strong> creates a global javascript object called <code>sniff</code> which contains 5 simple informations:

| Name  | Description |
| :------------- | :------------------- |
| <code>sniff.version</code>  | <stong>Sniff.js</strong> release version  |
| <code>sniff.browserType</code>  | browser type (<code>chrome</code>, <code>firefox</code>, <code>safari</code>, <code>opera</code>, <code>msie</code>) |
| <code>sniff.browserVersion</code>  | major number of version  (e.g. if the complete version is 33.0.1750.146 here you have only 33)|
| <code>sniff.browserVersionExtended</code>  | full number of version  |
| <code>sniff.mobile</code>  | mobile os type (<code>ipad</code>, <code>iphone</code>, <code>ipod</code>, <code>android</code>, <code>blackberry</code>, <code>operamini</code>, <code>iemobile</code>, <code>null</code>) |

