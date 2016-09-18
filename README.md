# CSS_Slider
A simple image slider coded completely in CSS. This is done to achieve the most cross compatibility among browsers.
By avoiding the use of JavaScript, the slider does not rely on the device having it, allowing it to work in about all browsers.

## Features
* Automatic timed advancement, each slide is 4s long (described below is how to modify)
* Play/Pause button
* Forward/Previous arrow advancement
* Page indicators that double as page advancement

## Framework
#### Provides an explanation of how to add or subtract images and adjust the other pieced of the framework to accoidate the change
### Radio Buttons
The radio buttons, which are not visible, are what handle the play, pause, and advancement. You need to have a radio button for each page, as well as, the play and pause which should not be changed. To add a new radio buttons just place it under the others with an id of the slide number like othe other ones. This is housed in the HTML document directly under the opening cssSlider div statement. 
### Slider
To add images to the slider simply insert them into the HTML document in the sliderImages div. The only thing that will need to be changed to meet the need of more or less than 6 images is the width of the whole slider, which is depicted below as 600vw. Simply replace it with the number of images X 100vw.
``` css
/*transition slider size*/
#cssSlider> #sliderImages {
    position: absolute;
    left: 0;
    width: 600vw;
```
### Next/Previous Arrows
To add or remove arrows to complement the change in images you need to change two references. Each radio button has two corresponding arrows, a next and a previous. In the pageNav div look in both the previousArrow and nextArrow. The previous arrows are the left arrows and next is the right arrows. Either inset a new arrow, naming like the others except with the for="the id of the new radio button"
## Animations and Manual Advancement
#### Provides an explanation of how to configre animations and manual advancement of features
### Slider
The timimg transitions works in percents of time. The way the timing works is the show runs for 100% of the chosen time. So, start by picking a duration. For example, I choose 40s.  I did this because I wanted each slide to be shown for 4s. I achieved this timing by pausing each slide for 10% of the 100% of the time (10% of 40s is 4s). Any percent can be used, however 10% is easiest to work with. 

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
For the manual page advancement we say, whenever its corresponding radio button is selected margin over x. In mine if the first is selected it will margin over 0, if the second -100vw, and so on untill there are no more pictures. 
```css 
/********** MANUAL PAGE ADVANCEMENT **********/

#cssSlider> #slide1:checked~ #sliderImages {
    margin-left: 0;
}

#cssSlider> #slide2:checked~ #sliderImages {
    margin-left: -100vw;
}
```
### Next/Previous Arrows
The next and previous arrows run on a timer similar to the slider. The gist of how it works is, as time progresses, using keyframe animatios, the corresponging arrows are brought from a z-index of -1 to 15 when on that arrow's page. When the slide show is paused on the other hand, whichever page is avtive tells its corresponding arrows to be a z-index of 15.
To figure out the timing of the animation is rather simple, take the percent of time used for the first slide to the start of the second. This is when the arrow is visible, z-index 15.  Next, take the decimal right after the ending time and go to 100%. This is when the arrow is not visible, z-index -1. As in my exaple, my first slide starts at 0% and the second starts at 16.6666666667%, this is when I will show the arrow. Then going from 16.66666666668% to 100% I will not show the arrow.
```css
/*arrows*/
/*this hows only the code for keyframes, not all browers suppost code for keyframes, so 
besure to update the code for @-webkit-keyframes arrows also*/
@keyframes arrows {
    0%,
    16.6666666667% {
        z-index: 15;
    }
    16.66666666668%,
    100% {
        z-index: -1;
    }
}
```
Now the the other part of the animation, is the actual timing of the animation. As there are multiple arrows, they each need a little bit of timing so that they do not all diaplay at the same time. The syntax for that is ``` (animation or -webkit-animation): (time of whole show in ms) infinite (delay start of animation) ``` To figure out the delay, take the time of the show in ms and divide by the number of images. Start the fitst arrow with a delay of 0ms, and increase them by the time we just found. In mine that was 40000/6 = 6666.6666666667ms. 
```css
/*STARTING ARROW ANIMATION, FOR WHICH TO BE ON TOP*/
#cssSlider> #play:checked~ #pageNav> #previousArrow> #slideL6,
#cssSlider> #play:checked~ #pageNav> #nextArrow> #slideR2,
#cssSlider> #pause:checked~ #pageNav> #previousArrow> #slideL6,
#cssSlider> #pause:checked~ #pageNav> #nextArrow> #slideR2 {
    -webkit-animation: arrows 40000ms infinite 0ms;
    animation: arrows 40000ms infinite 0ms;
}

#cssSlider> #play:checked~ #pageNav> #previousArrow> #slideL1,
#cssSlider> #play:checked~ #pageNav> #nextArrow> #slideR3,
#cssSlider> #pause:checked~ #pageNav> #previousArrow> #slideL1,
#cssSlider> #pause:checked~ #pageNav> #nextArrow> #slideR3 {
    -webkit-animation: arrows 40000ms infinite 6666.6666666667ms;
    animation: arrows 40000ms infinite 6666.6666666667ms;
}
```
As for when the animation is not running is even easier. Whichever radio button is active will bring the corresponding arrows to a z-index of 15. So, for mine if the show animation is not running and the user is manually navigating the images the first page would bring the previous page 6 arrow and next page 2 arrow to the top. For this see the section in the code titiled ```/*WHICH ARROW SHOULD BE ON TOP*/``` in the ```/********** NEXT SLIDE ARROW NAVIGATION **********/```.
### Page Indicators
The page indicators are exactly like the Next/Previous Arrows with one small modification. The difference is in the animation percents and the fact that we change its color instead of z-index. The animation is from 0% to the start time of the second image rounded down to the nearest percent. Then from the next percent to 100%. So, mine was 0% to 16%, then 17% to 100%. This is so there is time for the indicator dots to fade in and out, allowing for a smother transition. All you need to do is set time percents like the Arrows, except in the ```/*page indicators*/``` under ```/********** ANIMATIONS **********/```
For the manual lighting of the indicator dot is exactly like the Next/Previous Arrows. It is just a copy of the code, but it selects the dots instead of the arrrows. The code can be vieded in ```/*STARTING PAGE INDICATOR WHICH TO BE LIT ANIMATION*/``` under ```/********** SLIDE INDICATORS **********/```.
### Slider Text Box
The Slider Text Box is the slide's description in the bottom left corner. It functions a lot like the Next/Previous Arrows, with the only major modificaiton to the animation percent timing. The percents are a bit inexact in the fact that you just have to play with them untill it looks right. To get the base percents take the percent of time used for the first slide to the start of the second. Mine was 0% to 16.6666666667%. Then just plug them in the framework, described below and play aroud untill it looks good. For the actial timing of the animations refer to Next/Previous Arrows, and put the code in ```/*TEXT BOX ANIMATION*/``` under ```/********** SLIDER TEXT **********/```.
```css
/*text box*/
/*this hows only the code for keyframes, not all browers suppost code for keyframes, so 
besure to update the code for @-webkit-keyframes arrows also*/
@keyframes textBoxBounce {
    /*was 0% to 16.6666666667%, but after modification this is what worked for me*/
    0.6927083333333334%,
    15.963958333333334% {
        opacity: 1;
        z-index: 2;
        visibility: visible;
        -webkit-transform: translateY(10px);
        transform: translateY(10px);
    }
    /*was 0% to 16.6666666667%, but after modification this is what worked for me*/
    0.9895833333333334%,
    15.667083333333334% {
        opacity: 1;
        z-index: 2;
        visibility: visible;
        -webkit-transform: translateY(0px);
        transform: translateY(0px);
    }
    /*was 17%, but after modification this is what worked for me*/
    17.65625% {
        opacity: 0;
        z-index: 2;
        visibility: hidden;
        -webkit-transform: translateY(-100px);
        transform: translateY(-100px);
    }
    /*just needs to be a decimal percent difference from the previous*/
    17.66625%,
    100% {
        z-index: 0;
    }
}
```
As for the manual control of the text box, whichever radio button is selected brings its corresponding text box forward. This can be viewed in ```/*BRING THE TEXT FORWARD ON ITS PAGE*/``` under ```/*TEXT BOX ANIMATION*/``` under ```/********** SLIDER TEXT **********/```.

### Author
This image slider was created by [b.duke](https://bmduke1997.github.io/).

#### Licenses
- The slider itself is under the GPLv3 license. Do what you want with it, credit would be nice, but not necessary.
- The play/pause and next/previous arrows are a part of [Google's Material Icons](https://design.google.com/icons/), licensed under 
the Apache License Version 2.0. 
- The font [TimeBurner](http://www.fontspace.com/nimavisual/timeburner) is licensed as Freeware, free for personal and commercial use.
