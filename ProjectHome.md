This script provides an easy to use and integrate HSV color picker.

see the [DEMO](http://www.knallgrau.at/code/colorpicker/demo)

or just [download](http://colorpickerjs.googlecode.com/files/colorpickerjs-1.0.zip) (VERSION 1.0)

The 1.0 release works with prototype 1.6 and script.aculo.us 1.8

## How to implement it ##

  1. include the javascript files in your HEAD
  1. link the colorpicker.css file in your HEAD or Stylesheet
  1. add an input field holding the hex color value (without the leading #)
  1. initialize the ColorPicker

```
<script>
  new Control.ColorPicker("colorFieldName");
</script>
```

## Options ##

swatch ... specify and ID of an element that will be used as a button to open the colorPicker popUp, and will also display the selected color as it's background.

IMAGE\_BASE ... base URL where the images used for the ColorPicker are located (including the trailling slash)

| **Callback** 	| **Description** |
|:--------------|:----------------|
| onOpen 	      | Called after the slider popUp is opened. |
| onClose 	     | Called after the slider popUp is closed. |
| onUpdate 	    | Called whenever a user picked a different color. If the user is dragging the slider, or the colorpicker (circle) the update occures onMouseMove. |
| getPopUpPosition 	| If you want to get control over the position of the colorPicker popUp you may provide this function. ColorPicker expects this function to return an Array with two number values [x,y]. getPopUpPosition will receive the open event (click) as the only argument. You may access all values and methods of ColorPicker via this. |

## Full Example ##

```
<form>
<p>color 1 #<input type="text" id="colorfield1" value="FF33FF"></p>
<p>color 2 #<input type="text" id="colorfield2" value="CC3366"></p>
<p>color 3 #<input type="text" id="colorfield3" value="66FF66"></p>
<p>color 4 #<input type="text" id="colorfield4" value="339900"> <button style="width: 1.5em; height: 1.5em; border: 1px outset #666;" id="colorbox4" class="colorbox"></button></p>
</form>

<script type="text/javascript">
["1", "2", "3"].each(function(idx) {
  new Control.ColorPicker("colorfield" + idx, { IMAGE_BASE : "img/" });
});
new Control.ColorPicker("colorfield4", { "swatch" : "colorbox4" });
</script>
```

WARNING: You must not call "new Control.ColorPicker()" unless you closed all wrapping block elements around the form (i.e. divs) - otherwise you will get an exception in IE6/7. If you need to so, use

```
Event.observe(window, "load", function() { 
  new Control.ColorPicker("colorfield4", { "swatch" : "colorbox4" })
});
```

## STYLESHEET ##

To make the ColorPicker work like it should, you also need to include the colorpicker.css file to your page.

This file defines the appearance of the ColorPicker PopUp and is using the following keys:

  * #colorpicker ... container for popUp (adapt width, hight, background to your needs)
  * #colorpicker-hue-slider ... slider container (adapt width and height to your needs)
  * #colorpicker-hue-bg-img ... slider bg
  * #colorpicker-hue-thumb ... slider handle
  * #colorpicker-div ... container for color picker area (adapt width, height to your needs)
  * #colorpicker-bg ... color picker area
  * #colorpicker-selector ... circle, that indicates the current color
  * #colorpicker-footer ... container for OK button
  * #colorpicker-value ... span containing the value input, prefixed by '#'
  * #colorpicker-value-input ... input.text containing the current color value (without the #)
  * #colorpicker-okbutton ... the blue OK button

## Who is using it ##

  * [Twitter](http://www.twitter.com) (Settings > [Design](http://twitter.com/account/profile_settings))
  * [blogr.com](http://www.blogr.com) For customizing the design.
  * [madmimi.com](http://madmimi.com) Customize settings
  * [Booktour](http://booktour.com) For a widget "follow this author: on my website"
  * [SuperSaaS](http://www.supersaas.com) For customizing calender layouts

Please drop me a line, if you are using colorpicker.js (matthias.platzer AT knallgrau.at)

## Credits ##

written by Matthias Platzer AT [knallgrau.at](http://www.knallgrau.at)

inspired by [YUI Color Picker script](http://www.dynamicdrive.com/dynamicindex11/yuicolorpicker/).

implemented using [script.aculo.us](http://script.aculo.us), [YUI Util color.js](http://developer.yahoo.com/yui/) and some more [EasyRGB math](http://www.easyrgb.com/math.html)