---
layout: post
title: Jantar Mantar Course Module
date: 2023-04-18 10:30:00
description: A course module to know about Samrat Yantra using the simulation that we've made!
tags: unity3d jantarmantar elearing
categories: blog
---

This course aims at equipping students with the ability to --
* Analyze and comprehend the intricacies of the relationship between time and the shadow cast by the Sundials (especially Jantar Mantar's sundial).
* Design a low level implementation of a sundial along with a small-scale model of Samrat Yantra.

### 1.0 Introducing the topic through Questions

#### 1.1 What's Time?

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/time_jm.png" title="example image" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

* Do you what time is?
* What are some of the different units of time that we use, like seconds, minutes, hours, and days?
* How do you think our understanding of time has changed over the years?

#### 1.2 How would you measure time?

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/measure_jm.png" title="example image" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

* Do you know how time is measured?
* Have you ever experienced a situation where it was challenging to measure time accurately? What happened?
* Let's do an activity where we come up with creative ways to measure time! Can you think of ways to measure one minute, five minutes, or an hour without using a clock or a watch? Let's see who can come up with the most creative ideas!

#### 1.3 Introducing Sundials

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/sundial_jm.png" title="screenshot" class="img-fluid rounded z-depth-1 d-block ml-auto" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/sundial_2_jm.png" title="screenshot" class="img-fluid rounded z-depth-1 d-block mr-auto" zoomable=true %}
    </div>
</div>

* Someone mentioned the sun as a way to measure time. Did you know that people have been using the sun to measure time for thousands of years? Have you ever heard of a sundial? 
* Have you ever seen a real-life sundial before? Where and when did you see it?
* Do you know how they work?

## 2.0 Learning through Activities

#### 2.1 Stick and Shadow Activity

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/sns_1_jm.png" title="screenshot" class="img-fluid rounded z-depth-1 d-block ml-auto" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/sns_2_jm.png" title="screenshot" class="img-fluid rounded z-depth-1 d-block mr-auto" zoomable=true %}
    </div>
</div>

**Materials needed:**

* A stick or a dowel
* Chalk or masking tape
* A watch or a clock

**Instructions:**

* Choose a sunny day and find a flat surface that receives sunlight, such as a patio or a paved area. Make sure there are no obstructions that would block the sunlight.
* Using the chalk or masking tape, draw a circle on the ground with a diameter of at least one meter. This circle represents the face of the sundial.
* Insert the stick or dowel in the center of the circle, making sure it stands up straight.
* At exactly noon (12:00 PM), stand the stick or dowel upright so that it casts a shadow on the circle. Mark the tip of the shadow with a small dot or a piece of chalk.
* Wait for 15 minutes and mark the tip of the shadow again. Repeat this process every 15 minutes until 3:00 PM, making sure to mark each new position of the shadow on the circle.
* Connect the dots using a straight edge or a ruler to create a curved line. This line represents the path of the sun in the sky.
* Divide the circle into 12 equal parts using the curved line as a guide. Mark each division with a number from 1 to 12, starting at the top of the circle and moving clockwise.
* Your sundial is now complete! To tell the time, stand the stick or dowel upright so that it casts a shadow on the circle. The position of the shadow on the circle will indicate the time of day.

**Tips:**

* Make sure to use a watch or a clock to keep track of the time accurately.
* If the stick or dowel is too short, you can use a stack of books or a box to elevate it.
* If the surface you're using isn't flat, make sure to adjust the angle of the stick or dowel so that it's perpendicular to the ground.
* If you live in the Southern Hemisphere, make sure to point the stick or dowel towards the North instead of the South.

#### 2.2 Learning about Samrat Yantra

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/samrat_yantra_jm.jpg" title="example image" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

**Materials Needed:**
* Ruler
* Compass
* Scissors
* Cardboard or stiff paper
* Pencil
* Tape
* Protractor
* Whiteboard or chart paper

**Instructions:**

