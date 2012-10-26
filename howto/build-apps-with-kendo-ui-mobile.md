---
title: Build Apps with Kendo UI Mobile
meta_title: Build mobile apps with Kendo UI Mobile framework | Kendo UI Documentation
meta_description: This tutorial you help you develop mobile apps with Kendo UI Mobile widgets and test apps on different mobile platforms.
slug: howto-build-apps-with-kendo-ui-mobile
tags: How-To
publish: true
---

# How-To: Build Apps With Kendo UI Mobile

In this how-to, we'll examine how to build apps with Kendo UI Mobile. You will learn:

- What makes Kendo UI Mobile unique
- How to use Kendo UI Mobile to build a basic app
- How to test an app on different mobile platforms
- How to work with Kendo UI Mobile's adaptive rendering
- Next steps for putting a Kendo UI Mobile app in app stores 

At the conclusion of this how-to, you should be able to build a mobile app with HTML, JavaScript, and Kendo UI Mobile that can be deployed through a mobile browser or app store.

## Why Kendo UI Mobile

Kendo UI Mobile is designed to help developers build mobile app experiences using HTML and JavaScript that automatically adapt to the native look-and-feel of different mobile platforms. Developers using Kendo UI Mobile can focus on their app's function and content and let the Kendo UI framework handle differences between platforms like iOS and Android.

Where some mobile HTML frameworks focus on providing a "one size fits all" experience, Kendo UI Mobile focuses on delivering perfectly tailored experiences for every platform where an app is run. Built and packaged correctly, a Kendo UI Mobile app can be virtually indistinguishable to end-users from a native SDK app.

The advantage of building apps with HTML, JavaScript, and Kendo UI Mobile, of course, is that developers can maintain a single code base to target all major app platforms. Your team can focus on becoming masters of HTML, JavaScript, and CSS, rather than being average practioners of Objective-C, Java, .NET, UIKit, and the myriad of other developer skills need for cross-platform mobile app development.

## Building Blocks of a Kendo UI Mobile App

