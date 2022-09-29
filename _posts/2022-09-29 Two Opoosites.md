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
    This image can also have a caption. It's like magic.
</div>

### 1.0 2D Lighting System
Upon initial analysis, we decided that the atmosphere should be given the most priority while developing this game. And the visual appeal of the game played a significant role in that. Back when we started working on this project, Unity didn't have any rendering pipeline that supported 2D lighting. So my task was to develop a 2D lighting system for the game.

### 1.1 2D Raycaster (GL) - 1st iteration
* The basic idea was to draw transparent lines originating radially outwards from a sprite with negligible separation to give a sense of light coming out.
* I used the Unity's low level [Graphics Library (gl)](https://docs.unity3d.com/ScriptReference/GL.html) to draw lines between two points.
* The raycast loop formulated- <br>

{% highlight c# linenos %}

int main(int argc, char const \*argv[])
{
    for (float i = 0; i < theta; i += steps)
    {
        GL.Begin(GL.LINES);               
        GL.Color(col); // Initializing GL Library with white color as input

        GL.Vertex3(player.transform.position.x, player.transform.position.y, 0); //strating point
        GL.Vertex3(player.transform.position.x + Mathf.Cos(i * Mathf.Deg2Rad) * maxVisiblityDistance, player.transform.position.y + Mathf.Sin(i * Mathf.Deg2Rad) * maxVisiblityDistance, 0); //ending point

        GL.End(); //clearing garbage            
    }
}

{% endhighlight %}





