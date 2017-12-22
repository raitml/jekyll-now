---
layout: post
title: Local Setup
---

In this post, we'll cover the steps necessary to setup a local instance. Unless you have a GPU or a [dedicated](https://medium.com/@andytwigg/building-a-deep-learning-machine-a48ae696801f) deep learning rig, it can be quite inefficient and kinda stupid to do any sort of deep learning on a local machine. Local instances can be very handy for debugging and for saving costs.

My workflow usually consists of writing code on my local environment, and then pushing it to the cloud instance. That way, I don't rack up a huge VM bill. 

The guide below is applicable to Linux/Mac OS workstations and won't work for Windows. I am working on a Windows guide and will update soon

The first step is to download [Anaconda](https://www.anaconda.com/download) Python 3.+ Graphical installer. It'll take a while to download (~500MB) so go get yourself a cup of coffee.

![Anaconda]({{ site.baseurl }}/images/anaconda.png) 

Once it is done downloading, the next step is to install the package. Depending on your OS, the instructions might differ and I strongly encourage that you go through the [Documentation](https://docs.anaconda.com/anaconda/install) to make sure you're doing it right. 

For Mac OS, the process is straightforward. Just grant the required privileges and it'll be done in no time.

A general overview of Anaconda is provided [here](https://medium.com/ai-saturdays/basic-tutorials-part-3-4962731e808e)

The next step is to configure Anaconda. Start by opening up the terminal

```
conda update conda
conda update anaconda
conda update scikit-learn
```

Next, create a separate conda environment so it's easier to keep track of dependencies

```
conda create --name myenv 
```
Replace **myenv** with the name you choose. Change Python version to the installed version

To verify the environment creation

```
conda list
```

If your environment shows up in there, it's been created and configured properly

Now, activate the created environment

```
source activate myenv [Linux and Mac OS]
activate myenv [Windows]
```

Next up, we need to download all the required dependencies into the environment. 

Enter the environment and install the required dependencies
```
source activate myenv
pip install -r requirements.txt
```

The *requirements.txt* file can be obtained by using the following command
```
wget https://raw.githubusercontent.com/fastai/courses/master/requirements.txt
```

This should install all the required dependencies that are necessary for setup. If there are any that I've left out, use the following syntax to install
```
conda install -n myenv package_name
``` 

The package_name reflects the package you want to install and myenv is your environment name

To install Tensorflow
```
conda install -c conda-forge tensorflow
```

Verify the installation by executing the following within the environment

```
import tensorflow
print('tensorflow: %s' % tensorflow.__version__)
```

This should setup the local environment. If you're stuck, go through the [Anaconda](https://conda.io/docs/index.html) documentation or ask on the comments below

In the next post, we'll look at building a simple Neural Network from scratch using NumPy. 

Cheerios. And keep learning deep.

![Deep Learning]({{ site.baseurl }}/images/dl.png)