First of all, all Kendo UI Mobile apps are built entirely with HTML, JavaScript, and CSS. Those are the only skills you will need to build a Kendo UI Mobile app that looks and feels native across mobile platforms. If you plan to work with data, you should also be familiar with [JSON](http://en.wikipedia.org/wiki/JSON).

There are a few key, non-visual pieces of Kendo UI Mobile used in virtually all apps:

1. **[Application](http://demos.kendoui.com/mobile/application/index.html)**:
The shell of a Kendo UI Mobile app. Application manages all navigation, application history, loading views, mobile meta tags, and other essential mobile app tasks.
2. **[Layout](http://demos.kendoui.com/mobile/layout/index.html)**: Defines the reusable portions of a mobile app, similar to a MasterPage or template. Layouts are often used improve app maintainability by defining things used across multiple views, like navigation. Layouts are not required, but encouraged.
3. **[Views](http://demos.kendoui.com/mobile/view/index.html)**: Individual pages of a mobile app. Views contain the majority of an app's content. Every will app will have one or more views.

Where Layouts and Views are defined with HTML, the Application is simply JavaScript. There is no markup associated with an Application. Let's create the basic structure of a Kendo UI Mobile app.

### Step 1: Create a simple HTML page
Kendo UI Mobile apps can be created using simple html pages. To begin, try creating a page called "index.html" with code like this: 

	<!DOCTYPE html>
	<html>
	<head>
		<title>My App</title>
		<!--TODO: Add CSS links-->
	</head>
	<body>

		<!--TODO: Add JavaScript referneces-->
	</body>
	</html>

> Where are the mobile meta tags? Don't worry. Kendo UI Mobile will automatically add mobile meta tags for you at runtime.

### Step 2: Add references to Kendo UI Mobile
Just as with other parts of the Kendo UI framework, adding Kendo UI Mobile to your applciation is a simple process of copying the provided JavaScript and CSS assets in to your project and then configuring the CSS and JavaScript links. When setup, your app page should look something like this:

	<!DOCTYPE html>
	<html>
	<head>
		<title>My App</title>
		
		<link href="css/kendo.mobile.all.min.css" rel="stylesheet" />
	</head>
	<body>

		<script src="js/jquery.min.js"></script>
		<script src="js/kendo.all.min.js"></script>
	</body>
	</html>

This example uses the minified versions of Kendo UI's scripts and styles that include all features, widgets, and themes. You can create customized, more compact versions of the Kendo UI resources for your apps if you choose not to use specific features or widgets. For development, the "all" minified files are the best choice.

Also note that we've included a reference to jQuery. jQuery is the only external dependency for Kendo UI.

> Modern CSS and JavaScript references don't require the `type` attribute in most cases. You can safely add references to your CSS and JavaScript assets while omitting this attribute and everything will work fine in new and old browsers. The `type` attribute is officially made optional for both [script](http://dev.w3.org/html5/spec/the-script-element.html#attr-script-type) and [link](http://dev.w3.org/html5/spec/the-link-element.html#attr-link-type) elements in the HTML5 spec.

### Step 3: Define an app layout
The layout is your app's template. All content from views (which we'll create later) will be rendered inside of the layout. A layout can contain anything, but generally it's where your app titlebar and navigation will live. Let's add a layout to our app with these basic elements.

	<!DOCTYPE html>
	<html>
	<head>
		<title>My App</title>
		
		<link href="css/kendo.mobile.all.min.css" rel="stylesheet" />
	</head>
	<body>
		<section data-role="layout" data-id="default">
			<header data-role="header">
				<div data-role="navbar">My App</div>
			</header>
			<!--View content will render here-->
			<footer data-role="footer">
				<div data-role="tabstrip">
					<a href="#">Home</a>		
				</div> 
			<footer>
		</section>

		<script src="js/jquery.min.js"></script>
		<script src="js/kendo.all.min.js"></script>
	</body>
	</html>

Let's break this update down. First, you see that we've started to use the `data-role` attribute in our HTML. This communicates to Kendo UI Mobile that the HTML should be transformed when the Appplication is initialized. So, in this case:

`<section data-role="layout" data-id="default">`

When the Application is initialized, this block of HTML will be initialized as a Kendo UI Mobile layout. The `data-id` attribute is further defined to give this layout a unique name that can be used by our views.

Next, we've introduced a couple of Kendo UI Mobile's visual widgets: Navbar and TabStrip. We'll talk more about these later, but for now note that they are also configured with the simple `data-role` attribute.

### Step 4: Create a view
Now that the app's layout is defined, we need at least one view that can be displayed when our app loads. Most apps will have many views, but we'll start with something simple:

	<!DOCTYPE html>
	<html>
	<head>
		<title>My App</title>
		
		<link href="css/kendo.mobile.all.min.css" rel="stylesheet" />
	</head>
	<body>
		<div data-role="view" data-layout="default">
		Hello Mobile World!
		</div>

		<section data-role="layout" data-id="default">
			<header data-role="header">
				<div data-role="navbar">My App</div>
			</header>
			<!--View content will render here-->
			<footer data-role="footer">
				<div data-role="tabstrip">
					<a href="#">Home</a>		
				</div> 
			<footer>
		</section>

		<script src="js/jquery.min.js"></script>
		<script src="js/kendo.all.min.js"></script>
	</body>
	</html>

Nothing too fancy in this update. We've once again used the `data-role` attribute to define our view, and we've also used the `data-layout` attribute to tell our view which layout template to use.

We can put anything inside of a view, including other Kendo UI Mobile widgets. For now, we've used some simple Hello World text.

If you try to run the app now, you'll see a bunch of HTML, but nothing will look right. We need to take one more step.

### Step 5: Initialize the mobile application
So far, we've defined some HTML, but we have not written any JavaScript. To make our HTML come to life and start looking and feeling like a mobile app, we need one line of script:

	<script>
		var app = new kendo.mobile.Application();
	</script>

Add this script block *after* your jQuery and Kendo UI Mobile script links, but before the closing `body` tag.

This single line of JavaScript will automatically initialize your Kendo UI Mobile app and all widgets with the `data-role` attributes. Go ahead! Give it a try. Load your page in a browser and see the beginnings of your HTML mobile app.

> If you have trouble seeing the app, make sure all of your script and CSS resources are loading without error (using the browser developer tools). Some browsers (like Chrome) will block the loading of external resources if you load your page using the `file://` protocol. Instead, test your pages using local web server (localhost) or a browser that does not restrict local resources, like Safari.

## Add Views and Navigation
Now that you have a basic Kendo UI Mobile app structure setup, you can begin adding more views to your app. Multiple views can be defined in the same file, or views can be defined in separate HTML files. For larger apps, maintaining views in separate files during development is the prefered approach.

To add a second view to your app, create a new page called "about.html" with the following content:

	<!DOCTYPE html>
	<html>
	<head>
		<title>About</title>
	</head>
	<body>
		<div data-role="view" data-layout="default">
		All About My App
		</div>
	</body>
	</html>

This page does **not** redefine references to the Kendo UI Mobile script or CSS resources. This page requires minimal markup. When the Kendo UI Mobile application loads an external view (a view defined in separate file), it will look for the first `data-role="view"` in the `body` element and discard the rest of the page.

To enable our app to navigate to this page, let's update the **TabStrip** added previously to include a navigation link for our external view:

	<footer data-role="footer">
		<div data-role="tabstrip">
			<a href="#">Home</a>
			<a href="about.html">About</a>		
		</div> 
	<footer>

When Kendo UI Mobile encounters a link to an external view, it will automatically load and cache the view with Ajax and provide a seamless navigation experience.

> If you do not want a link in Kendo UI Mobile to be treated as a view, be sure to include the `data-rel="external"` attribute. 

If we did want to maintain multiple views in a single page, we would simply navigate the `id` of the view, like this:
	
	<div data-role="anotherView" id="view2">...</div>
	<footer data-role="footer">
		<div data-role="tabstrip">
			<a href="#">Home</a>
			<a href="about.html">About</a>
			<a href="#view2">More</a>		
		</div> 
	<footer>

Finally, as you've probably noticed if you're testing as we go, your navigation is now working, but the views all appear instantly with no animation transition. To really give your app that native mobile feeling, we can add a default transition for all views by modifying the Application initalization script:

	<script>
		var app = new kendo.mobile.Application(document.body, 
		{
			transition:'slide'
		});
	</script>

Now your application is looking native! At this point your application should look like this if you've been following along:

![Basic Kendo UI Mobile app](https://github.com/telerik/kendo-docs/raw/master/tutorials/images/km-basic-app-1.png)

## Testing for Multiple Platforms
By default, Kendo UI Mobile will render with an iOS look-and-feel if it does not detect another mobile platform. When you want to test the look-and-feel of your app on other platforms- and see how Kendo UI Mobile automatically adapts- you can take one of two paths:

1. **Force Platform Rendering**
2. **Use Browser Tools**

Of course, nothing replaces actually testing on mobile devices. In many cases, the Kendo UI Mobile styles look better on devices than in desktop browsers. Be sure to test on an iPhone, Android, BlackBerry, or whatever devices you intend support before deploying your app.

## Tweaking Apps for Specific Platforms
Kendo UI Mobile's automatic platform adapting is a huge time saver, but sometimes developers want to customize the presentation of an app for specific platforms. When you want to take more control over the experience different devices see, you should use the `data-platform` attribute. For example:

	<div data-role="layout" data-id="foo" data-platform="ios">
  		<div data-role="header">iOS App</div>
	</div>

	<div data-role="layout" data-id="foo" data-platform="android">
  		<div data-role="header">Android App</div>
	</div>

The use of `data-platform` in these examples will cause different headers to be displayed to iOS and Android users of the app.

The `data-platform` override is currently only available on layout elements.

You can also use custom CSS to fine-tune your apps. When Kendo UI Mobile initalizes an app, it adds a device specific CSS class to the Application root element. This allows you to create styles that specifcially target different platforms. For example, on iOS, the HTML for an initializted app might look like:

`<body class="km-ios km-vertical" style="overflow: visible; ">`

Now, if we want to create styles for our app that will only be applied to iOS devices, we can create CSS rules like this:

	.km-ios .myStyle { color: blue; }
	.km-android .myStyle { color: green; }

This added degree of control makes it a cinch to precisely style apps for different target platforms.

## Next Steps: Polish and Preparing for App Stores
We've covered a lot of ground so far. You should now be able to:

- Create a basic Kendo UI Mobile application with layouts and views
- Add additional views to an app and handle navigation
- Test the look and feel of your app for different platforms
- Take control over styling your app for different platforms

The next steps you will take in your app building journey may include things like:

- Creating and configuring an icon for your app
- Consuming and customizing Kendo UI Mobile widget icons
- Handling view events to initalize your data and load data
- Packaging your app with Cordova to access device APIs

See the related docs to learn more about these advanced topics. Otherwise, have fun building awesome cross-plaform mobile apps with HTML, JavaScript, and Kendo UI Mobile!