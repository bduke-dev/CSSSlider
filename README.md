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
The only thing that will need to be changed to meet the need of more or less than 6 images is the width of the whole slider.
'''<p>
/*transition slider size*/
#cssSlider> #sliderImages {
    position: absolute;
    left: 0;
    transition: 2.66666666668s;
    width: 600vw;
  }
</p>
'''
### Author
This image slider was created by [b.duke](https://bmduke1997.github.io/).

#### Licenses
- The slider itself is under the GPLv3 license. Do what you want with it, credit would be nice, but not necessary.
- The play/pause and next/previous arrows are a part of [Google's Material Icons](https://design.google.com/icons/), licensed under 
the Apache License Version 2.0. 
- The font [TimeBurner](http://www.fontspace.com/nimavisual/timeburner) is licensed as Freeware, free for personal and commercial use.
