---
author: Shravan Bhat
title: Image Quality Enhancement
description: Deep Learning Methods for Quality Enhancement of Satellite Remote Sensing Images
tags: ["python", "Deep Learning", "PyTorch"]
icon: fas map
layout: minimal
---

Satellite images often suffer from poor illumination caused by environmental factors, smog, and unpredictable weather conditions. This leads to insufficient saturation, low contrast, and a decline in visual quality, negatively impacting the performance of computer vision algorithms.

To address this issue, I explore the potential of Deep Neural Networks for low light enhancement. My approach involves training a lightweight deep network to estimate pixel-wise and high-order curves for dynamic range adjustment in images. The specially designed curve estimation takes into account factors like pixel value range, monotonicity, and differentiability. My method does not rely on paired or unpaired data during training. Instead, I utilize a set of carefully formulated non-reference loss functions that implicitly measure enhancement quality and guide the network's learning process.

I have also provided a comprehensive walkthrough of the code, ensuring that this project can be easily reproduced and reused by others.

<a href="NNDL_project.ipynb" download>Download Code</a>

The below tables provides a comparison of the model with GladNet and Retinex models, which are two different image enhancement techniques.
<div class="col-6 mx-auto">{{< image src="img/table.JPG" caption="Results of different illumination Models on NITK university images">}}</div>


**Comparision of Metrics**

| #  | Architecture | PSNR  | SSIM | MAE   | Parameters | FLOPs  |
| -- | ------------ | ----- | ---- | ----- | ---------- | ------ |
| 1. | GladNet      | 15.46 | 0.48 | 107.58 | 931,523    | 18.37G |
| 2. | RetinexNet   | 15.99 | 0.53 | 104.81 | 444,613    | 13.54G |
| 3. | Presented Model    | 15.79 | 0.50 | 106.46 | 79,416     | 5.21G  |
{.table .table-bordered .border-secondary}

The table presents a comparison of three different image enhancement architectures: GladNet, RetinexNet, and Presented Model. Each architecture is evaluated based on four performance metrics: Peak Signal-to-Noise Ratio (PSNR), Structural Similarity Index (SSIM), Mean Absolute Error (MAE), as well as the number of model Parameters and Floating-Point Operations (FLOPs).

Among the three architectures, RetinexNet achieved the highest PSNR of 15.99 and the highest SSIM of 0.53, indicating superior image enhancement quality compared to the other models. However, Presented Model demonstrated a competitive performance with a PSNR of 15.79 and SSIM of 0.50, while also requiring significantly fewer parameters (79,416) and FLOPs (5.21G). Both GladNet and Presented Model have slightly higher MAE values compared to RetinexNet, but Our Model strikes a balance between computational efficiency and image enhancement effectiveness.
