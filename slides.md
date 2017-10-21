<!-- 
Title: Level up your designer to developer SVG Workflow
Details:
* The importance of understanding the capabilities of SVGs and how developers and designers can improve the quality of designs created in the browser
* Through an understanding of SVG capabilities you will know how each layer of Illustrator is rendered through SVGs in the browser
* You won’t learn about SVG font icons; you WILL learn about how to efficiently export SVGs so your team won’t curse your name. With SVGs you can render each design layer directly in the browser
* Apply filters, lighting effects, gaussian blur, and animations, all directly through the use of this file format. Get exactly what you want in the browser
Plus a few favorite tips/tricks about SVG elements and attributes
-->
<svg class="svg svg-logo" style="max-width: 400px;" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 106.7 104" enable-background="new 0 0 106.7 104" xml:space="preserve">
  <polygon class="svg-outline logo-top-hex" id="logo-top-right" fill="#661A38" points="104,31.5 104,73 74.6,102.3 33.1,102.3 3.8,73 3.8,31.5 33.1,2.1 74.6,2.1 "/>
  <polygon class="svg-outline  bottom-R" id="bottom-R" fill="#7E1542" points="72,102.3 33.7,102.3 33.7,53 34.4,53.9 34.6,54.1 68.6,98 "/>
  <polygon class="svg-outline logo-left-hex" id="logo-left-hex" fill="#B22D70" points="33.7,2.1 33.7,102.3 33.1,102.3 3.8,73 3.8,31.5 33.1,2.1 "/>
  <rect class="svg-outline logo-top-R" id="logo-top-R" x="33.7" y="2.1" fill="#7E1542" width="35.099" height="51.7"/>
  <polygon class="svg-outline logo-bottom-right-R" id="logo-bottom-right-R" fill="#AA1D4E" points="92.299,84.7 74.6,102.3 71.2,102.3 68.6,98.8 34.6,54.1 34.4,53.9 33.7,53 34.6,53 68.6,53.5 68.799,53.8 "/>
</svg>

Note:
Industry professionals, work trip conference, multiple speakers, I want my audience to feel that I am knowledgable. I was kind of ill prepared in the last talk. Organization. Think about reading the room. They will likely be pretty hyped. What is the room going to be like? If people are in a really great mood, match that mood. Talking about something to break the ice in the room. I don't know about you guys I nerd out about and I'm here to teach you guys about SVGs. 30-35 mins You're not their favorite band, they don't know all your songs. How can you bridge the gap between rock star and being a teacher?


# Down the SVG Rabbit Hole
<!-- Optimizing the design to front end development workflow -->
### __[@robyn_larsen](http://twitter.com/robyn_larsen)__
### [r@robynlarsen.ca](http://robynlarsen.ca)
Note:
Good Morning everyone, thank you so much for joining today, I am so excited to be here and see so many familiar faces in the audience. FITC is one of my favorite tech events to attend each year in Toronto. Did everyone head to the party last night? How much did you love Anouk's dress that pours shots?


<div class="grid grid--middle">
  <!-- One -->
  <div class="column grid-1of4">
    <svg id="svg svgBadge" class="svg svg-glow" style="fill:#61bde3;" viewBox="0 0 137.3 137.3" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
      <use xlink:href="#svgBadge" />
    </svg>
  </div>
  <!-- Two -->
  <div class="column grid-1of4">
    <svg style="fill:#61bde3;" viewBox="0 0 137.3 137.3" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
      <defs>
        <!-- Glowing Pulse Animation -->
        <filter id="glow">
          <!--Blur effect-->
          <feGaussianBlur stdDeviation="7" result="spec1">
            <animate attributeName="stdDeviation"
                     from="0" to="7"
                     dur="1s"
                     repeatCount="indefinite"
                     values="0; 7; 7; 0;"
                     keyTimes="0; 0.45; 0.75; 1"
                     keySplines=".42 0 1 1;
                                 0 0 .59 1;
                                 .42 0 1 1;
                                 0 0 .59 1;
                                 .42 0 1 1;
                                 0 0 .59 1;
                                 .42 0 1 1;
                                 0 0 .59 1;"/>
          </feGaussianBlur>
          <!--Composition of inputs-->
          <feComposite in="SourceGraphic" in2="spec1" operator="arithmetic" k1="0" k2="1" k3="1" k4="0" />
        </filter>
      </defs>
      <use xlink:href="#svgBadge" filter="url(#glow)" />
    </svg>
  </div>
  <!-- Three -->
  <div class="column grid-1of4">
    <svg viewBox="0 0 137.3 137.3">
      <use xlink:href="#svgBadge" filter="url(#spotlight)" />
    </svg>
  </div>
  <!-- Four -->
  <div class="column grid-1of4">
    <svg class="svg" style="fill:#61bde3;" viewBox="0 0 137.3 137.3" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" >
      <use xlink:href="#svgBadge" filter="url(#spotlight)"/>
    </svg>
  </div>
  <!-- Five -->
  <div class="column grid-1of4">
    <svg viewBox="0 0 137.3 137.3">
      <use xlink:href="#svgBadge" filter="url(#spotlight-moving)" />
    </svg>
  </div>
