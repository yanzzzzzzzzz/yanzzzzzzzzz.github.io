從上回的影像調整大小部分定義
$$m \times n &rarr; m' \times n', 其中n'<n$$

如何保留重要的資訊又縮減尺寸，其中定義甚麼是重要，甚麼是不重要的影像資訊

## Basie Idea

不重要的資訊代表影像梯度變化小的地方，定義一個energy function

![](/assets/img/post_img/energy-function.png)

使用梯度來作為energy function的原因：
* 邊界代表紋理資訊
* 人眼對edge比較敏感，平滑處就可以被視為不重要資訊
* 概念很簡單

![](/assets/img/post_img/gradient-based-pixel-removal.png)

* 圖一對整張影像濾除低能量pixel
* 圖二對每行方向濾除最低能量pixel
* 圖三對每列方向濾除最低能量pixel，看起來結果較好一點，但仍看得出來階梯處有瑕疵的感覺

## Seam Carving
