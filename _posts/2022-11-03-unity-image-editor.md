---
layout: post
title: Image Editor using Unity
date: 2023-08-17 11:00:00
description: I made an image editor using Unity just for the kicks!
tags: unity3d photo-editor
categories: blog
---

I was recently accepted into the Florida Interactive Entertainment Academy for the Technical Art track. I was checking out some medium blogs to to learn some image manipulation to brush up some of my technical art skils. Them medium gods were actually pretty darn helpful and I somehow ended up developing a janky photo editor using Unity. It transforms any regular image into a "low-quality-meme". I call it the "Low Res Meme Editor". I'll be discussing my approach towards developing the photo editor in this blog.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/Icon_Editor.png" title="Janky Icon for a Janky Photo Editor" class="img-fluid rounded z-depth-1" zoomable=true %}
        <div class="caption">
        Janky Icon for a Janky Photo Editor
        </div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/Editor_UI.jpg" title="The Editor UI" class="img-fluid rounded z-depth-1" zoomable=true %}
        <div class="caption">
        The Editor UI
        </div>
    </div>     
</div>

## **1.0 Preparing Images for Editing**

The first step was transforming the images into a suitable format for easy manipulation. `Texture2D` felt appopriate for this purpose, as it gives me more control over the pixel data. I could directly manipulate pixel values using the `GetPixel()` and `SetPixel()` methods of any Texture2D object.

