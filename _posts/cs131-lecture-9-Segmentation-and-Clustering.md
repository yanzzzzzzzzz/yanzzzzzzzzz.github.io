image segmentation

## 影像分割目的 
* 把屬於同一群的像素集合在一起
* 將想要做進一步分析的物件與背景分割出來，概念跟框選ROI相似，但是更精細的ROI，把非物件的不相干雜訊濾除

## 視覺上分群的範例
依照格式塔原則進行分類，以Gestalt為名的完形心理學，概念是人類對於任何視覺圖像的認知，是一種經過知覺系統組織後的形態與輪廓，而並非所有各自獨立部份的集合
其中格式塔原則的一些特點：
* Similarity 相似性
* Symmetry 對稱，影像左右半邊具有對稱性
* Common Fate 共同命運，同群在影像中表現出相同的移動方向性、趨勢
* Proximity 相近，物體距離相近時視為一群

![](/assets/img/post_img/Gestalt-Factors.png)

## clustering method
分群的概念是把一組資料依照距離或相似程度分成不同的群集
分群法是一種非監督式分群方法

### 相似度比對
常見的相似度比對方法有：
* Euclidean distance
* Cosine similarity

## 參考
[視覺法則 – 格式塔原則](https://uiclub.tw/2015/09/05/visual-principles-gestalt-principles/)