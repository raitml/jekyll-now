---
layout: post
title: Local Setup
---

In this post, we'll cover the steps necessary to setup a local instance. Unless you have a GPU or a [dedicated](https://medium.com/@andytwigg/building-a-deep-learning-machine-a48ae696801f) deep learning rig, it can be quite inefficient and kinda stupid to do any sort of deep learning on a local machine. Local instances can be very handy for debugging and for saving costs.

My workflow usually consists of writing code on my local environment, and then pushing it to the cloud instance. That way, I don't rack up a huge VM bill. 

The guide below is applicable to Linux/Mac OS workstations and won't work for Windows. I am working on a Windows guide and will update soon

The first step is to download [Anaconda](https://www.anaconda.com/download) Python 3.+ Graphical installer. It'll take a while to download (~500MB) so go get yourself a cup of coffee.

Once it is done downloading, the next step is to install the package. Depending on your OS, the instructions might differ and I strongly encourage that you go through the [Documentation](https://docs.anaconda.com/anaconda/install) to make sure you're doing it right. 

For Mac OS, the process is straightforward. Just grant the required privileges and it'll be done in no time.

The next step is to configure Anaconda. Start by opening up the Anaconda Navigator GUI. 
