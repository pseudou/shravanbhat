---
author: Shravan Bhat
title: Dark Image Processing for Glare-Prone Environments
description: Alogrithm to mitigate glare-induced Darkness
tags: ["python", "OpenCV"]
icon: fas map
layout: minimal
---

Noise is present in any imaging system, but it makes imaging particularly challenging in low light. High ISO can be used to increase brightness, but it also amplifies noise.Postprocessing, such as scaling or histogram stretching, can be applied, but this does not resolve the low signal-to-noise ratio (SNR) due to low photon counts. There are physical means to increase SNR in low light, including opening the aperture, extending exposure time, and using flash. But each of these has its own characteristic drawbacks. For example, increasing exposure time can introduce blur due to camera shake or object motion. The challenge of fast imaging in low light is wellknown in the computational photography community, but remains open. Researchers have proposed techniques for denoising, deblurring, and enhancement of low-light images. These techniques generally assume that images are captured in somewhat dim environments with moderate levels of noise. In contrast, we are interested in extreme low-light imaging with severely limited illumination (e.g., moonlight) and short exposure (ideally at video rate).

The following flowchart shown in Fig gives our approach on the implementation of the model.

<div class="col-6 mx-auto">{{< image src="img/flow.png" caption="Algorithm">}}</div>

**BRIGHTNESS FACTOR** 

In this section we load the image into the model. The image is then converted from its colour (i.e. RGB) format to gray scale format. To reduce or eliminate noise, the image is passed through a low pass Gaussian filter where the image Fig. 1. Recursion Algorithm is convolved with a seven by seven kernel of the Gaussian function. The image is then passed to a loop where it sums up all the kernel values of the image and divides it by a normalized value, to get the brightness factor of the image. This Factor is sent to the next section.


**THRESHOLD CONDITION**

A set of images are put through the algorithm to find the ideal output, by keeping the right threshold. This threshold is used to check if the image’s brightness factor goes above the threshold or not. If it does, then the recursion algorithm is broken and the Image goes to the output. If it doesn’t then it is passed to the next section.

**INCREASED ISO**

Now the original raw image is taken and each pixel value is multiplied by two so as to increase the ISO of the image since the image’s brightness factor is lesser than the threshold value. This value is then taken back to the calculation of brightness factor by gray-scaling the image and finding the brightness factor

**BRIGHT LIGHT REMOVAL**

The output image is then passed to this section. The image is passed through a threshold where pixels with high intensity are kept white and other pixel value is changed to black. Contour are drawn around the white pixel and the contour with the largest area is taken. Using the original image, the contour is filled with the pixel value around the contour and Gaussian filter is applied to smooth-en the image. The image is finally shown as the output

**RESULT**

<div class="col-6 mx-auto">{{< image src="img/comparison.png" caption="Result">}}</div>