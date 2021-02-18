---
title: cs131-lecture-3-Filters-and-convolutions
author: yanz
date: 2021-02-18 16:32:00 +0800
categories: [course]
tags: [cs131]
math: true
toc : true
---

## 概述
> What is filtering：Forming a new image whose pixel values are transformed
from original pixel values

影像處理中的濾波：把原來影像像素值透過某種轉換組合成新的影像

## 目標
* 從影像中取出有用的訊息或轉換影像屬性
    * 擷取特徵：edge, corners, blobs detection...
    * 其他應用：超解析度成像super-resolution, 影像修復in-painting, 去噪de-noising

![](/assets/img/post_img/feature-in-filtering.png){: width="800"}

![](/assets/img/post_img/feature-in-filtering_1.png){: width="800"}

## convolution & correlation
convolution 公式：

![](/assets/img/post_img/2D-Discrete-Convolution.png){: width="400"}


correlation 公式：

![](/assets/img/post_img/correlation.png){: width="400"}

compare with convolution & correlation

![](/assets/img/post_img/convolution-cross-correlation.png){: width="400"}


convolution的符號是$$ f*g $$，correlation的符號是$$ f**g $$
convolution先對filter mask做轉置再做correlation


## 參考
[影像修復matlab example](https://la.mathworks.com/help/images/ref/inpaintexemplar.html)

