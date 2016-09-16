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
    width: 600vw;
```
That takes care of the sizing, the other issue with changing the size is the timing of the transition needs to be chenged. The way the timing works is the show runs for 100% of the chosen time. So, start by picking a duration. For example, I choose 40s.  I did this because I wanted each slide to be shown for 4s. I achieved this timing by pausing each slide for 10% of the 100% of the time (10% of 40s is 4s). Any percent can be used, however 10% is easiest to work with. 

Now that you have chosen a pause percent you multiply it by the number of images, making sure that it dows not excede 100%. So, going on my exaple, I have 6 images and each pauses for 10% of the time, meaning that 60% of the time the slider is not moving. This leaves 40% of the time to actually have transitions between each image. Next we need to calculate the transition percent between each image. This is achieved by taking the 40% achieved in teh step before and dividing it between our 6 images, producing 6.6666666667% of time to transition from one image to the next (note it is very important to use as many decimal places as possible so no transitions can get off over time). One last thing we need to do is use the 6.6666666667% we found and multiply 40s by it. We do this so we can fid how log the image switch duration is, so we can use that time when manually switching between images (40 X 6.6666666667% is transition: 2.66666666667s). Using all of the numbers we calculated, here's the actual places you will use it (note I am excluding the lines already stated above).
``` css
/*transition slider size*/
#cssSlider> #sliderImages {
    /*animation parameters*/
    -webkit-animation-name: slider;
    -webkit-animation-duration: 40s; /*the chosen time*/
    -webkit-animation-timing-function: ease-in-out;
    -webkit-animation-iteration-count: infinite;
    animation-name: slider;
    animation-duration: 40s; /*the chosen time*/
    animation-timing-function: ease-in-out;
    animation-iteration-count: infinite;
    /*this is the time to transition between images
    when using the arrows*/
    transition: 2.66666666667s;
}

/*slider*/
/*this hows only the code for keyframes, not all browers suppost code for keyframes, so 
besure to update the code for @-webkit-keyframes slider, @keyframes slider-ie, 
and @-webkit-keyframes slider-ie*/
@keyframes slider {
    /*from 0% of time to 10% of time stay on image 1*/
    0%,
    10% {
        transform: translateX(0);
    }
    /*take the ending percent, 10% in this case, and add 6.6666666667%. This is the next start time*/
    /*now add 10%, how long each page is paused*/
    /*also, besure to increment the transform: translateX() by -100vw each time*/
    /*follow this pattern untill 100% is reached*/
    16.6666666667%,
    26.6666666667% {
        transform: translateX(-100vw);
    }
    33.3333333333%,
    43.3333333333% {
        transform: translateX(-200vw);
    }
```

### Author
This image slider was created by [b.duke](https://bmduke1997.github.io/).

#### Licenses
- The slider itself is under the GPLv3 license. Do what you want with it, credit would be nice, but not necessary.
- The play/pause and next/previous arrows are a part of [Google's Material Icons](https://design.google.com/icons/), licensed under 
the Apache License Version 2.0. 
- The font [TimeBurner](http://www.fontspace.com/nimavisual/timeburner) is licensed as Freeware, free for personal and commercial use.
