---
layout: post
title: Two Opposites
date: 2022-09-22 11:00:00
description: blog showing the development process behind two opposites
tags: unity3d 2dlighting brackeys
categories: blog
---

Two opposites is a game about the journey of two opposites (characters with mirrored controls) separated by a mirror. They need to solve puzzles to escape the mirror world and finally meet each other. However, the challenge lies in the fact that they can only solve these puzzles together. You can play it in your browser [here](https://makra.itch.io/two-opposites) <br><br>
The game was made in a week (in a team of three) for the Brackeys Game Jam (10k+ people participated worldwide) and ranked **#22 in the innovation category.** <br>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/TwoOppLogo.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Two Opposites Logo
</div>

#### 1.0 2D Lighting System
Upon initial analysis, we decided that the atmosphere should be given the most priority while developing this game. And the visual appeal of the game played a significant role in that. Back when we started working on this project, Unity didn't have any rendering pipeline that supported 2D lighting. So my task was to develop a 2D lighting system for the game.

#### 1.1 2D Raycaster (GL) - 1st iteration
* The basic idea was to draw transparent lines originating radially outwards from a sprite with negligible separation to give a sense of light coming out.
* I used the Unity's low level [Graphics Library (gl)](https://docs.unity3d.com/ScriptReference/GL.html) to draw lines between two points.
* The raycast loop formulated- <br>

{% highlight c# %}


for (float i = 0; i < theta; i += steps)
{
    GL.Begin(GL.LINES);               
    GL.Color(col); // Initializing GL Library with white color as input

    GL.Vertex3(player.transform.position.x, player.transform.position.y, 0); //strating point
    GL.Vertex3(player.transform.position.x + 
    Mathf.Cos(i * Mathf.Deg2Rad) * maxVisiblityDistance, 
    player.transform.position.y + 
    Mathf.Sin(i * Mathf.Deg2Rad) * maxVisiblityDistance, 
    0); //ending point

    GL.End(); //clearing garbage            
}


{% endhighlight %}

* This loop draws rays from the player's position to equally spaced points around the player.
* The angle that light covers is governed by **theta**.
* The spacing between each ray is governed by **steps**.
* The color of the rays is governed by **col**.
* The length of light ray is governed by **maxVisiblityDistance**.
* All of these variables were serialized in the inspector.
* This script is attached to the MainCamera and the loop is called in **OnPostRender()** method so that the lines are rendered as soon as the camera finishes rendering the scene.


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/theta.gif" title="example image" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
        Adjusting theta
        </div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/steps.gif" title="example image" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
         Adjusting steps
        </div>
    </div>
    
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/col.gif" title="example image" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
        Adjusting color
        </div>
    </div>    
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/maxvdist.gif" title="example image" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
        Adjusting max visibility distance
        </div>
    </div>    
</div>

#### 1.2 Ray Material
* The next task to make the light rays feel more natural by introducing transparency.
* While pondering I found that GL library by default uses the Unlit material provided by Unity to create the lines.
* As the Unlit Material doesn't support transparency by default, I wrote an Unlit Shader that supported both transparency and vertex colors.
* The RGBA values of the colors of the material based upon this shader was passed as an input. 

{% highlight c# %}


GL.Begin(GL.LINES);
lineMat.SetPass(0);
GL.Color(new Color(lineMat.color.r,
lineMat.color.g,
lineMat.color.b,
lineMat.color.a));


{% endhighlight %}

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/TwoOppLogo.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    With transparency controls, the rays looked more natural.
</div>

#### 1.3 Environment Lighting
* The next step would be to make the scene react to the light rays emitted by the player.
* This involved two steps-

1. Making the light ray stop when it hits an object. This is done by Raycasting along the light rays that GL draws and checking if we've hit something.

{% highlight c# %}


RaycastHit2D hit = Physics2D.Raycast(player.transform.position, new Vector2(Mathf.Cos(i * Mathf.Deg2Rad), Mathf.Sin(i * Mathf.Deg2Rad)), maxVisiblityDistance);

if (hit)
{
    GL.Vertex3(player.transform.position.x, player.transform.position.y, 0);
    GL.Vertex3(hit.point.x, hit.point.y, 0);
}

else
{
    GL.Vertex3(player.transform.position.x, player.transform.position.y, 0);
    GL.Vertex3(player.transform.position.x +
    Mathf.Cos(i * Mathf.Deg2Rad)* maxVisiblityDistance,
    player.transform.position.y +
    Mathf.Sin(i * Mathf.Deg2Rad)* maxVisiblityDistance,
    0);
} 


{% endhighlight %}

2. Making the sprite color of the object depend upon its distance from the light source.

{% highlight c# %}


GL.Begin(GL.LINES);
lineMat.SetPass(0);
GL.Color(new Color(lineMat.color.r,
lineMat.color.g,
lineMat.color.b,
lineMat.color.a));


{% endhighlight %}