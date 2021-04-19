---
title: cs131 lecture 12 visual recognition 
author: yanz
date: 2021-04-17 17:35:00 +0800
categories: []
tags: []
math: true
toc : true
---

## 常見視覺辨識任務
* Objection Detection
* Objection localization
* VQA(Visual Question Answering)

## Challenges && Nearest Neighbor Classifier

參考[cs231n Image Classification](https://yanzzzzzzzzz.github.io/posts/cs231n-Image-Classification/)



## Simple object recognition pipeline
參考 paper:[Analyzing Appearance and Contour Based Methods for Object Categorization](http://web-info8.informatik.rwth-aachen.de/media/papers/leibe-categorization-cvpr03.pdf)

建造一個架構，用來辨識影像，輸入影像後會輸出對應類別結果

![](/assets/img/post_img/Object-recognitionframework.png)


## 訓練架構

![](/assets/img/post_img/object-recognition-pipeline.png)

訓練階段重點：
* 訓練資料：輸入的訓練影像與標記類別
* 定義要擷取的影像特徵
* 訓練方法

### 訓練資料
dataset:[ETH-80 dataset](https://github.com/Kai-Xuan/ETH-80)

* 共有八類，每類41張影像，共有3280張影像
* 解析度1024 * 768 
* 但網路上找到的dataset並沒有到達這麼高的解析度(256 * 256)

![](/assets/img/post_img/eth80-dataset.png)

### 影像特徵
![](/assets/img/post_img/Image-features.png)

提到了幾個特徵提取方法
* Global RGB histogram
* 整體形狀分析：PCA-based methods
* 局部形狀特徵：[shape context](https://people.eecs.berkeley.edu/~malik/papers/BMP-shape.pdf)
* 紋理：Filter banks

### 訓練方法
可使用KNN classifier

### result

![](/assets/img/post_img/visual-recognition-result.png)