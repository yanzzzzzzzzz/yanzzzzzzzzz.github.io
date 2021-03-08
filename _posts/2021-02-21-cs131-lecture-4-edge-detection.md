---
title: cs131 lecture 4 Edge Detection
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

## edge detector 

好的edge detector應避免這些事情發生
* Poor robustness to noise：對noise抵抗能力低
* Poor localization：與真實edge位置仍有小幅度差距
* Too many responses：檢出太多不必要edge

![](/assets/img/post_img/bad-edge-detector.png)

### Sobel edge detector

Sobel Operator 

![](/assets/img/post_img/sobel-operator.png)

由`高斯平滑 + 一階微分` 組成

![](/assets/img/post_img/sobel-operator-explain.png)

gradient magnitude & gradient direction

![](/assets/img/post_img/sobel-magnitude-direction.png)


![](/assets/img/post_img/sobel-result.png)

缺點
* 準確率差，誤判率高
* 對noise敏感


### Canny edge detector

詳見[canny-edge-detector](https://yanzzzzzzzzz.github.io/posts/canny-edge-detector/)

## Line Detection
直線是一個很常見的特徵，例如在建築物、道路、零件電路板等都看得到
從edge資訊更進一步找出直線
### Naïve method

![](/assets/img/post_img/line-detection.png)

對影像中的edge點任取兩個點，檢查在此點形成的線上是否有其他edge點
當點數量大於一定值時，視為真正的直線
缺點：
* 時間複雜度為$$ O(N^2) $$ ，N為edge數量

### Hough transform
與蠻力法相似，用投票的方式來找出合適的線段
但不同的地方在於使用hough space將直線透過另一種公式做轉換

####　Hough space
直線方程式
$$ y=ax+b $$(1)
但這個方程式(1)不能表示垂直的線段

$$ r = xcos \theta + ysin \theta $$ (2)

![](/assets/img/post_img/hough-space.png)

因此由公式(2)可以簡單的改變$$ \theta $$ 值組合出多種不同角度的直線

![](/assets/img/post_img/hough-space-1.png)

單個edge點(x,y)在$$ [r,\theta] $$ hough space下所呈現多條直線的結果為

![](/assets/img/post_img/hough-space-2.png)

可以看到單個點在$$ [r,\theta] $$空間下畫出一條彎曲線


加上不同edge座標點，可以在hough space下畫出多條彎曲線
並且有疊加交點，而此交點正好是兩點所形成的直線$$ [r, \theta] $$

![](/assets/img/post_img/hough-space-3.png)


可篩選交點數較多的點為真實直線，也可以篩選指定直線角度範圍

![](/assets/img/post_img/hough-transform.png)


優點：
* 概念簡單，好實現
* 相同概念也可以用在[檢測圓形](https://youtu.be/Ltqt24SQQoI?t=185)

缺點：
* 只得到直線角度資訊，沒有直線長度資訊


## 補充

### 消失點 vanishing point

![](/assets/img/post_img/vanishing-point.png){: width="600" height="300"}

消失點是三維空間中所有平行線相交的交點。
消失點的應用在檢測道路上有很大的幫助，在二維影像中車道最終會在消失點相交，但真實空間的車道是平行的。
透過edge尋找消失點，進行道路檢測。

[VPGNet: Vanishing Point Guided Network for Lane and Road Marking Detection and Recognition ICCV2017-用DeepLearning 進行消失點檢測影片](https://youtu.be/jnewRlt6UbI)

## 參考

[Line Detection by Hough transformation](http://web.ipac.caltech.edu/staff/fmasci/home/astro_refs/HoughTrans_lines_09.pdf)