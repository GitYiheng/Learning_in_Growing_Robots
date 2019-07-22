[![Video_Clip_Thumbnail](images/video_clip_thumbnail.PNG)](https://youtu.be/2-Y8vzH2t5g)

# Learning in Growing Robots: Knowledge Transfer from Tadpole to Frog Robot

This is a part of an ongoing project exploring the relation between varying structure and learning. We use the growing process from a tadpole to a frog as the model. The task is to swim to a randomly generated target position. Between different growing stages, weights of both the policy and value networks are directly transferred. In this way, better parameter initialization provides an initial performance boost and accelerates convergence. It is interesting to see that transfer learning is beneficial even with robots with different structures.

Preliminary results can be found in [Learning in Growing Robots: Knowledge Transfer from Tadpole to Frog Robot](https://link.springer.com/chapter/10.1007/978-3-030-24741-6_42) 

# Installation

This is only tested in Windows 10.

## Step 1 Install Unity

Unity 2017.4.1 (version is important): https://unity3d.com/get-unity/download/archive

## Step 2 Install Anaconda

Python 3.6.8 (Anaconda 4.5.12): https://www.anaconda.com/distribution/

## Step 3 Install Tensorflow

Open Anaconda Prompt and type

```
conda create -n growvenv python=3.6
activate growvenv
pip install tensorflow==1.7.1
```

## Step 4 Install ML-Agents Toolkit
