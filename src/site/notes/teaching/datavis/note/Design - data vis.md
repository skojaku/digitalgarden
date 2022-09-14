---
{"dg-publish":true,"permalink":"/teaching/datavis/note/design-data-vis/","dgHomeLink":true,"dgPassFrontmatter":false}
---


# Design
Data visualization conists of many different parts. For example, a simple scatter plot consists of axis, labels, ticks, shapes and colors of points. Each component is indispensable and needs to be carefully designed to team up with other components. Inappropriate arrangement of parts loses clarity and hinders the key messages. 

# Gestalt Principle 

We make sense of complex worlds by grouping different elements. 

"*The whole is something else than the sum of its parts.*" 

as encapsulated by a German Gestalt Psycologist, Kurt Koffka. On the side note, this phrase is a translation from German, and there was another incorrect translation that goes like "The whole is *greater* than the sum of its parts." But the original argument of Kurt is that the "whole" is a different element added to its parts, not greater than its parts. 

There are three fundamental principles of how make group things together:

**#1: Objects are perceived in the simplest form.**
For example, when we see the Olympic logo, we perceive it as five rings interlocking each other, instead of different (non-ring) objects that are separated to each other. 

![olympic logo](https://upload.wikimedia.org/wikipedia/commons/thumb/5/55/Olympic_rings_with_transparent_rims.svg/2560px-Olympic_rings_with_transparent_rims.svg.png)


**#2: Our eyes naturally follow smooth lines and curves.** 
If you drive a car, you should see that lanes are separated by a sequence of white rectangles. We follow them as if they are a continuous line, although each element is disconnected and not related to each other. 

![Road](https://bloximages.newyork1.vip.townnews.com/santafenewmexican.com/content/tncms/assets/v3/editorial/2/ab/2ab36ee8-7d4c-11eb-a7a1-2f768ea3d73e/60417f4d3e2d7.image.jpg?resize=554%2C500)

**#3: We tend to *fill in* the details if parts are incomplete.**
When an object is incomplete, we tend to fill in the details. For example, the logo of WWF dones not have some outlines. Still, we perceive it as a panda bcause we subconciously fill in the missing outlines. 

![WWF](https://uploads.toptal.io/blog/image/125750/toptal-blog-image-1522045535498-3cfb27ba5cf1188777b80c9ea2f652b2.png)


# Five laws of Gestalt Psychology
The three fundamental principles lead to several laws of Gestalt Psycology. 

**1. Law of similarity** 
We tend to group things that are similar. For example, Slack logo consists of many different parts. But we tend to group parts of the same *color* and percieve four parts making up the logo. The logo of NBC also uses the law of similarity. It represents wings of peacok. Although each wing has a different color, they are perceived as a unified whole because all wings have the same *shape*. The notion of "similar" can be anything, as long as we can perceive it. 

![slack¥|200](https://orangecounty.aiga.org/wp-content/uploads/2021/05/slack-logo.png)   ![slack¥|200](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8d/NBC_2013_%28flat_version%29.svg/1200px-NBC_2013_%28flat_version%29.svg.png)

**2. Law of closure**
When an object is incomplete, we tend to fill in the missing parts. For example, we may perceive a triangle in the following figure even if the triangle doesn't exist . It's because we fill in the lines to make up a triangle. It's also related to the first principle, i.e., instead of understanding it as three kiwi with some part missings that face inward, it's simpler if we understand it as three kiwi with a triangle on top. 

![gestalt](https://miro.medium.com/max/1400/1*i00fI96rVsxN4Tw-fHaHcQ.png)

**3. Law of proximity**
We tend to group things that are close to each other. For example, we can read "UX" in the figure because we tend to group points that are next to each other as a group.

![UX](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTTB4CvVVrZslw5k0VedxytCqjwC7mFa2n0QQ&usqp=CAU)
**4. Law of simplicity**
We tend to group things in the simplest form. For example, we perceive the log of Indiana University as "I" and "U" intersecting each other, even if there are many but more complex decomposition sof the logo.

![Indiana University¥|400](https://i.pinimg.com/736x/e6/0a/07/e60a07442ff285a78a3b95c018967d9b.jpg)


**5. Law of continuity** 
Our brain has a tendency to decieve smooth lines and curves. For example, in the logo of IBM, the words "IBM" appears to be easy read despite many gaps.   
![IBM](https://www.neurosciencemarketing.com/wp-content/uploads/2017/03/IBM.jpg)

## Implication for data visualization
Gestalt psycology provides many interesting implications into data visualization. For instance, the law of similarity tells us that we should use similar colors and shapes for similar data. The law of proximity tells us that we should put related panels next to each other. The law of continuation suggests that we should connect points if they are sequentially ordered. The law of closure suggests that we may drop the clunky borders of each panel. Law of simplicity warns that we have a tendency to oversimplify complex image, e.g., decieving a trend as linear, even if it is a highly non-linear non-monotonical trend.


![line data points](https://www.excelcharts.com/wp-content/uploads/2011/11/line-data-points2.png)

![Gestalt](https://cdn-images-1.medium.com/max/1024/1*C9XapvVFAhF4DHXXf2TUuA.jpeg)
## Why we group things togeter?

Our perception of grouping is deeply attributed to how our brain processes information. When an information comes into our brain, we pre-process the information before consciously process it. This is called ***pre-attentative process***. It is a process that takes place subconciously before we pay attention consciously. Pre-attentive process filters out important information, which is then futher processed by more attentative process. Pre-attentative process is useful in data visualization to effectively direct our attention to the information we want to present.

![pre-attentative process](https://infovis-wiki.net/w/images/6/6a/Preattentive_4.JPG)

![Pre-attentative by color and shape](https://humansofdata.atlan.com/wp-content/uploads/2019/07/preattentive-processing.png)


Many other laws and interesting examples are here!
- [Gestalt Laws applied to data visualization](http://daydreamingnumbers.com/concepts/gestalt-laws-data-visualization/)
- [mautrau](https://muatrau.com/which-gestalt-principles-is-applied-when-we-perceive-objects-which-are-near-each-other-to-belong-together#gestalt-principle-proximity)
- [pre-attentive processing](https://uxplanet.org/preattentive-processing-and-design-e59eba74373e)