* Provide the students with the [Samrat Yantra Model Template](https://www.jantarmantar.org/resources/Projects/SY-Model/Samrat-Yantra-Model-Templates.pdf) and explain the different views and proportions of the instrument.
* Ask the students to use a ruler and a compass to trace the shapes onto a piece of cardboard or stiff paper.
* Have the students cut out the traced shapes using scissors.
* Ask the students to assemble the individual cut pieces of sundial using tape to attach the various parts together.
* Have the students use a protractor to set the angle of the gnomon to the latitude of their location.

Ask the students to place their Samrat Yantra in a sunny location and use a pencil to mark the position of the shadow cast by the gnomon at different times of the day.

Have the students record the time corresponding to each shadow position on a whiteboard or chart paper.

Discuss with the students how the Samrat Yantra measures time using the position of the sun, and how its design takes into account the Earth's axial tilt and the latitude of the location.

Finally, ask the students to present their Samrat Yantra to the class and explain how they used the templates to guide their designs, and how they took into account the Earth's axial tilt and the latitude of their location.

#### 1.2 3D Models

- Then we created rough models of the [Samrat Yantra](https://www.jantarmantar.org/learn/observatories/instruments/samrat/index.html) in Blender based on the resources we could procure.
- As the model didn't take CAD dimensions into account, it sure had some flaws that were pointed by Sameer Sir in our weekly meetings. Especially the fact that the base model wasn't symmetrical from both the sides.
- We were later expected to come up with dimensionally accurate models based on CAD and paper model replicas that we found

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/SamratYantraRough.png" title="example image" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/Error1_SamratYantra.png" title="example image" class="img-fluid rounded z-depth-1" zoomable=true %}
        <div class="caption">
        Left Side - Base
        </div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/Error2_SamratYantra.png" title="example image" class="img-fluid rounded z-depth-1" zoomable=true %}
        <div class="caption">
        Right Side - Base
    </div>
    </div>    
</div>
<div class="caption">
    Not Symmetrical
</div>

#### 1.3 Day & Night Cycles

My job was to script the day & night cycles in Unity (need not be physically precise initially).

- I used a Procedural Sky shader for skybox as it comes with a sun that mimics the directional light by default.
- Then I bound the directional light's rotation and intensity, fog color and a clock to the day & night cycle.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <video class="video-fluid rounded z-depth-1" autoplay muted loop>
            <source src="../../../assets/img/day_night.mp4" type="video/mp4">
        </video>
    </div>
</div>

#### 2.0 Week - 2

In the next week we were assigned the task to come up with labelled Jantar Mantar Engineering Drawings, paper prototype and 3D models of Jantar Mantar that we obtained online and adding a rough sundial model in Unity to check if the shadows casted by the day & night cycle are working properly.

#### 2.1 Precision CAD modelling

- We were suggested to make accurate CAD model from any random CAD design to learn precision CAD modelling.
- The blend file can be found [here](assets/../../assets/misc/Perc.blend).

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/CAD_Design.jpeg" title="example image" class="img-fluid rounded z-depth-1" zoomable=true %}
        <div class="caption">
        CAD Design
        </div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/Model_Render.png" title="example image" class="img-fluid rounded z-depth-1" zoomable=true %}
        <div class="caption">
        Model Render
    </div>
    </div>    
</div>

#### 2.2 Labelling of Engineering Drawings

- All the engineering drawings were labeled to make their assembly (for 3D model and paper prototype) easier.
- As we didn't have a lot of dimensionally accurate references for the Samrat Yantra, so we used online references to manually label each of them individually first and then come up with a rough idea how the model and paper model was to be assembled.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/Label.jpg" title="example image" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

#### 2.3 Making of Paper Prototype

- The engineering drawings after analysis and labelling were converted into a paper prototype for us to visualize.
- The process was fairly simple as these engineering drawings were originally meant for paper prototyping itself. So we had to cut and glue them accordingly.
- The prototypes were dimensionally accurate and represented a scaled down model of Samrat Yantra.
- As the paper was quite thin, the model wasn't structurally intact.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/Cut.jpg" title="example image" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

#### 2.4 Shadows in Unity

- I decided to use a cylinder model to simulate how the sun would cast its shadows on a full day and night cycle.
- The shadows depicted linear movement (motion on a straight line), unlike the sundial, which roughly works like a clock, and the dial rotates in a clockwise fashion.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <video class="video-fluid rounded z-depth-1" autoplay muted loop>
            <source src="../../../assets/img/shadow_day_night.mp4" type="video/mp4">
        </video>
    </div>
</div>

#### 2.5 Recreating paper prototype in Blender
- Using the drawings and dimensions in paper prototype we created the parts of Samrat Yantra.
- As we created each part individually and later scaled them back, the final model was not in proportion.
- The problem was then solved using accurate dimensions calculated from the pdf.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/251.png" title="example image" class="img-fluid rounded z-depth-1" zoomable=true %}        
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/252.png" title="example image" class="img-fluid rounded z-depth-1" zoomable=true %}        
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/253.png" title="example image" class="img-fluid rounded z-depth-1" zoomable=true %}        
    </div>      
</div>


#### 3.0 Week - 3

In this week we were expected to start working the UX that our project had to offer.

- For this we were expected to give the day/night cycle and camera controls to the user as well as allow the user to input any time to check the shadow configuration at that time.
- We also decided to replace the existing cylinder that depicted the sundial with an actual sundial model along with proper sundial markings.
- Some people began working on the game's UI as well.

#### 3.1 Sundial Model

- A sundial was modeled based on refrence dimensions that we obtained online.
- It was quite surprising to see that the shadows were rotating perfectly just due to the shape of the dial while keeping the rotation pattern of the sun same as before.
- Add cyl vs sundial and model img here.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/Sundial.jpeg" title="example image" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <video class="video-fluid rounded z-depth-1" autoplay muted loop>
            <source src="../../../assets/img/shadow_day_night.mp4" type="video/mp4">
        </video>
        <div class="caption">
            Old Design - Less Physical Accuracy
        </div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <video class="video-fluid rounded z-depth-1" autoplay muted loop>
            <source src="../../../assets/img/accurate_day_night.mp4" type="video/mp4">
        </video>
        <div class="caption">
            New Design - More Physical Accuracy
        </div>
    </div>    
</div>

#### 3.2 Day/Night Cycle & Camera Controls

- Unity's default input system was used to take the input of the players.
- The horizontal axis was assigned to the rotation of the camera whereas the vertical axis was kept responsible for the day/night cycle.
- A dedicated prompt was shown on the screen to inform the users about the same.

<video class="video-fluid rounded z-depth-1" autoplay muted loop>
    <source src="../../../assets/img/user_control.mp4" type="video/mp4">
</video>

#### 3.3 Custom Time Input

- I used the Text Mesh Pro input box to take inputs from the user.
- I limited each text box to take 2-digit integer inputs (HH & MM format).
- This value was used to assign a custom time value that users could input to check the behavior of the sundial at that particular time.

<video class="video-fluid rounded z-depth-1" autoplay muted loop>
    <source src="../../../assets/img/time_day_night.mp4" type="video/mp4">
</video>

#### 4.0 Week-4
In this week we worked upon the UI & UX.

#### 4.1 Designing the UI
* The UI for the project was designed using Figma.
* The icons were given a contrasting color with respect to the black and blue sky hue and they were provided with a drop shadow as well.
* The edges were kept rounded to give it a material look.  

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/figma_sundial.png" title="example image" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

#### 4.2 Implementing the UI in project
* The UI was implemented over the canvas component provided by Unity to replace keyboard inputs with Touch/Click inputs. It Included-
  * A Start/Stop Button
  * A Slider
  * A Left/Right Button
  * A Forward/Backward button
  
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/UI_Sundial.jpg" title="example image" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

* The Start/Stop button was used to play and pause the simulation.
* The Slider was used to rotate the camera angle (with step wise increment/decrement aided by the Left/Right button).
* The Forward/Backward button used to speed up or reverse the process.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <video class="video-fluid rounded z-depth-1" autoplay muted loop>
            <source src="../../../assets/img/start_stop_btn.mp4" type="video/mp4">
        </video>
        <div class="caption">
            Start/Stop Button
        </div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <video class="video-fluid rounded z-depth-1" autoplay muted loop>
            <source src="../../../assets/img/slider.mp4" type="video/mp4">
        </video>
        <div class="caption">
            Slider
        </div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <video class="video-fluid rounded z-depth-1" autoplay muted loop>
            <source src="../../../assets/img/fwd_bwd_btn.mp4" type="video/mp4">
        </video>
        <div class="caption">
            Forward/Backward button
        </div>
    </div>      
</div>

#### 5.0 Week-5
In this week, we began working upon the login system.

#### 5.1 Home & Sign Up Page
* Created a menu for selecting the yantra user wants to explore. 
* Created icons for selecting the yantra user wants to explore.
* A `sign-up` Page opens user selects a yantra.
* The `home.html` page consists of containers, each representing a yantra having a class `product-container`, with reference to `login.html`.
* The webpage requires one-time signup.
* The orientation of the `login.html` page is styled using css.
* Js script with an event listener is linked to signup element.
* The event listener sends data using POST request to the google sheet.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/icons.png" title="example image" class="img-fluid rounded z-depth-1" zoomable=true %}
        <div class="caption">
        Yantra Selection Menu
        </div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/signup_page.png" title="example image" class="img-fluid rounded z-depth-1" zoomable=true %}
        <div class="caption">
        Sign Up Menu
    </div>
    </div>    
</div>

#### 5.2 Login Information
* The login details of users are stored in a google sheet.
* In further iterations the details will be stored in a database.
* The database will also be used for saving user preferences such as, camera and lightning setups.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/login_info.png" title="example image" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>


#### 6.0 Week-6
In this week, we were expected to convert the Unity project into a web-based experience and integrate it with the our SignUp page. Apart from this, we were also expected to come up with precise models of the Yantras and integrate them within our project.

#### 6.1 Exporting the Project to Web
* The Unity project was optimized and revamped to be exported to the Web as a WebGL experience.
* The project was hosted online using Github Pages and can be accessed [here](https://aryamanntomar.github.io/DES499-WebPage/).
* All compressions on the build were disabled and they generally raise conflicts while getting decompressed on the Jekyll framework that GitHub Pages use.
* Code was optimized to give preference to speed over size in the final build.
* The homepage was renamed to `index.html` (naming convention for homepages on Github Pages).
* The yantras were linked to the `jantar-mantar-experience.html` in our build.
* We further plan to use Firebase Authentication to only provide private sessions to the users who Sign Up for the experience.

<video class="video-fluid rounded z-depth-1" autoplay muted loop>
    <source src="../../../assets/img/WebGLExp.mp4" type="video/mp4">
</video>

#### 6.2 Precise models of the Yantras

* First, the dimensions of the model were calculated by Ajitesh.
* The base of the model was made by Shubham using the dimensions provided by Ajitesh.
* After referring to the [PDF](https://www.jantarmantar.org/resources/Projects/SY-Model/Samrat-Yantra-Model-Templates.pdf) provided by sir, we found difficulty in coming up with precise models of the block.
* We tried certain adjustments, scaling and fitting the side block on the base of the yantra.
* The curves of the yantras was quite difficult to make, due to its precision levels.
* We made the curve long enough to pass through the pyramid of the yantra while maintaining the precision standards of our model after multiple adjustments (even though they were not precise in the [PDF](https://www.jantarmantar.org/resources/Projects/SY-Model/Samrat-Yantra-Model-Templates.pdf) itself)
* The center pyramids along with the staircase was similarly designed using the iterative adjustment process mentioned above.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/PM1.jpg" title="example image" class="img-fluid rounded z-depth-1" zoomable=true %}
        <div class="caption">
        The Curves
        </div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/PM2.jpg" title="example image" class="img-fluid rounded z-depth-1" zoomable=true %}
        <div class="caption">
        The Center Pyramid
    </div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/PM3.jpg" title="example image" class="img-fluid rounded z-depth-1" zoomable=true %}
        <div class="caption">
        The Base with Side Blocks
    </div>
    </div>    
</div>