</div>
<p class="cite">Source: [Progaming League](http://progamingleague.com) - Millennial eSports</p>
<p class="cite">CodePen Collection: https://codepen.io/collection/nGzZxb/</p>
<p class="cite">Slides: robynlarsen.ca/speaking/svg/</p>
Note:
BOOOM! This is what we are here to learn. These are some of my favorite inline SVG filters.

I don't know everything about this yet because there is so much meat to this lasagna. I am going to teach you the things I have learned so far to make your life easier.
I'm not smartest person in the room *point to her*, I don't want to call out any names or anything. You're going to see alot of information, don't worry about writing this down. I will send out a link to the slides afterwards. By the end of talk I'm going to turn you all into uber SVG nerds.


<!-- .slide: data-background="linear-gradient(-45deg, #661A38 0%, #D6BB92 100%)" -->
![favorites](assets/images/favorites-1.jpg)
***
former nuclear engineer turned front end developer

_aka major nerd and amateur gnar schredder_
***
![favorites](assets/images/favorites-2.jpg)
Note: Former nuclear engineer turned front end developer. If you're ever in Revelstoke, hit me up on twitter, that's usually where I can be found in my down time each winter. The nerdiest thing I've ever done, is work on reactors in the Hanain region of China. You want to know more, that's what the google machine is for.


<!-- .slide: data-background-image="assets/images/zona.png" -->


<!-- .slide: data-background="#2A5A8A" -->
<img style="background-color: transparent; border-color: transparent; box-shadow: none;" src="assets/images/phuse_logo_white.png" alt="">
<p>phuse.ca</p>



# Content
<ul>
  <li>
    <p><span class="highlight"><strong>SVGs for Designer</strong></span> - Project goals and where we can take it</p>
  </li>
  <li>
    <p><span class="highlight"><strong>Collaboration: Exporting SVG</strong></span> - The bones of our SVGs</p>
  </li>
  <li>
    <p><span class="highlight"><strong>SVG code for Beginner</strong></span> - Export and optimization methods</p>
  </li>
  <li>
    <p><span class="highlight"><strong>FED SVG Workflow</strong></span> - The cost of building it right</p>
  </li>
  <li>
    <p><span class="highlight"><strong>Advanced SVG</strong></span> - The fun filters that nobody knows about</p>
  </li>
</ul>
Note:
I am working under the assumption you are either a designer or developer that already works with SVGs in production scale applications.
First we will start with SVGs for designers, idenitfy project goals and where we can take it. That will lead to us to the bones of our SVGs and collaboration. Down into exporting and optimization methods.
We will discuss the front end development svg workflow, the cost of building it right.
And then the sexy bits, advanced svgs, the fun inline svg filters.

The acciles heel and each have their super powers. Think of your different segments as your super heros. The only way they defeat the nerd king. A great presentation is like a good standup comdy. Turn that smarts into relatable. Make this talk invaluable to the nerd king. Out of our super heros, what our strengths of the super heros.



# SVGs for Designers
*Determine your goals:*
Stagnant or Animated?

<div class="grid">
  <div class="column grid-1of4">
    <svg class="svg" style="fill:#61bde3;" viewBox="0 0 137.3 137.3" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" >
      <use xlink:href="#svgBadge"/>
    </svg>
  </div>
  <div class="column grid-1of4">
    <svg style="fill:#61bde3;" viewBox="0 0 137.3 137.3" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" filter="url(#glowingPulse)">
          <defs>
            <!-- Glowing Pulse Animation -->
            <filter id="glowingPulse">
              <!--Blur effect-->
              <feGaussianBlur stdDeviation="7" result="spec2">
                <animate attributeName="stdDeviation"
                         from="0" to="10"
                         dur="1s"
                         repeatCount="indefinite"
                         values="0; 10; 10; 0;"
                         keyTimes="0; 0.45; 0.75; 1"
                         keySplines=".42 0 1 1;
                                     0 0 .59 1;
                                     .42 0 1 1;
                                     0 0 .59 1;
                                     .42 0 1 1;
                                     0 0 .59 1;
                                     .42 0 1 1;
                                     0 0 .59 1;"/>
              </feGaussianBlur>
              <!--Composition of inputs-->
              <feComposite in="SourceGraphic" in2="spec2" operator="arithmetic" k1="0" k2="1" k3="1" k4="0" />
            </filter>
          </defs>
          <use xlink:href="#svgBadge"/>
        </svg>
  </div>
</div>
Note:
<!-- 01. Will this SVG include a complex animation?
- Do you want to control the hover states?
- Do you want the ability to control your SVGs in the DOM? -->
Is your asset going to be a still or give life to the element in the DOM such as hover effects or animations? This will determine whether you decide to go the inline route and how the SVGs are exported.


# SVGs for Designers
Communicate. Communicate early.
Note:
Sharing your project goals is really important for developers to know. This determines how the development team handles SVG assets and will also determine how they setup task runners. We've all been there in crunch mode.


# SVG Assets
Sketch and Illustrator

<img style="max-width: 200px;" src="assets/images/code-examples/sketch.jpg" alt="">
<img style="max-width: 200px;" src="assets/images/illustrator.png" alt="">
Note:
  I understand there are multiple ways to export SVGs. For the sake of time I am only going to go through exporting SVGs from Sketch because it is becoming an industry standard tool.


# Exporting Assets
## Illustrator
<img style="max-width: 200px;" src="assets/images/illustrator.png" alt="">

[Exporting SVG Illustrator for <br> Responsive Web Design in 2 minutes](https://helpx.adobe.com/illustrator/how-to/export-svg.html)
Note:
If you're interested in Illustrator I have linked a tutorial in my slide deck that you can find online.
  // Out of the designers in the room, who is using sketch and who is using illustrator?


<!-- .slide: data-background="assets/images/code-examples/sketch_illustrator_messy_svg.png" -->
Note:
This thing. Look at this ugly piece of code. By default exported SVG code in Sketch is really messy.


# SVG Assets
## Sketch
<img style="max-width: 200px;" src="assets/images/code-examples/sketch.jpg" alt="">
1. By default, exported SVG code in Sketch is really messy

```javascript
  defaults write com.bohemiancoding.sketch3 
  exportCompactSVG -bool yes
```

Source: <cite>[robots.thoughtBot.com](https://robots.thoughtbot.com/organized-workflow-for-svg)</cite>
Note:
From a development/semantic html standpoint the code exported by Sketch is usually quite complex and deeply nested. This will change the way Sketch exports the files, making them more compact and web-ready (ish). You'll need to restart your computer for this to take effect.


## Export SVGs in Sketch
By default the Sketch canvas is infinite

1) Add SVGs to their own artboards prior to exporting

<div class="grid grid--middle">
  <img src="assets/images/sketch_artboard.png" alt="">
</div>


## Export SVGs in Sketch
2) Select svg layers (can't use dotted arrow select, will need to select in the layers panel)

<div class="grid grid--middle">
  <img src="assets/images/sketch_select.png" alt="">
</div>


## Export SVGs in Sketch
3) Flatten - removes the inline transform/translate/rotate attributes

<div class="grid grid--middle">
  <img src="assets/images/sketch_flatten.png" alt="">
</div>


<!-- .slide: data-background="assets/images/code-examples/compared_svg_code.png" -->
Note:
On the right is the clean semantic code we expect from HTML. On the left is what Sketch generally gives you.


## Sketch Workflow
01. Name your layers - it translates to an id
- add SVGs to their own artboard
- Use `icon-` & `logo-` prefix for svg icons
- Try to add all simple icons to one svg file
  - Utilize `<use>` element (discussed later)
- Reduce layer nesting to prevent complex inline SVG nesting
- Flatten and merge layers
- Reduce the complexity of shapes and reduce points - will reduce `<path>` elements
Note:
Later in the presentation we will dive into the <use> element later
Think about how you're saying this. Lots of word economy.



### SVG Code for Beginners
-----
```html
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<svg width="33px" height="33px" viewBox="0 0 33 33" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
    <!-- Generator: Sketch 3.4.2 (15857) - http://www.bohemiancoding.com/sketch -->
    <defs></defs>
    <g id="Welcome" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd" stroke-linecap="round" stroke-linejoin="round">
        <g id="Contact-Mobile-Portrait" transform="translate(-263.000000, -22.000000)" stroke="#FFFFFF">
            <g id="Mobile-Menu-+-Page-1" transform="translate(-2333.000000, 0.000000)">
                <g id="Mobile-Menu">
                    <g id="Group" transform="translate(2333.000000, 0.000000)">
                        <g id="Stroke-5-+-Stroke-7" transform="translate(263.000000, 22.000000)">
                            <g>
                                <path d="M0.825,0.825 L32.175,32.175" id="Stroke-5"></path>
                                <path d="M32.175,0.825 L0.825,32.175" id="Stroke-7"></path>
                            </g>
                        </g>
                    </g>
                </g>
            </g>
        </g>
    </g>
</svg>```
-----
Note:
- width/height
- transform
- rotate
- ids/layers


### SVG Code for Beginners
-----
```html
<svg viewBox="0 0 33 33">
  <g>
    <path d="M0.825,0.825 L32.175,32.175" id="Stroke-5"></path>
    <path d="M32.175,0.825 L0.825,32.175" id="Stroke-7"></path>
  </g>
</svg>```
-----



# SVG Optimization
#### To optimize or not to optimize

Go back to your project goals.
Note:
This really depends on your goals. If you want to do complex SVG animations I generally never optimize the SVG and will instead do it by hand. This can be tedious but I found it to be extremely helpful for complex SVGs. It also avoids any browser compatibility mishaps.


# [SVGO](https://github.com/svg/svgo)
## SVG Optimization
Node.js based tool for optimizing SVG graphical files

-----
` npm install -g svgo`

` svgo --pretty folder/`

` svgo --pretty file.svg`

` svgo --pretty file.svg file.min.svg`

-----
Note:
`--pretty` creates a more readble svg
Use the insight explain it. You can optimize an entire folder, single files, and reassign optimized files.


# Front end development
## SVG Workflow
At this point we have been given the assets and optimized what we wanted to in the SVG code.

Defaults - forces the svg to only take up 100% of the parent container
``` css
svg, img, iframe, video {
  max-width: 100%;
}
```


# FED SVG Workflow
01. Name your layers - it translates to an inline id
- Use `icon-` & `logo-` prefix for svg icons & logos, respectively
- Remove inline `width` and `height` attributes
- Try to add all simple icons to one svg file
  - Utilize `<use>` element
- `svgo --pretty icons/`
- Other `svgo` parameters include `--addClassesTOSVGElement -s=svgClass`



# Advanced SVG
## [Filters](https://www.w3.org/TR/SVG/filters.html), Lighting Effects & Gaussian Blur

For all you math nerds, you will see standard deviation, keySplines, cubic bezier and k-not values.
Note:
One day commuting on the train, I started exporing the W3 SVG filter effects. I went through all of the filters I found interesting and tried to find a way to integrate them into a production project.


# Filters
<!-- .slide: data-background="#000000" -->
<div class="grid grid--middle">
  <div class="grid-1of2 column" style="float:left;">
    <ol>
      <li><a href="https://www.w3.org/TR/SVG/filters.html#feGaussianBlurElement" target="_blank">feGaussianBlur</a></li>
      <li><a href="https://www.w3.org/TR/SVG/filters.html#fePointLightElement" target="_blank">fePointLight</a></li>
      <li><a href="https://www.w3.org/TR/SVG/filters.html#feSpotLightElement" target="_blank">feSpotLight</a></li>
      <li><a href="https://www.w3.org/TR/SVG/filters.html#feOffsetElement" target="_blank">feOffset</a></li>
      <li><a href="https://www.w3.org/TR/SVG/filters.html#feSpecularLightingElement" target="_blank">feSpecularLighting</a></li>
      <li><a href="https://www.w3.org/TR/SVG/filters.html#feDistantLightElement" target="_blank">feDistantLight</a></li>
    </ol>
  </div>
  <div class="grid-1of2 column">
    <div class="grid grid--middle">
      <!-- One -->
      <div class="column grid-1of4">
        <svg class="svg svg-glow" style="fill:#61bde3;" viewBox="0 0 137.3 137.3" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
          <use xlink:href="#svgBadge" />
        </svg>
      </div>
      <!-- Two -->
      <div class="column grid-1of4">
        <svg style="fill:#61bde3;" viewBox="0 0 137.3 137.3" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" filter="url(#glow)">
          <defs>
            <!-- Glowing Pulse Animation -->
            <filter id="glow">
              <!--Blur effect-->
              <feGaussianBlur stdDeviation="7" result="spec1">
                <animate attributeName="stdDeviation"
                         from="0" to="7"
                         dur="1s"
                         repeatCount="indefinite"
                         values="0; 7; 7; 0;"
                         keyTimes="0; 0.45; 0.75; 1"
                         keySplines=".42 0 1 1;
                                     0 0 .59 1;
                                     .42 0 1 1;
                                     0 0 .59 1;
                                     .42 0 1 1;
                                     0 0 .59 1;
                                     .42 0 1 1;
                                     0 0 .59 1;"/>
              </feGaussianBlur>
              <!--Composition of inputs-->
              <feComposite in="SourceGraphic" in2="blur1" operator="arithmetic" k1="0" k2="1" k3="1" k4="0" />
            </filter>
          </defs>
          <use xlink:href="#svgBadge" />
        </svg>
      </div>
      <!-- Three -->
      <div class="column grid-1of4">
        <svg viewBox="0 0 137.3 137.3">
          <use xlink:href="#svgBadge" filter="url(#spotlight)" />
        </svg>
      </div>
      <!-- Four -->
      <div class="column grid-1of4">
        <svg class="svg" style="fill:#61bde3;" viewBox="0 0 137.3 137.3" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" >
          <use xlink:href="#svgBadge" filter="url(#spotlight)"/>
        </svg>
      </div>
      <!-- Five -->
      <div class="column grid-1of4">
        <svg viewBox="0 0 137.3 137.3">
          <use xlink:href="#svgBadge" filter="url(#spotlight-moving)" />
          <!-- <use xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="#svgBadge" filter="url(#glow)"></use> -->
        </svg>
      </div>
    </div>
  </div>
</div>

Note:
On this page you will see a number of filters all applied to the same 2-D SVG. There are a number of great filter examples on the W3 site. If you're looking for a few more complex filter effects.


<div class="grid grid--middle">
  <div class="column grid-1of3">
    <svg class="svg svg-glow" style="fill:#61bde3;" viewBox="0 0 137.3 137.3" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
      <use xlink:href="#svgBadge"/>
    </svg>
  </div>
  <div class="column grid-2of3">
    <p>Default <code>path</code> with fill color</p>
  </div>
</div>
```html
<svg class="svg svg-glow" style="fill:#61bde3;"
      viewBox="0 0 137.3 137.3">
  <use xlink:href="#svgBadge"/>
</svg>
```


<div class="grid grid--middle">
  <div class="column grid-1of3">
    <svg style="fill:#61bde3;" viewBox="0 0 137.3 137.3" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" filter="url(#glowingPulse)">
      <defs>
        <!-- Glowing Pulse Animation -->
        <filter id="glowingPulse">
          <!--Blur effect-->
          <feGaussianBlur stdDeviation="7" result="spec2">
            <animate attributeName="stdDeviation"
                     from="0" to="10"
                     dur="1s"
                     repeatCount="indefinite"
                     values="0; 10; 10; 0;"
                     keyTimes="0; 0.45; 0.75; 1"
                     keySplines=".42 0 1 1;
                                 0 0 .59 1;
                                 .42 0 1 1;
                                 0 0 .59 1;
                                 .42 0 1 1;
                                 0 0 .59 1;
                                 .42 0 1 1;
                                 0 0 .59 1;"/>
          </feGaussianBlur>
          <!--Composition of inputs-->
          <feComposite in="SourceGraphic" in2="spec2" operator="arithmetic" k1="0" k2="1" k3="1" k4="0" />
        </filter>
      </defs>
      <use xlink:href="#svgBadge"/>
    </svg>
  </div>
  <div class="column grid-2of3">
    <code>feComposite, animate, feGaussianBlur</code>
    <input style="width: 100%;" id="slider1" type="range" min="0" max="10" step="1" />
  </div>
</div>
```html
  <!-- Glowing Pulse Animation -->
  <filter id="glow">
    <!--Blur effect-->
    <feGaussianBlur stdDeviation="10" result="blurElement">
      <animate attributeName="stdDeviation"
               from="1" to="10" dur="1s" 
               repeatCount="indefinite"
               values="1; 10; 10; 1;" 
               keyTimes="0; 0.45; 0.75; 1"
               keySplines=".42 0 1 1;
                           0 0 .59 1;
                           .42 0 1 1;
                           0 0 .59 1;
                           .42 0 1 1;
                           0 0 .59 1;
                           .42 0 1 1;
                           0 0 .59 1;"/>
    </feGaussianBlur>
    <!--Composition of inputs-->
    <feComposite in="SourceGraphic" in2="blurElement" operator="arithmetic"
                k1="0" k2="1" k3="1" k4="0" />
  </filter>
```


<code>feComposite, animate, feGaussianBlur</code>
```html
  <!-- Glowing Pulse Animation -->
  <filter id="glow">
    <!--Blur effect-->
    <feGaussianBlur stdDeviation="7" result="blur1">
      <animate attributeName="stdDeviation"
               from="3" to="7" dur="1s" 
               repeatCount="indefinite"
               values="3; 7; 7; 3;" 
               keyTimes="0; 0.45; 0.75; 1"
               keySplines=".42 0 1 1;
                           0 0 .59 1;
                           .42 0 1 1;
                           0 0 .59 1;
                           .42 0 1 1;
                           0 0 .59 1;
                           .42 0 1 1;
                           0 0 .59 1;"/>
    </feGaussianBlur>
    <!--Composition of inputs-->
    <feComposite in="SourceGraphic" in2="blur1" 
                operator="arithmetic"
                k1="0" k2="1" k3="1" k4="0" />
  </filter>
```


<div class="grid grid--middle">
  <div class="column grid-1of4">
    <svg viewBox="0 0 137.3 137.3">
      <use xlink:href="#svgBadge" filter="url(#spotlight)" />
    </svg>
  </div>
  <div class="column grid-3of4">
    <h3>fePointLight</h3>
  </div>
</div>
```html
<!-- Spotlight in a single spot -->
<filter id="spotlight">
  <!--Blur effect-->
  <feGaussianBlur stdDeviation="2" result="blur1" />
  <!--Lighting effect-->
  <feSpecularLighting result="spec1" in="blur1"
                      specularExponent="100"
                      lighting-color="rgba(255, 255, 255, 0.1)">
    <!--Light source effect-->
    <fePointLight x="60" y="69" z="100"/>
  </feSpecularLighting>
  <!--Composition of inputs-->
  <feComposite  in="SourceGraphic" in2="spec1" 
                operator="arithmetic"
                k1="0" k2="1" k3="1" k4="0" />
</filter>```
Note:
This is a pretty complex svg definition


`fePointLight`
```html
<!-- Spotlight in a single spot -->
<filter id="spotlight">
  <!--Blur effect-->
  <feGaussianBlur stdDeviation="2" result="blur1" />
  <!--Lighting effect-->
  <feSpecularLighting result="spec1" in="blur1"
        specularExponent="100"
        lighting-color="rgba(255, 255, 255, 0.1)">
    <!--Light source effect-->
    <fePointLight x="60" y="69" z="100"/>
  </feSpecularLighting>
  <!--Composition of inputs-->
  <feComposite in="SourceGraphic" in2="spec1" 
      operator="arithmetic"
      k1="0" k2="1" k3="1" k4="0" />
</filter>```


<div class="grid grid--middle">
  <div class="column grid-1of3">
    <svg class="svg" style="fill:#61bde3;" viewBox="0 0 137.3 137.3" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" >
      <use xlink:href="#svgBadge"/>
    </svg>
  </div>
  <div class="column grid-1of3">
    <svg viewBox="0 0 137.3 137.3">
      <use xlink:href="#svgBadge" filter="url(#spotlight-moving)" />
      <!-- <use xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="#svgBadge" filter="url(#glow)"></use> -->
    </svg>
  </div>
</use>


<div class="grid grid--middle">
  <div class="column grid-1of4">
    <svg viewBox="0 0 137.3 137.3">
      <use xlink:href="#svgBadge" filter="url(#spotlight-moving)" />
    </svg>
  </div>
  <div class="column grid-3of4">
    <h3>[feSpecularLighting](https://www.w3.org/TR/SVG/filters.html#feSpecularLightingElement)</h3>
  </div>
</div>
```html
<!-- Light travelling across the icon -->
<filter id="spotlight-moving">
  <!--Blur effect-->
  <feGaussianBlur stdDeviation="2" result="blur1" />
  <!--Lighting effect-->
  <feSpecularLighting result="spec1" in="blur1" 
        specularExponent="100"
        lighting-color="rgba(255, 255, 255, 0.1)">
    <!--Light source effect-->
    <fePointLight x="40" y="100" z="50">
      <animate  attributeName="x" from="20" to="200"
         dur="4s" repeatCount="indefinite"
         // defining the posiiton of the light
         values="-10; 100; 170; 200; -10;" 
         keyTimes="0; 0.15; 0.45; 0.75; 1"
         //keySplines defines set of Bezier control points
         keySplines=".42 0 1 1; 
                     0 0 .59 1;
                     .42 0 1 1;
                     0 0 .59 1;
                     .42 0 1 1;
                     0 0 .59 1;
                     .42 0 1 1;
                     0 0 .59 1;" />
    </fePointLight>
  </feSpecularLighting>
  <!--Composition of inputs-->
  <feComposite in="SourceGraphic" in2="spec1" 
        operator="arithmetic"
        k1="0" k2="1" k3="1" k4="0" />
</filter>
```
Note:
This is a pretty complex svg definition


`feSpecularLighting`
```html
<!-- Light travelling across the icon -->
<filter id="spotlight-moving">
  <!--Blur effect-->
  <feGaussianBlur stdDeviation="2" result="blur1" />
  <!--Lighting effect-->
  <feSpecularLighting result="spec1" in="blur1" specularExponent="100"
                      lighting-color="rgba(255, 255, 255, 0.1)">
    <!--Light source effect-->
    <fePointLight x="40" y="100" z="50">
      <animate  attributeName="x" from="20" to="200"
         dur="4s" repeatCount="indefinite"
         // defining the posiiton of the light
         values="-10; 100; 170; 200; -10;" 
         keyTimes="0; 0.15; 0.45; 0.75; 1"
         // keySplines defines set of Bezier control points
         keySplines=".42 0 1 1; 
                     0 0 .59 1;
                     .42 0 1 1;
                     0 0 .59 1;
                     .42 0 1 1;
                     0 0 .59 1;
                     .42 0 1 1;
                     0 0 .59 1;" />
    </fePointLight>
  </feSpecularLighting>
  <!--Composition of inputs-->
  <feComposite in="SourceGraphic" in2="spec1" 
      operator="arithmetic"
      k1="0" k2="1" k3="1" k4="0" />
</filter>
```


### [feComposite](https://www.w3.org/TR/SVG/filters.html#feCompositeElement)
combination of the two input images pixel-wise in image space
```html
<!-- Glowing Pulse Animation -->
<defs>
  <!-- Spotlight in a single spot -->
  <filter id="spotlight">
    <!--Blur effect-->
    <feGaussianBlur stdDeviation="2" result="blur1" />
    <!--Lighting effect-->
    <feSpecularLighting result="spec1" in="blur1" specularExponent="100"
                        lighting-color="rgba(255, 255, 255, 0.1)">
      <!--Light source effect-->
      <fePointLight x="40" y="15" z="50"/>
    </feSpecularLighting>
    <!--Composition of inputs-->
    <feComposite in="SourceGraphic" in2="spec1" operator="arithmetic"
                 k1="0" k2="1" k3="1" k4="0" />
  </filter>
</defs>```
`operator=arithmetic applies result = k1*i1*i2 + k2*i1 + k3*i2 + k4`


### Ruby Helper
```ruby
def embedded_svg(filename, options = {})
  assets = Rails.application.assets
  file = assets.find_asset(filename).source.force_encoding("UTF-8")
  doc = Nokogiri::HTML::DocumentFragment.parse file
  svg = doc.at_css "svg"
  if options[:class].present?
    svg["class"] = options[:class]
  end
  raw doc
end
```
### Use
``` ruby
= embedded_svg "svg/ralph.svg", class: "ralph-logo"
```
<div class="cite">
  Source: [robots.thoughtBot.com](https://robots.thoughtbot.com/organized-workflow-for-svg)</cite>
</div>


<!-- .slide: data-background="linear-gradient(rgba(0,0,0,.4), rgba(0,0,0,.4)), url(assets/images/code-examples/code_mode.png)" -->
<div style="background-color: rgba(0,0,0,.6); padding: 20px;">
<h1>Thank You</h1>
<h2>Questions?</h2>
<h4><a href="http://twitter.com/@robyn_larsen">@robyn_larsen</a></h4><h4><a href="http://robynlarsen.ca">r@robynlarsen.ca</a></h4>
<p class="cite">Slides: robynlarsen.ca/speaking/level-up-svg/</p>
<p class="cite">CodePen Collection: codepen.io/collection/nGzZxb/</p>
</div>


# Resources
* [Creating & Exporting SVG Assets](https://sarasoueidan.com/blog/svg-tips-for-designers/)
* [Exporting SVGs in Illustrator](https://helpx.adobe.com/illustrator/how-to/export-svg.html)
* [W3 SVG Filters](https://www.w3.org/TR/SVG/filters.html)
* [ThoughtBot - SVG Articles](https://robots.thoughtbot.com/tags/svg)
* [ThoughtBot - Inline SVG Ruby Helper](https://robots.thoughtbot.com/organized-workflow-for-svg)
* [SVG Immersion Podcast with Rob Levin](https://itunes.apple.com/us/podcast/svg-immersion-anything-everything/id975438780?mt=2)
* [Sara Soueidan](https://sarasoueidan.com/tags/svg/)
* [CSS Tricks](https://css-tricks.com/search-results/?q=svg)
* [Summary of this talk on Medium](https://medium.com/@melaniebrgr/level-up-your-design-and-development-team-svg-workflow-526ff4045a6e#.f89u13sjk)
Note:
// Keep it as easy and digestable as possible
// I wanted them to give them animated or still and they can go back to you.
// If there is too much information on there then why am I sitting there and talking to you.
// Create digestable bits on a billboard, easily digestable.


## SVG - viewport
***
I like to visualize the SVG canvas with a viewBox the same way as Google maps. You can zoom in to a specific region or area in Google maps; that area will be the only area visible, scaled up, inside the viewport of the browser. However, you know that the rest of the map is still there, but it’s not visible because it extends beyond the boundaries of the viewport - it’s being clipped out.
***
-- <cite>[Sara Soueidan](https://sarasoueidan.com/tags/svg/)</cite>