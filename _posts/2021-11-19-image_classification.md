---
layout: single
title: "Image Classification"
date: 2021-11-19 12:00:00 -0000
categories: neural network (nn) Convolutional nets  transfer learning  
excerpt: Classifying images using series of neural networks. 
---

In this project, we classify seires of images into ten classes using multi-layer perceptron, conveloutional neural network, and by using transfer learning from a pre-trained model (Inception). 

 
 <div align="center">
  <img src="/assets/images/blogs/ten_classes.png" width="600px" height="240" alt="Photo of a lighthouse.">
  <p>Ten sample images representing ten classes</p>
 </div>

## Transfer learning 
We used tranfer learning from the pre-trained *Inception* model. During the traing all the layers of the pre-trained model are frozen (will not train). In other words, the pre-trained model is utilized as feature extractor preprocessor.

<div align="center">
  <img src="/assets/images/blogs/pred_labels.png" width="500px" height="200" alt="Photo of a lighthouse.">
</div>