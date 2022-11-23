---
{"dg-publish":true,"permalink":"/literature-notes/teaching/datavis/note/perception-data-vis/","dgHomeLink":true,"dgPassFrontmatter":false}
---



# Why perception?

We extensively rely on visuals to perceive the world around us. However, our visual perception is not as truthful as you might think. Our visual perception can be easily misled or manipulated if we are not aware of the inherent bias in the visual perception. 



## Color consistency 

Our visual system has an ability to perceive a color to be relatively the same under a situaion of changing illuminance.  This creates a pecuilar visual perception bias.  

![Color constancy](https://cdn-ak.f.st-hatena.com/images/fotolife/k/kazoo04/20150227/20150227155035.png)

The left and right dress colors in shade are the same color 😳
![Color perception2](https://pbs.twimg.com/media/CfINXByUYAAPCbE?format=png&name=small)


## Why biased?
What we see is not what we perceive. We perceive colors based on the wavelength and illuminance of the lights reflected from the object. Our visual system detects light by two photorecepters, which signals to visual cortex. The visual cortex, in turn, processes the information into the subjective perception. Our visual cortex recognizes a familiar object as being consistent color regardless of the wevelength and illuminance of the lights from the object. For example, see the following image. We perceives tree as a green object although the actual color consists only of red, black and white. 

![What we see is not what we perceives](https://upload.wikimedia.org/wikipedia/en/thumb/8/81/Mountain-spring-redwhite.png/520px-Mountain-spring-redwhite.png)

Examples and readings:
- https://twitter.com/kscottz/status/873726218344050688
- https://kazoo04.hatenablog.com/entry/2015/02/27/150642
- Color constancy (色の恒常性)

## Color encoding 

A red for you may be a different color for me. Since color perception can vary for persons to persons, we need an objective system to represent a color. Two widely used color systems are RGB and YMC. What are the differences?
- RGB refers to Red, Green and Blue. It is developed as a priciple color for lights. Our screen displays a color by combining and modulating the RGB colors. Colors get lighter if different colors RGB colors are combined. 
- YMC refers to Yellow, Magenta, and Cyan. These colors are basis colors for printing. With a black ink, we can represent any color for printing.

![RGB vs YMC](https://souzoulog.com/wp-content/uploads/2019/07/RGTBCMY.png)

RGB and YMC systems can produce any color, although it is hard to imagine what colors to mix in what proportion to create a desired color. As a more intuitive color system, HSL and HSV are developed. H and S refer to Hue and Satulation. Hue determines what color the color is. Satulation determines the intensity of the color. Both schemes are different in "brightness":

Brightness: HSL
![HSL](https://www.peko-step.com/image/img_hsv005.png)

Brightness: HSV
![HSV](https://www.peko-step.com/image/img_hsv003.png)

In HSL, the color is the most bright and least satulated at a point of 50% and gets white as the brightness increases further. In HSV, the color is the brightest at 100%. 

When to use HSL over HSV (or vise versa)? We perceive two kinds of lights, one from the light source, and the other from a reflection. HSV represents the brightness of a light source, while HSL represents a reflection of an object with the color. Thus, the L in the HSL covers white as the most strongest reflection is white.  

- Readings & Examples
	- https://jamie-wong.com/post/color/
	- https://www.peko-step.com/html/hsv.html
	- https://www.nature.com/articles/nmeth0810-573


## Summary & Implication 

Our color perception is contextual. Our perception is subjective, and not everyone perceives a color to be the same color. Cautions are needed when comparing similar colors, as our perception can be easily biased.

## Quantity 
Quantity can be visualized in different ways. A quantity (numbers) can be represented as a height, ares and volumes, which go through our eyes and stimulate our brain. Our brain has a systematic bias in translating the stimulus and quantity. Steven's Power law characterizes the bias between the actual and perceived quantities. We are pretty good at reading the length. However, areas, brightness, and volume are often underestimated. Electric shock is, on the other hand, tends to be overestimated!

![Steven's Power law](https://graphworkflow.files.wordpress.com/2019/09/stevens_law.png)

Due to this inherent perception bias, some people question of the use of pi chart. For example, the example belows demonstrate that it is hard to interpret the angles and areas correctly. By making a pichart as a bar graph, we can perceive the difference more clearly. 

![Pi chart](https://qph.cf2.quoracdn.net/main-qimg-b21b31338ffe580c7c5e2723f1d7ffe6-lq)
[link](https://www.quora.com/How-and-why-are-pie-charts-considered-evil-by-data-visualization-experts)

Then, should we abondan the pi chart all together? We can avoid using pi charts when we can replace them as bar charts. However, as data visualization gets more complex, sometimes, we may want to use pi charts. 

Our perception of change also has a pecuilar bias. For example, Weber's law suggests that the perceivable changes are proportional to the total quantity. For example, say we have two weights, one is 1kG and the other is 10kG. If we can perceive 100g (or bigger) change in 1KG weight, then we can perceive 1KG or bigger change for 10Kg. The ratio is constant. 


