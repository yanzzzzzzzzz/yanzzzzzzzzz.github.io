
* filtering 在做甚麼事情
    * 把原來影像像素值透過某種轉換組合成新的影像
* filtering的目標、解決的問題、應用
    * 從影像中取出有用的訊息或轉換影像屬性
        * 特徵:edge, corners, blobs...
        * 超像素super-resolution, 影像修復in-painting, 去噪de-noising
* filter的應用範例與結果
    * moving average
    * threshold
* 系統可以根據其屬性進行分類
    * 空間特性 -位移不變性

* 位移不變性系統

##  filtering

### 概述
> What is filtering：Forming a new image whose pixel values are transformed
from original pixel values

影像處理中的濾波：把原來影像像素值透過某種轉換組合成新的影像

### 目標
* 從影像中取出有用的訊息或轉換影像屬性
    * 擷取特徵：edge, corners, blobs detection...
    * 其他應用：超解析度成像super-resolution, 影像修復in-painting, 去噪de-noising

![](/assets/img/post_img/feature-in-filtering.png){: width="400"}

![](/assets/img/post_img/feature-in-filtering_1.png){: width="400"}


## 參考
[影像修復matlab example](https://la.mathworks.com/help/images/ref/inpaintexemplar.html)

