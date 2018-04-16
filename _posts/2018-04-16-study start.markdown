---
layout: post
title:  "Featured Image"
date:   2018-04-16
image: touring.jpg
---

<p class="intro"><span class="dropcap">L</span>먼가 써봄.</p>

Learning Structured Sparsity in Deep Neural
Networks

High demand for computation resources severely hinders deployment of large-scale
Deep Neural Networks (DNN) in resource constrained devices. In this work, we
propose a Structured Sparsity Learning (SSL) method to regularize the structures
(i.e., filters, channels, filter shapes, and layer depth) of DNNs. SSL can: (1) learn
a compact structure from a bigger DNN to reduce computation cost; (2) obtain a
hardware-friendly structured sparsity of DNN to efficiently accelerate the DNN’s
evaluation. Experimental results show that SSL achieves on average 5.1 and
3.1 speedups of convolutional layer computation of AlexNet against CPU and
GPU, respectively, with off-the-shelf libraries. These speedups are about twice
speedups of non-structured sparsity; (3) regularize the DNN structure to improve
classification accuracy. The results show that for CIFAR-10, regularization on
layer depth reduces a 20-layer Deep Residual Network (ResNet) to 18 layers while
improves the accuracy from 91.25% to 92.60%, which is still higher than that of
original ResNet with 32 layers. For AlexNet, SSL reduces the error by  1%.
Introduction
Deep neural networks (DNN), especially deep Convolutional Neural Networks (CNN), made remarkable
success in visual tasks [1][2][3][4][5] by leveraging large-scale networks learning from a
volume of data. Deployment of such big models, however, is computation-intensive. To reduce
computation, many studies are performed to compress the scale of DNN, including sparsity regularization
[6], connection pruning [7][8] and low rank approximation [9][10][11][12][13]. Sparsity
regularization and connection pruning, however, often produce non-structured random connectivity
thus, irregular memory access that adversely impacts practical acceleration in hardware platforms.
Figure 1 depicts practical layer-wise speedup of AlexNet, which is non-structurally sparsified by
norm. Compared to original model, the accuracy loss of the sparsified model is controlled within
Because of the poor data locality associated with the scattered weight distribution, the achieved
speedups are either very limited or negative even the actual sparsity is high, say, >95%. We define
sparsity as the ratio of zeros in this paper. In recently proposed low rank approximation approaches,
DNN is trained first and then each trained weight tensor is decomposed and approximated by a
product of smaller factors. Finally, fine-tuning is performed to restore the model accuracy. Low rank
approximation is able to achieve practical speedups because it coordinates model parameters in dense
matrixes and avoids the locality problem of non-structured sparsity regularization. However, low
approximation can only obtain the compact structure within each layer, and the structures of the
layers are fixed during fine-tuning such that costly reiterations of decomposing and fine-tuning are
required to find an optimal weight approximation for performance speedup and accuracy retaining.