

# SIFT描述子介紹

我們在上一回找到了角點，但如何利用關鍵點的周圍資訊，來讓彼此匹配
也許可以把角點周圍的像素區塊取出來匹配，但如果遇到兩張影像角度不同時如何匹配?


## SIFT descriptor(SIFT=Scale-Invariant Feature Transform)
建構一個旋轉不變性描述子
* 從DoG得到一個帶有尺度不變性的關鍵點
* 從關鍵點周圍資訊找出特徵角度(不直接旋轉個別影像，因為很慢)

![](/assets/img/post_img/keypoint-neightborhood.png)


### SIFT流程

![](/assets/img/post_img/gradient-direction.png)

計算角度直方圖，把角度切成八等分

![](/assets/img/post_img/gradient-direction-1.png)

把關鍵點周圍梯度值每4x4為一群，個別計算旋轉過的梯度方向直方圖
梯度的貢獻程度取決於距離，如果它在兩個直方圖位置的中間，它給兩個直方圖一半的貢獻


![](/assets/img/post_img/descriptor-parameter.png)

梯度直方圖的方向分為8份與每個區塊為4x4是由作者選出最佳的參數結果

* 8方向的直方圖，4x4個直方圖陣列，會有8x4x4=128個向量
* SIFT描述子是一個長度為128的向量，並有帶有旋轉不變性與尺度不變性
* 可以比較影像A與影像B的各自的向量來尋找配對的關鍵點

## 參考
[David G. Lowe,"Distinctive Image Features from Scale-Invariant Keypoints"," International Journal of Computer Vision, 60, 2 (2004), pp. 91-110](https://people.eecs.berkeley.edu/~malik/cs294/lowe-ijcv04.pdf)