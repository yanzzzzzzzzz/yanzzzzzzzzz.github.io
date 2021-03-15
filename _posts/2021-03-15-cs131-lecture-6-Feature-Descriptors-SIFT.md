---
title: cs131 lecture 6 Feature Descriptors-SIFT
author: yanz
date: 2021-03-15 16:30:00 +0800
categories: [course]
tags: [cs131]
math: true
toc : true
---

我們在上一回找到了角點，但如何利用關鍵點的周圍資訊，來讓彼此匹配，也許可以把角點周圍的像素區塊取出來匹配，但如果遇到兩張影像角度不同時如何匹配?

# SIFT descriptor(SIFT=Scale-Invariant Feature Transform)
建構一個旋轉不變性描述子
* 從DoG得到一個帶有尺度不變性的關鍵點
* 從關鍵點周圍資訊找出特徵角度(不直接旋轉個別影像區塊進行匹配，因為很慢)

![](/assets/img/post_img/keypoint-neightborhood.png)


## SIFT流程

![](/assets/img/post_img/gradient-direction.png)

使用影像梯度計算關鍵點周圍的角度直方圖，並把角度切成八等分

![](/assets/img/post_img/gradient-direction-1.png)

把關鍵點周圍梯度值每4x4為一群，個別計算旋轉過的梯度方向直方圖
梯度的貢獻程度取決於距離，如果它在兩個直方圖位置的中間，它給兩個直方圖一半的貢獻

![](/assets/img/post_img/descriptor-parameter.png)

梯度直方圖的方向分為8份與每個區塊為4x4是由作者選出最佳的參數結果

* 8方向的直方圖，4x4個直方圖陣列，會有8x4x4=128個向量
* SIFT描述子是一個長度為128的向量，並有帶有旋轉不變性與尺度不變性
* 可以比較影像A與影像B的各自的向量來尋找配對的關鍵點
* 很大的影像梯度通常來自3D照明效果(如：眩光)，將128維向量最大數值限制在0.2內，計算完後再進行正規化(乘上256)

## SIFT 測試結果

![](/assets/img/post_img/noise.png)

在隨機改變影像尺度、角度，再加上一定的noise的dataset下的特徵比對結果

![](/assets/img/post_img/stability.png)

在隨機改變影像尺度、角度、仿射變換並加入2%的noise的dataset，對30000個特徵進行最鄰近點搜尋的結果，測試穩定性

![](/assets/img/post_img/Distinctiveness.png)

對測試資料進行30度的仿射變換與2%的noise後提取特徵點，計算單點最鄰近搜尋的準確率

## SIFT 結論
* SIFT是一個具有尺度不變性、旋轉不變性，並具有獨特性的關鍵點提取方法
* 有效率的計算速度，可以在一般的PC上做到接近即時處理的效果
* 論文中也展示使用關鍵點加上最鄰近搜尋來進行物件檢測


## 參考
* [David G. Lowe,"Distinctive Image Features from Scale-Invariant Keypoints"," International Journal of Computer Vision, 60, 2 (2004), pp. 91-110](https://people.eecs.berkeley.edu/~malik/cs294/lowe-ijcv04.pdf)
* [wiki-尺度不變特徵轉換](https://zh.wikipedia.org/wiki/%E5%B0%BA%E5%BA%A6%E4%B8%8D%E8%AE%8A%E7%89%B9%E5%BE%B5%E8%BD%89%E6%8F%9B)