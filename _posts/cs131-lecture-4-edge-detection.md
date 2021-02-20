# edge detection 

目標: 從圖片中找到亮度突然變化的地方
* 大部分的形狀等資訊可以從邊緣分析出來
* 用edge來提取資訊、辨識物件
* 回復幾何形狀與消失點(vanishing point)



* edge 常見特性

* 1d 2d 離散微分


補充：
消失點 vanishing point
![](/assets/img/post_img/vanishing-point.png)

消失點是三維空間中所有平行線相交的交點。
消失點的應用在檢測道路上有很大的幫助，在二維影像中車道最終會在消失點相交，但真實空間的車道是平行的。
透過edge尋找消失點，進行道路檢測。
[VPGNet: Vanishing Point Guided Network for Lane and Road Marking Detection and Recognition ICCV2017-用DeepLearning 進行消失點檢測影片](https://youtu.be/jnewRlt6UbI)
