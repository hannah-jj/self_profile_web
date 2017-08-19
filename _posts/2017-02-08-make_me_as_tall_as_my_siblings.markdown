---
layout: post
title:  "Make Me As Tall as My Siblings!"
date:   2017-02-08 00:23:16 -0500
excerpt_separator: <!--more-->
---


Surfing the web is no longer the same after I have gone through the HTML and CSS portion of the program!  <!--more-->I often resize the browser on desktop computer just to see how/if the pages are responsive to changes. And whenever I browse pages that are not built for optimal view on mobile device, I would think about how it can be done.  It was really amazing to see how CSS can control the styles of a website. 

While I was coding-along in the "Adding Responsive Feature" lab, I couldn't help but to notice that the below scene doesn't look right:

![](http://i.imgur.com/UjrjfmS.png)

The two columns (siblings) don't have the same height! I couldn't get pass that, so I fired up google searching for ways to make the columns the same height!  It turns out that the height issues are very common when the contents of the siblings are not exactly the same.

I found many posts, a lot of suggesting using Javasript to get the height of the tallest sibling and set the others with the same height.  Those solutions are still beyond me since I am still a newbie. So I tried other ones that are easier to understand and doable for me.  One of them suggested using table display:

![](http://i.imgur.com/OF8kMMW.png)

I tried it, and no matter how I constructed the <div> and CSS file, the two siblings won't display with same height. Arg!!! I struggled a while and decided to move on.  I concluded that due to the contents were floating, this method doesn't work.

Another post suggested a "cheap fix" with CSS file: making the padding-bottom for the siblings as many px as possible, and compensate with the same negative px on margin-bottom, then make the overflow on the parent container to be hidden.

CSS File:

```
.row-2 {
  overflow: hidden;
}
.cell-1, .cell-2 {

  padding: 30px;
  padding-bottom: 99999px;
  margin-bottom: -99999px;
  background: white;
}

```

Setup in HTML side should include the two siblings in the same <div> with class "row-2", and each sibling's container would have class of "cell-1" and "cell-2" respectively. And it worked!!!

![](http://i.imgur.com/2XdH211.png)

Now there is still something that was bothering me: the gap between this row and the next row has disappearred!  This time I thought of something quick myself: putting in a placeholder <div> section with no content:

```
.temp{
    padding: 0px;
  margin-bottom: 20px;
}
```

And hooray!

![](http://i.imgur.com/0PsqQLX.png)

It was probably a cheap fix for now before I learn more bulletproof way of fixing, but I still feel accomplished nonetheless.

Now, if there is a way to make me as tall as my sibling with a click of button, that'll be fantastic!
