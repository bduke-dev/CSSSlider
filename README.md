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

## Update HTML to include your images and descriptions

Each image needs its own radio button entry, left and right arrow, and indicator as shown below.

```html
<div id="cssSlider">
    <!--radio button to control going to each page-->
    <input type="radio" name="slider" id="slide1">
    <input type="radio" name="slider" id="slide2">
    <input type="radio" name="slider" id="slide3">
    <input type="radio" name="slider" id="slide4">
    <input type="radio" name="slider" id="slide5">
    <input type="radio" name="slider" id="slide6">
    <input type="radio" name="slider" id="play" checked>
    <input type="radio" name="slider" id="pause">
    <!--each image in the slider-->
    <div id="sliderImages">
        <div><img src="./contents/sliderImages/slide1.png" alt="pure"></div>
        <div><img src="./contents/sliderImages/slide2.png" alt="css"></div>
        <div><img src="./contents/sliderImages/slide3.png" alt="image"></div>
        <div><img src="./contents/sliderImages/slide4.png" alt="slider"></div>
        <div><img src="./contents/sliderImages/slide5.png" alt="no"></div>
        <div><img src="./contents/sliderImages/slide6.png" alt="JavaScript"></div>
    </div>
    <!--optional description for each slide, comment out individually or whole section-->
    <div id="slideDesc">
        <span class="slideText" id="slideText1">
            <p>Pure</p>
        </span>
        <span class="slideText" id="slideText2">
            <p>CSS</p>
        </span>
        <span class="slideText" id="slideText3">
            <p>Image</p>
        </span>
        <span class="slideText" id="slideText4">
            <p>Slider</p>
        </span>
        <span class="slideText" id="slideText5">
            <p>No</p>
        </span>
        <span class="slideText" id="slideText6">
            <p>Java Script</p>
        </span>
    </div>
    <!--each slide needs a left and right arrow-->
    <div id="pageNav">
        <div id="previousArrow">
            <label for="slide6" class="slideL" id="slideL6"></label>
            <label for="slide1" class="slideL" id="slideL1"></label>
            <label for="slide2" class="slideL" id="slideL2"></label>
            <label for="slide3" class="slideL" id="slideL3"></label>
            <label for="slide4" class="slideL" id="slideL4"></label>
            <label for="slide5" class="slideL" id="slideL5"></label>
        </div>
        <div id="playPause">
            <label for="play" class="playPauseBtn" id="playBtn"></label>
            <label for="pause" class="playPauseBtn" id="pauseBtn"></label>
        </div>
        <div id="nextArrow">
            <label for="slide2" class="slideR" id="slideR2"></label>
            <label for="slide3" class="slideR" id="slideR3"></label>
            <label for="slide4" class="slideR" id="slideR4"></label>
            <label for="slide5" class="slideR" id="slideR5"></label>
            <label for="slide6" class="slideR" id="slideR6"></label>
            <label for="slide1" class="slideR" id="slideR1"></label>
        </div>
    </div>
    <!--indicator to show which page is active-->
    <div id="pageIndicators">
        <label for="slide1" class="indicator"><span class="point" id="point1"></span>
        </label>
        <label for="slide2" class="indicator"><span class="point" id="point2"></span>
        </label>
        <label for="slide3" class="indicator"><span class="point" id="point3"></span>
        </label>
        <label for="slide4" class="indicator"><span class="point" id="point4"></span>
        </label>
        <label for="slide5" class="indicator"><span class="point" id="point5"></span>
        </label>
        <label for="slide6" class="indicator"><span class="point" id="point6"></span>
        </label>
    </div>
</div>
```

### Author

This image slider was created by [b.duke](https://bduke.dev/).

#### Licenses

* The slider itself is under the GPLv3 license. Do what you want with it, credit would be nice, but not necessary.
* The play/pause and next/previous arrows are a part of [Google's Material Icons](https://design.google.com/icons/), licensed under
the Apache License Version 2.0.
* The font [TimeBurner](http://www.fontspace.com/nimavisual/timeburner) is licensed as Freeware, free for personal and commercial use.
