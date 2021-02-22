---
title: cs131-lecture-4-edge-detection
author: yanz
date: 2021-02-21 23:37:00 +0800
categories: [course]
tags: [cs131]
math: true
toc : true
---

## edge 的重要性
* 大部分的形狀等資訊可以從邊緣分析出來
* 用edge來提取資訊、辨識物件
* 回復幾何形狀與消失點(vanishing point)



## edge產生原因
* 表面法向不連續性(Surface normal discontinuity)：區塊內看到多個不同角度的表面
* 深度不連續性 (Depth discontinuity)：由物體前後距離不一所產生邊緣
* 表面顏色不連續性 (Surface color discontinuity)：物體改變顏色，例如材質顏色改變
* 亮度不連續性 (Illumination discontinuity)：陰影，光線亮度變化

![](/assets/img/post_img/edge-origin.png)

## 邊緣檢測在一階微分應用
edge detection Using First/Second Derivative

![](/assets/img/post_img/edge-in-derivatives.png)

透過一階微分找出亮度變化大的地方
### First Derivative

1D function：

![](/assets/img/post_img/1d-derivatives.png)

2D function：

![](/assets/img/post_img/edge-in-derivatives-2d-function.png)

轉換成2D mask/filter

![](/assets/img/post_img/gx-in-2d-derivative.png)

![](/assets/img/post_img/gy-in-2d-derivative.png)


* gradient vector：對x,y方向進行偏微分，也就是用上述兩個Gx, Gy的mask個別對影像進行convolution
* gradient magnitude：透過x,y方向梯度的加總得到最終梯度強度
* gradient direction：gradient vector中gradient變化量最大的角度

![](/assets/img/post_img/gradient-vector.png)

## noise對edge detection的影響
* noise對邊緣檢測的影響不大
* 若有較大的影響可以考慮先對影像進行平滑運算
    * Median filter
    * Gaussian filter
    * Bilateral filter

Tradeoff：影像模糊度越強，noise越少，但edge也會被模糊掉


補充：
消失點 vanishing point
![](/assets/img/post_img/vanishing-point.png){: width="400" height="400"}

消失點是三維空間中所有平行線相交的交點。
消失點的應用在檢測道路上有很大的幫助，在二維影像中車道最終會在消失點相交，但真實空間的車道是平行的。
透過edge尋找消失點，進行道路檢測。
[VPGNet: Vanishing Point Guided Network for Lane and Road Marking Detection and Recognition ICCV2017-用DeepLearning 進行消失點檢測影片](https://youtu.be/jnewRlt6UbI)
