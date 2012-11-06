FlexSlider SCSS
===============

Rewritten base CSS for [FlexSlider v2.0](http://www.woothemes.com/flexslider) to gel with [Bones v1.25](http://themble.com/bones/)

By no means is this file perfect, I've simply converted all CSS to nested SCSS and used Bones / Compass mixins where possible.

Feel free to fork and fix where you see fit!

Instructions
-----------

Here's an overall rundown on how to get FlexSlider v2.0 running with Bones v1.25, including the SCSS addition.

*NB: This is assuming you're using SASS/SCSS, not LESS.*

###Step 1

* **Option 1)** Clone the `/library` directory and add to your Bones theme directly
* **Option 2)** Add the code below to `style.scss` and manually add the individual files to your `/library` directory

<pre>// styles in flexslider.scss
@import "flexslider";`</pre>

###Step 2

After you've done the above, open bones.php in the `/library` folder of your theme.

Scroll to around **Line 128** where the Modernizr script is registered. 

Add the following:

<pre>// flexslider js
wp_register_script( 'flexslider', get_stylesheet_directory_uri() . '/library/js/libs/flexslider/jquery.flexslider-min.js', array(), '2.1', false );</pre>

Scroll to around **Line 156** and add the following underneath the jQuery enqueue:

`wp_enqueue_script( 'flexslider' );`

The above will link the FlexSlider JS into your Bones header.

###Step 3

Lastly, you just need to add the jQuery goodness into your `/library/js/scripts.js` file to make FlexSlider fire.

Around **Line 69** of `scripts.js` you will find the comment *// add all of your scripts here*

Insert the following after that:

<pre>// FlexSlider v2.0
$('.flexslider').flexslider({
		animation: "slide",
		controlsContainer: ".flex-container"
	});</pre>