

SIFT影像局部描述子介紹

檢測局部點ok
下一步，怎麼進一步描述他們更容易匹配
Descriptor:向量化關鍵點鄰域內容的，並具有不變性與獨特性

旋轉不變性描述子

建構一個旋轉不變性描述子
* 從DoG得到一個關鍵點與尺度
* 從關鍵點選擇出一個特徵角度
* 對所有關鍵點描述相對於特徵角度的方向

SIFT descriptor(SIFT=Scale-Invariant Feature Transform)
* 基於梯度的描述子來擷取關鍵點周圍的特徵
* 使用關鍵點對應的模糊影像區域
* 從關鍵點周圍取出影像梯度
* 為了具有旋轉不變性，旋轉梯度方向和位置
    * 取消旋轉，並直接在對應關鍵點存取得到的梯度方向
    * 也可以直接旋轉整張影像，但很慢

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