* So I created method that took an image an returned a Texture2D corresponding to it.

        {% highlight c# %}

        private Texture2D GetTextureFromImage(Image targetImage) {}

        {% endhighlight %}

* Then I created an empty texture with the width and height of the image.

        {% highlight c# %}

        Rect rect = targetImage.sprite.rect;
        Texture2D texture = new Texture2D((int)rect.width, (int)rect.height);
                
        {% endhighlight %}

* Finally the pixels on the original image are mirrored on the pixels of the empty texture using the `SetPixels()` method.

        {% highlight c# %}

        texture.SetPixels(
            targetImage.sprite.texture.GetPixels(
                (int)rect.x,
                (int)rect.y,
                (int)rect.width, 
                (int)rect.height));
        texture.Apply();
        return texture;
                
        {% endhighlight %}

## **2.0 Image Editing Algorithms: Approach**

I chose to work on a series of image editing techniques. My plan was to apply these algorithms with different settings, essentially creating pre-defined configurations for editing images. **Most of these algorithms shall serve the sole purpose of giving the image a low-quality-meme look".**

#### **2.1 Saturation Control**

The first control I wished to establish was for Saturation i.e the intensity of the color of each pixel of the image. 

* A saturation value of 0 makes the image grayscale.
* A value of 1 keeps the original colors unchanged.
* Anything above 1 makes the image more vibrant.

<br>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/Saturation_Diagram.png" title="Algorithm for Saturation Control" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    Algorithm for Saturation Control
</div>

So the basic algorithm I used to achieve saturation control was--

1. Getting the texture from the image and creating an empty texture to assign the edits texture to.

{% highlight c# %}

originalTexture = GetTextureFromImage(image);
modifiedTexture = new Texture2D(originalTexture.width, originalTexture.height);

{% endhighlight %}

2. Looping through the pixels to access the HSV values from their color. The `saturation` value is of importance here as we are going to alter it, so it is passed as a reference type.

{% highlight c# %}

// accessing the texture code here

Color[] pixels = originalTexture.GetPixels();
int totalPixels = pixels.Length;

for (int i = 0; i < totalPixels; i++)
{
    Color pixelColor = pixels[index];
    Color.RGBToHSV(pixelColor, out float hue, out float saturation, out float value);    
}

{% endhighlight %}

3. Applying the saturation to each pixel. The `saturation` value is multiplied by  a `saturationFactor` to alter it. And finally a new array of Color of length the same as the original image is assigned the color with the new `saturation` value.


{% highlight c# %}

Color[] modifiedPixels = new Color[totalPixels];

for (int i = 0; i < totalPixels; i++)
{
    // accessing HSV code here
    saturation *= _saturationFactor;
    modifiedPixels[index] = Color.HSVToRGB(hue, saturation, value);
}

{% endhighlight %}

4. A new texture with the saturated pixels is created and assigned to a sprite.

{% highlight c# %}

modifiedTexture.SetPixels(modifiedPixels);
modifiedTexture.Apply();

Sprite modifiedSprite = Sprite.Create(modifiedTexture,
                                      new Rect(0, 0, modifiedTexture.width, modifiedTexture.height),
                                      new Vector2(0.5f, 0.5f));
image.sprite = modifiedSprite;

{% endhighlight %}

<br>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/saturationFactor.png" title="Saturation Control" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    Saturation Control
</div>


#### **2.2 Adding Gaussian Blur**

Next in the list are algorithms that helps blur an image using a Gaussian Function. This helps achieve the bokeh effect. It has the effect of reducing an image's high frequency components and thus acting like a low-pass filter. 

1. **Creating the Gaussian Kernel**

* First we create a gaussian kernel of a given size and radius. The gaussian kernel is a float 2D matrix (`float[,]`). Each element in the matrix is a weight that determines the contribution of each pixel to the blurring process. These weights are caluclated based on the Gaussian distribution formula.

<p align="center">
  <img src="https://latex.codecogs.com/svg.image?f(x)&space;=&space;\frac{1}{\sigma\sqrt{2\pi}}&space;e^{-\frac{(x-\mu)^2}{2\sigma^2}}" style="color:white;" />
</p>

* **Input Parameters:** The `CreateGaussianKernel()` method takes the `radius` and `size` of the kernel as the parameter and returns a 2D matrix (`float[,]`). The `size` represents the dimensions of the kernel, and the `radius` controls the spread of the blur effect.

{% highlight c# %}

private float[,] CreateGaussianKernel(int size, float radius) {}

{% endhighlight %}

* **Initialization:** An empty 2D array called `kernel` of size x size is initialized. This array will store the weights that determine the strength of blurring for each pixel. The variable `sigma` is calculated as `radius / 3f`. `sigma` is a parameter that affects the spread of the Gaussian distribution. A larger sigma value results in a wider spread of the blur. The constant for the gaussian distribution is calculated as twice the `sigma` squared.

{% highlight c# %}

float[,] kernel = new float[size, size];
float sigma = radius / 3f; 
float twoSigmaSquare = 2f * sigma * sigma; 
float totalWeight = 0f; 

{% endhighlight %}

* **Gaussian and Total Weight Calculation:** The nested loops iterate over each element of the `kernel` array. For each element at position [y, x], it calculates the squared distance from the center of the kernel. The formula *x * x + y * y* calculates the squared Euclidean distance. Using the squared distance, it calculates the weight using the formula *Mathf.Exp(-distance / twoSigmaSquare)*. This weight is a measure of how much influence a pixel at that distance should have on the blurring process. The greater the distance, the smaller the weight. The calculated weight is assigned to the corresponding position in the kernel array. The `totalWeight` variable keeps track of the sum of all the weights in the kernel. This sum is used to normalize the kernel later.

{% highlight c# %}

// intialization code here

for (int y = -size / 2; y <= size / 2; y++) // -size / 2 to size / 2
{
    for (int x = -size / 2; x <= size / 2; x++) // -size / 2 to size / 2
    {
        float distance = x * x + y * y; 
        float weight = Mathf.Exp(-distance / twoSigmaSquare); 
        kernel[y + size / 2, x + size / 2] = weight; 
        totalWeight += weight;
    }
}

{% endhighlight %}

* **Kernel Normalization:**  After calculating all the weights, the kernel is normalized to ensure that the sum of all the weights equals 1. This step is essential to maintain the overall brightness of the image during blurring. The nested loops iterate over each element of the `kernel` array again. Each weight is divided by the `totalWeight`, effectively scaling down the weights to ensure their sum equals 1. And then the `kernel` is returned.

{% highlight c# %}

// intialization code here

// weight calculation code here

for (int y = 0; y < size; y++)
{
    for (int x = 0; x < size; x++)
    {
        kernel[y, x] /= totalWeight;
    }
}

return kernel;

{% endhighlight %}

2. **Applying the Gaussian Kernel**

The gaussian kernel created above is applied to the pixels of the image thereby convulating the kernel with the particular pixel and its neighbouring pixels, thus calculating the weighted sum of their colors. This sum becomes the new color value for the central pixel, resulting in the blurring effect.

* **Input Parameters:** The `ApplyKernel()` method takes a Texture2D as input along with a `kernel`, `x`, `y` (position within the image) and `size` of the kernel as the parameter. It then calculates and returns the weighted average of colors in the neighborhood around the (x, y) position using the provided Gaussian kernel.

{% highlight c# %}

private Color ApplyKernel(Texture2D texture, int x, int y, float[,] kernel, int size) {}

{% endhighlight %}

* **Initialization:** The 3 float variables for the RGB values are initalized to accumulate the weighted sum of red, green, and blue color channels. The half-size of the kernel is calculated as well and this is used to determine the bounds of the neighborhood around the (x, y) position.

{% highlight c# %}

float r = 0f, g = 0f, b = 0f;
int halfSize = size / 2;

{% endhighlight %}

* **Looping through the Kernel:** Nested for loops iterate over each cell in kernel. The outer `j` loop iterates over the rows of the kernel whereas the inner `i` loop iterates over its columns. 

{% highlight c# %}

for (int j = 0; j < size; j++)
{
    for (int i = 0; i < size; i++)
    {
        
    }
}

{% endhighlight %}

* **Calculating pixel coordinates of Input Image:** `offsetX` and `offsetY` is calculated inside the loop to represent the corresponding pixel coordinates in the input image based on the current `x` and `y` position within the image and the `i` and `j` indices. Both these values are clamped to the bounds of the image.

{% highlight c# %}

int offsetX = x + i - halfSize;
int offsetY = y + j - halfSize;

offsetX = Mathf.Clamp(offsetX, 0, texture.width - 1);
offsetY = Mathf.Clamp(offsetY, 0, texture.height - 1);

{% endhighlight %}

* **Retrieving and Updating the color values of pixels:** The color values of pixels at calculated coordinates `offsetX` and `offsetY` are retrieved from the input texture. The RGB values intialized earlier are updated by adding the color values retrieved multiplied by the weight value from the Gaussian Kernel matrix from the `i` and `j` position. The final color obtained is returned.

{% highlight c# %}

Color pixel = texture.GetPixel(offsetX, offsetY);
float weight = kernel[j, i];

r += pixel.r * weight;
g += pixel.g * weight;
b += pixel.b * weight;

{% endhighlight %}

3. **Applying the Gaussian Blur** 
Now we apply the gaussian blur to the image by calculating the kernel, processing the pixel and updating the image. 

* **Input Parameters:** The `ApplyGaussianBlur()` method takes a Texture2D as input along with the `radius` of the Gaussian Blur needed (basically used as the size of the kernel) and returns the blurred texture.

{% highlight c# %}

private Texture2D ApplyGaussianBlur(Texture2D sourceTexture, float radius) {}

{% endhighlight %}

* **Calculating Kernel size and Kernel:** The Kernel size is obtained by rounding the `radius` to the nearest integer, doubling it and then adding 1 to it, ensuring coverage of sufficient area around each pixel.

{% highlight c# %}

int kernelSize = Mathf.RoundToInt(radius) * 2 + 1;
float[,] kernel = CreateGaussianKernel(kernelSize, radius);

{% endhighlight %}

* **Creating Blurred Texture:** A new `blurredTexture` with same dimensions as `sourceTexture` is initialized.

{% highlight c# %}

Color[] pixels = sourceTexture.GetPixels();
Color[] blurredPixels = new Color[pixels.Length];

{% endhighlight %}

* **Iterating through pixels:** A nested loop is used to access the pixels of the `sourceTexture`. For each pixel at (`x`, `y`), the `ApplyKernel()` function is called to calculate the new color of that pixel. The calculated blurrer color is stored in the corresponding position of the `blurredPixels` array.

{% highlight c# %}

for (int y = 0; y < sourceTexture.height; y++)
{
    for (int x = 0; x < sourceTexture.width; x++)
    {
        Color blurredColor = ApplyKernel(sourceTexture, x, y, kernel, kernelSize);
        blurredPixels[y * sourceTexture.width + x] = blurredColor;
    }
}

{% endhighlight %}

* **Applying Blurred pixels to the Texture:** After processing all the pixels, the `blurredPixels` array is assigned to the `blurredTexture` and it is returned.

{% highlight c# %}

blurredTexture.SetPixels(blurredPixels);
blurredTexture.Apply();

return blurredTexture;

{% endhighlight %}

* **Blurred Sprite:** A sprite is created from the blurred texture and is applied to the image.

{% highlight c# %}

Sprite blurredSprite = Sprite.Create(blurredTexture,
                                    new Rect(0, 0, blurredTexture.width, blurredTexture.height),
                                    new Vector2(0.5f, 0.5f));
image.sprite = blurredSprite;

{% endhighlight %}

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/blurRadius.png" title="Gaussian Blur Control" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    Gaussian Blur Control
</div>