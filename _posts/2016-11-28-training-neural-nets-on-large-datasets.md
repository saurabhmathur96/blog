---
layout: post
title:  "Lessons learned from training neural nets on large datasets"
date:   2016-11-28
categories: machine-learning
---

This semester I have been trying to understand deep learning. Along the way I tried to implement some of the algorithms
and use them to classify images.

Since one of the main advantages of deep learning is that performance improves 
linearly with data - having to deal with large amount of data 
was inevitable. By large I do not mean the humongous datasets that are generally associated with distributed computing
and such - I mean the kind of datasets that just fit into your RAM specifically the CIFAR-10 object recognition dataset.


## 0 : The setup
I started off using my own thinkpad having 4GB RAM and running on an intel i3 processor. Later, I switched to
an Azure A4 virtual machine as training deep neural nets is a memory hungry task and rendered my system unusable.

## 1 : Sample and test !
One of the mistakes that I made was going all guns blazing and using the entire dataset for training everytime 
I made a change to the model. So, I ended up waiting as long as an entire day to find out that a learning rate of 0.01 is
too high. Tuning the number and types of layers was a nightmare.

A better way is to use a sample of the data and tune the hyper-parameters accordingly.

## 2 : Use background processes
Daemons are long running background processes that keep running even if interactive sessions such a the terminal window
are exited.
I used `nohup` to create background processes on the VM on Azure.

```
nohup th train_cifar10.lua < /dev/null > ./log.txt 2>&1 &
```

This was especially useful when I actually wanted to train the model on a larger portion of the training data. The advantage here being I don't need to be sshed into
the machine - I can login after some time and check if training has finished.

## 3 : Don't reinvent the wheel
There are a lot of standard architectures and pre-trained models based on those architectures available. It is even possible
to retrain just the final layer to reuse the image representations previously learnt. Examples of this are the Inception-v3 model
available for tensorflow and many other pretrained models for Torch.

## 4 : Choose the right deployment framework 
Since, most machine learning libraries use low level bindings to speed up computation, 
cross platform compatibility is a nightmare.

I use the free tier of heroku to experiment with web-apps and getting sklearn and numpy to work there was an 
arduous process. Also, the pickles of models trained using one version of sklearn are not guaranteed to work with all other versions.
Tensorflow has better compatibility and it was easier to deploy owing to better support of Google's Protocol Buffers
to save and load trained models. Here is a web-app that compares some neural nets on handwritten digit classification 
that I made using Flask and Tensorflow - [https://classifier-mnist.herokuapp.com/](https://classifier-mnist.herokuapp.com/).


Azure Machine Learning provides a simple interface to deploying custom and pre-built models as predictive services.