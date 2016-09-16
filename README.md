# CSS_Slider
A simple image slider coded completely in CSS. This is done to achieve the most cross compatibility among browsers.
By avoiding the use of JavaScript, the slider does not rely on the device having it, allowing it to work in about all browsers.

## Features
* Automatic timed advancement, each slide is 4s long (described below is how to modify)
* Play/Pause button
* Forward/Previous arrow advancement
* Page indicators that double as page advancement

## Framework
### Slider
The slider is set up to be the entire width of the screen, so 100vw.
The only thing that will need to be changed to meet the need of more or less than 6 images is the width of the whole slider, which is depicted below as 600vw. Simply replace it with the number of images X 100vw.
``` css
/*transition slider size*/
#cssSlider> #sliderImages {
    position: absolute;
    left: 0;
    transition: 2.66666666668s;
    width: 600vw;
```
That takes care of the sizing, the other issue with changing the size is the timing of the transition needs to be chenged. The way the timing works is the show runs for 100% of the chosen time. So, start by picking a duration. For example, I choose 40s.  I did this because I wanted each slide to be shown for 4s. I achieved this timing by pausing each slide for 10% of the 100% of the time (10% of 40s is 4s).

### Author
This image slider was created by [b.duke](https://bmduke1997.github.io/).

#### Licenses
- The slider itself is under the GPLv3 license. Do what you want with it, credit would be nice, but not necessary.
- The play/pause and next/previous arrows are a part of [Google's Material Icons](https://design.google.com/icons/), licensed under 
the Apache License Version 2.0. 
- The font [TimeBurner](http://www.fontspace.com/nimavisual/timeburner) is licensed as Freeware, free for personal and commercial use.
