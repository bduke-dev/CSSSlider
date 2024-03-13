# CSS_Slider

A simple image slider coded completely in CSS. This is done to achieve the most cross compatibility among browsers.
By avoiding the use of JavaScript, the slider does not rely on the device having it, allowing it to work in about all browsers.
The CSS Slider uses SCSS as a pre-processor, this allows users to easily change a few variables to have the slider suit their needs.

## Features

* Automatic timed advancement
* Play/Pause button
* Forward/Previous arrow advancement
* Page indicators that double as page advancement
* Easy configuration through a variables scss file

## Framework

#### Provides an explanation of how to add or subtract images and adjust the other pieces of the framework to accommodate the change

## Declaration

In the scss folder there is a file entitled "_variables.scss," this is where the magic happens.
Below are the configurable variables that allow you to match the slider to your needs.

```scss
$FONT_PATH: "timeburner.ttf";
$ARROW_PREVIOUS_PATH: "./icons/previous.svg";
$ARROW_NEXT_PATH: "./icons/next.svg";
$ARROW_PLAY_PATH: "./icons/play.svg";
$ARROW_PAUSE_PATH: "./icons/pause.svg";

$SLIDER_BACKGROUND: #5b5b5b; // background color of slider when images are too small
$INDICATOR_BACKGROUND_COLOR: #abb7b7; // color of indicators at the bottom of the slider
$INDICATOR_POINT_COLOR: #f2f1ef; // color of the indicator when lit
$DESC_BOX_COLOR: #abb7b7; // color of the description box
$DESC_BOX_TEXT_COLOR: black; // color of the text in the description box

$ASPECT_RATIO: 0; // either set this or height
$SLIDER_WIDTH: 100%; // always set the width
$SLIDER_HEIGHT: 100%; // aspect ration takes precedence over height
$SLIDE_COUNT: 6;
$SLIDE_TIME: 40; // in seconds
$SLIDE_PAUSE_PERCENT: 10; // percent of time paused on each image; $SLIDE_COUNT * $SLIDE_PAUSE_PERCENT !> 100
$BTN_OPACITY: 0.7; // opacity of play/pause and advancement buttons

```

### Radio Buttons

### Next/Previous Arrows

### Page Indicators

### Slider Text Box

## Animations and Manual Advancement

### Slider

### Next/Previous Arrows

### Page Indicators

### Slider Text Box

### Author

This image slider was created by [b.duke](https://bduke.dev/).

#### Licenses

* The slider itself is under the GPLv3 license. Do what you want with it, credit would be nice, but not necessary.
* The play/pause and next/previous arrows are a part of [Google's Material Icons](https://design.google.com/icons/), licensed under
the Apache License Version 2.0.
* The font [TimeBurner](http://www.fontspace.com/nimavisual/timeburner) is licensed as Freeware, free for personal and commercial use.
