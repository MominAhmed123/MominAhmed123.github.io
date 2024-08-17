---
layout: post
title: Vector Image Compression
description: Drawing with Fourier Epicycles
image: "/assets/images/projects/dftp.png"
---

<video style = "width: 75%; height: auto;" autoplay muted>
    <source src = "/assets/images/projects/DFT/DFT-skip2.mp4" type = "video/mp4" >
Your browser does not support the video tag.
</video>
Remark: I am sincrely sorry for the light mode.

## Motivation
If you draw a simple graph and take a screenshot, every single pixel is being saved. This is really ineffecient for several reasons - for example one simple improvement is just to save the location of the pixels that lie on the graph. I was more interested in trying to save even lesser space. The idea was that I wanted to approximate my graph with some mathematical equations where the approximation gets better if I am allowed to add more equations. 

One intuitive idea is just to capture some equally spaced points and connect them with a line segment. 

While this would definitely work, your approximate image will always be really sharp. It would be great if we could connect the points with some smooth curve, but we can't just randomly select a fixed curve equation to connect the points. On some research, I stumbled upon Discrete Fourier Transform.

## Discrete Fourier Transform
Suppose we have a bunch of rotating circles: 

$$C_1(r_1), ... , C_n(r_n)$$

where $$C_k(r_k)$$ means a circle of frequency $$k$$ units and radius $$r_k$$ units.
Using this list of circles, we can draw a figure by connecting the end of one circle to the start of the other circle (as you saw in the really clustered clip in the beginning). Given a list of $$r_k$$ it is easy to construct the output, however going in the backwards direction is not so easy. 

The idea with DFT is that we want to go from some points to a list of $$r_k$$. That is, we take some sample points from the output image, and we want to decompose it into the list of $$r_k$$ that make up the output.

As always, since I am too lazy (and I will probably make some mistakes in the explanation), here is an excellent video about DFT: 
<iframe style = "width: 100%; height: 400px;" src="https://www.youtube.com/embed/spUNpyF58BY" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
So, this is exactly what we were looking for. We have our output curve and we take equally spaced points from it as sample points. We use DFT to turn those points into a decomposition of rotating circles which we draw out. Since each sample point is covered in our approximate graph, if we add more sample points, our approximate graph becomes more accurate.

## The Code
The code is avaiable on github <a href = "https://github.com/MominAhmed123/DFT"> here </a>.

You can run mouse.java to draw any figure. Sample points are taken from this graph (based on the skip variable) and stored in samples.txt. 
<video style = "width: 75%; height: auto;" autoplay muted>
    <source src = "/assets/images/projects/DFT/DFT-mouse draw.mp4" type = "video/mp4" >
Your browser does not support the video tag.
</video>
VectorRotation.java uses DFT.java which accesses the points from samples.txt and performs DFT to provide the required radius of the epicycles. The number of epicycles depends on the number of sample points, and the number of sample points depend on the skip variable in mouse.java
~~~
    public final static int skip = 10;
~~~
Here skip indicates how many pixels are ignored until we take a sample point from the graph. In this case, we take every 1 in 10 points - the more we skip, the less accurate our drawing is.
<video style = "width: 75%; height: auto;" autoplay muted>
    <source src = "/assets/images/projects/DFT/DFT-skip10.mp4" type = "video/mp4" >
Your browser does not support the video tag.
</video>

You can also change the speed of the drawing by changing the time delay in VectorRotation.java
~~~
timer = new Timer(50, e -> {
    angle += dt;
    //if (angle >= Math.PI*2){
    //    angle = 0;
    //}
    updateVector();
});
~~~
For each frequency $$k$$, the amplitudes of each cycle $$r_k$$ along with the phase change $$\theta _ k$$ is printed in the terminal. 
