---
title: cs131 lecture 6 Feature Descriptors-Laplacian & DoG
author: yanz
date: 2021-03-10 14:55:00 +0800
categories: [course]
tags: [cs131]
math: true
toc : true
---

# 問題
Harris corner 沒有尺度不變性

![](/assets/img/post_img/harris-corner-scale-invariant.png)

在不同尺度下所呈現的角點響應函數都不同，Image 1的最小圓圈範圍是跟Image 2最大圓圈範圍才會有相同的角點結果

# 解決方法

![](/assets/img/post_img/scale-selection.png)

希望能設計一個scale invariant detection function可以讓每張影像都找得到一個穩定的尖峰，才能在多尺度搜尋時找到相同的結果

## Scale Invariant Detection

使用Laplacian與Difference of Gaussians kernel來對影像進行不同尺度的縮放

### Laplacian kernel

$$L = \sigma^2(G_{xx}(x,y,\sigma)+G_{yy}(x,y,\sigma))$$

![](/assets/img/post_img/Laplacian-kernel.png)

其中G是高斯函數

$$G(x,y,\sigma)=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{x^2+y^2}{2\sigma^2}}$$

###  Difference of Gaussians(DoG)

$$DoG = G(x,y,k{\sigma}) - G(x,y,{\sigma}) $$


![](/assets/img/post_img/DoG.png)

對影像逐漸加深模糊度，越模糊所保留的細節越少
高斯差所得到的影像細節隨著$$\sigma$$越大細節越粗糙

## Scale Invariant Detections

![](/assets/img/post_img/scale-invariant-detectors.png)

* Harris-Laplacian:結合Laplacian kernel的harris corner，並取出局部最大值作為結果
* SIFT:使用DoG並對每個點取3x3x3鄰居26個點(不包含自己)，找出高斯差最小的數值