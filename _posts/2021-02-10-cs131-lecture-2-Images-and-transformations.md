---
title: cs131-lecture-2-Images-and-transformations
author: yanz
date: 2021-02-10 11:10:00 +0800
categories: [course]
tags: [cs131]
math: true
toc : true
---

## 數位影像的類別
![](/assets/img/post_img/image-type.jpg){: width="400"}

* Binary ： 二值化影像，影像像素值非0即1，在影像顯示中0表示黑色、1代表白色
* Grayscale ： 灰階影像，影像像素值在`[0~255]`之間，像素值越
* Color ： 彩色影像，常見的是RGB和CMYK，RGB彩色影像是由紅、綠、藍三個色彩通道組合而成。CMYK則是由青色(Cyan)、洋紅色(Magenta)、黃色(Yellow)、黑色(blacK)四個通道組成。

![](/assets/img/post_img/rgb-cmyk.jpg){: width="400"}

## 影像解析度
* dpi：Dots Per Inch，每英寸點數，dpi的數值越高，所輸出的解析度就越高，常用在印表機上的設定
![](/assets/img/post_img/resolution.jpg){: width="400"}

## 影像轉換

### 變換矩陣 transformation matrix

* 對原x,y座標進行縮放

![](/assets/img/post_img/transformation-matrices.png){: width="400"}


* 角度轉換

![](/assets/img/post_img/rotate-matrix.png){: width="400"}

矩陣可以做多重轉換：

$$ p'=R_2R_1Sp $$

其中p是座標點，$$R_1 R_2 是角度轉換矩陣，S是縮放矩陣，p'是轉換後的座標點$$

多重轉換的細節：
* 矩陣變換是由右到左做變換
* 上列式子與 $$ p'=R_2(R_1(Sp)) $$ 相等
* 也與$$ p'=(R_2R_1S)p $$ ，先做矩陣變換運算，再與座標變換

### 齊次坐標 Homogeneous coordinates
* 變換矩陣可以做縮放、旋轉，但卻不能加上常量進行平移
* 解決方法：每個向量末端加上"1"

![](/assets/img/post_img/add-one-in-vector.png){: width="400"}

新的轉換矩陣可以旋轉、縮放，還可以平移了，讚

齊次坐標上的除法
* 我們也許想透過除法的方式達到縮放的效果，但實際上矩陣運算並不能直接做除法運算
因此將他轉換為齊次座標，再進行除法運算

用圖片來解釋比較清楚：
有個座標點為$$ [x, y] = [15, 21] $$，今天想將它縮小3倍，
我們透過齊次座標的方式把$$[x, y]$$改寫成$$[x, y, w] = [15, 21, 3]$$
其中的$$W$$把它想像成是我們的投影機距離
![](/assets/img/post_img/Homogeneous-coordinates-divide.png){: width="400"}

將整個矩陣除與3，$$[ \frac{15}{3}, \frac{21}{3}, \frac{3}{3}] = [5, 7, 1]$$
就是在上面的圖片中將投影機向前推進到$$W=1$$的位置
![](/assets/img/post_img/Homogeneous-coordinates-divide-1.png){: width="400"}


因此座標位置也跟著等比例縮小了

#### 2D座標平移、縮放、旋轉
![](/assets/img/post_img/shift-roate-scaling.png){: width="400"}

## 參考
[CS131 Computer Vision: Foundations and Applications](http://vision.stanford.edu/teaching/cs131_fall2021/index.html)

[写给大家看的“透视除法” —— 齐次坐标和投影](https://www.jianshu.com/p/7e701d7bfd79)