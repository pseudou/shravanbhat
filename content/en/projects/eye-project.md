---
author: Shravan Bhat
title: Eye Tracker based Wheelchair Control Algorithm
date: 2021-07-15
updated: 2023-07-12
description: A cost-effective eye tracker based wheelchair control algorithm for people with Quadriplegia
tags: ["python", "Deep Learning", "IoT"]
icon: fas eye
layout: minimal
---

The project focuses on addressing the mobility challenges faced by individuals with quadriplegia, a condition characterized by paralysis in the lower body and parts of the upper body. Traditional wheelchair control systems, such as mechanical or electric motors with joysticks, are unsuitable for quadriplegic patients who lack hand dexterity. However, eye movement control remains intact even in patients with brain and spinal cord injuries. Thus, we propose a cost-effective solution that utilizes eye movement tracking to generate control signals for wheelchairs, offering improved mobility and independence for individuals with quadriplegia.

Additionally, we aimed to optimize the solution's efficiency and reduce costs by designing a complete wheelchair system using a car bot, which emulates the functionality of a traditional wheelchair. Our research paper has been submitted to the internationally journal, Expert Systems With Applications, published by Elsevier. The journal has a CiteScore of 12.6 and an impact factor of 8.5. Currently, the paper is under review, showcasing our commitment to contributing to the field.

<div class="col-6 mx-auto">{{< image src="img/HLD.jpg" >}}</div>

Our project consists of two main components: a prediction model and a control signal flow. For the prediction model, we employed a CNN-based deep learning approach. To train the model, we utilized a dataset of eye images, accessible through the provided link. The dataset includes images of eyes in various directions, such as left, right, up, down, and straight. We trained multiple CNN architectures, comparing their performance metrics to identify the most suitable model for our task.

Additionally, we proposed a control flow structure that grants users the flexibility to move manually when needed, while also enabling them to control their wheelchair using their eye movements. In the project, using the proposed CNN model we control the bot movements.  The Trained CNN model and the control flow architecture would be running on a RPi microprocessor which would be controling the bot.

More comprehensive details regarding the project will be available after the research paper is published. An early version of the research can be accessed on the <a href="https://arxiv.org/abs/2207.10511">arxiv preprint website</a>. 

The data collected by us is available in <a href="https://data.mendeley.com/datasets/vy4n28334m/1">Mendeley Data</a>
