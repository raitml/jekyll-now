---
layout: post
title: Cloud Instance Setup
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

![Crestle setup]({{ site.baseurl }}/images/crestle.png) 

It's recommended to setup up an instance without the GPU, download all the necessary datasets and utility files. Once you're done, you can go back on and switch on the GPU to run the neural network *same paragraph*.

## GCP 

GCP is the Google Cloud Platform and is Google's answer to the mammoth that is AWS. GCP provides new users with a generous 300$ credit that comes in handy for beginners. Their GPU instances are also competitively priced and updated with the latest offerings from NVIDIA.

Unlike Crestle, GCP setup is a lot more complicated and requires multiple steps. We'll be covering the web GUI as it's easier to navigate for beginners.

The first step is to log into the Google cloud consolse and choose a project(setup a new one if you don't have one). Navigate to the compute engine and setup a new VM instance. 

  1. 4 CPU cores and 16 GB RAM
  2. Using the customize option, select a single Tesla K80 GPU(you might need to provision it if you get an error)
  3. Change boot disk to Ubuntu 16.04 LTS with 10 GB memory
  4. Check option for HTTP and HTTPS traffice
  
 If you're using the gcloud command line tool, there's also a handy option to generate the equivalent gcloud command :-)
 
Once the instance is ready, connect to it via the shell or use the gcloud command to connect via ssh from the local machine

Once logged into the machine, it's time to setup the development environment. This is why Crestle is so easy as all the setup is already pre-configured 

```
sudo apt-get update install
sudo apt-get --assume-yes upgrade
sudo apt-get --assume-yes install tmux build-essential gcc g++ make binutils
sudo apt-get --assume-yes install software-properties-common
```

The next step is to download and install the CUDA drivers for the NVIIDA GPUs. Use the following script 

```
#!/bin/bash
echo "Checking for CUDA and installing."
# Check for CUDA and try to install.
if ! dpkg-query -W cuda-8-0; then
  # The 16.04 installer works with 16.10.
  curl -O http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/cuda-repo-ubuntu1604_8.0.61-1_amd64.deb
  dpkg -i ./cuda-repo-ubuntu1604_8.0.61-1_amd64.deb
  apt-get update
  apt-get install cuda-8-0 -y
fi
```

To verify the installation, run the following code
```
nvidia-smi -pm 1
```

You should get the following as output

![SMI install verification]({{ site.baseurl }}/images/smi.png) 

The next step is to download the [cuDNN](https://developer.nvidia.com/cudnn) library which is especially designed to speed up NN calculations on NVIDIA GPUs. Download the latest cuDNN package for CUDA 8.0

#install cudnn libraries
```
wget "http://files.fast.ai/files/cudnn.tgz" -O "cudnn.tgz"
tar -zxf cudnn.tgz
cd cuda
sudo cp lib64/* /usr/local/cuda/lib64/
sudo cp include/* /usr/local/cuda/include/
```

Alas, we're not done yet! The next step is to download the Anaconda distribution and th Keras libraries
```
cd ~
mkdir downloads
cd downloads
wget "https://repo.continuum.io/archive/Anaconda2-4.2.0-Linux-x86_64.sh" -O "Anaconda2-4.2.0-Linux-x86_64.sh"
bash "Anaconda2-4.2.0-Linux-x86_64.sh" -b
```

Setup the Anaconda path variables 
```
echo "export PATH=\"$HOME/anaconda2/bin:\$PATH\"" >> ~/.bashrc
export PATH="$HOME/anaconda2/bin:$PATH"
conda install -y bcolz
conda upgrade -y --all
```

To install and configure Keras
```
pip install keras==1.2.2
mkdir ~/.keras
echo '{
    "image_dim_ordering": "th",
    "epsilon": 1e-07,
    "floatx": "float32",
    "backend": "tensorflow"
}' > ~/.keras/keras.json
```

To install Tensorflow
```
sudo apt-get install python-dev python-pip libcupti-dev
sudo pip install tensorflow-gpu
```

For troubleshooting, follow this guide on [GitHub](https://github.com/eshvk/gcp-dl)

Phew! That was a lot of command line hassling. Crestle did all that in one go, whereas Google gives 300$ worth of credit to play around with so choose your pick.

Remember to **shut down the instance when you're done** working or you'll be left with a hole in your pocket.
