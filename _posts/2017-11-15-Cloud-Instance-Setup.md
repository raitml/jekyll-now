---
layout: post
title: Cloud Instance Setup!
---

Hello!

The first step for Neural Networks any of us have to do is to setup a cloud instance/local machine. GPUs are the bread and butter for neural networks and an absolute must to achieve any kind of efficiency.

There are many options to choose from, including Crestle, Paperspace, GCP and AWS. For an overview on the same, please head to Sanyam Bhutani's excellent post comparing the different frameworks [here](https://medium.com/ai-saturdays/cloud-setup-tutorial-part-0-53d42dd4c733)

AWS and GCP have a generous free tier, so if you haven't already utilized those, head over and create an account right now!

To keep it simple and cost effective, we'll be covering two alternatives here: Crestle and GCP. 

So let's get started!

## Crestle

Crestle is the simplest alternative for setting up a GPU enabled cloud instance. There are no terminals to play around with, making the setup a breeze. 

Just head on over to [Crestle](https://www.crestle.com) and sign up for an account. Once the setup formalities are done, things get simpler.

Just use the GPU toggle button to switch on/off a GPU instance. Click on the 'Start Jupyter' button to head on over to your new jupyter notebook. You can also switch to a terminal session later on if you prefer.

![_config.yml]({{ site.baseurl }}/images/crestle.png) 

It's recommended to setup up an instance without the GPU, download all the necessary datasets and utility files. Once you're done, you can go back on and switch on the GPU to run the neural network *same paragraph*.

## GCP 

GCP is the Google Cloud Platform and is Google's answer to the mammoth that is AWS. GCP provides new accounts with a generous one year trial with 300$ credit that's very helpful for a beginner. Their GPU instances are also competitively priced and are always updated with the latest offerings from NVIDIA.

Unlike Crestle, GCP setup is a lot more complicated and requires multiple steps. We'll be covering the web GUI as it's easier to navigate for beginners.


