Local invariant features 局部不變特徵

## 使用local invariant features動機
* 全局特徵有它的限制性
* 增強對遮擋、角度變化的魯棒性

## 常見的方法
1. 找到多個獨特的關鍵點
1. 定義一個rectangle大小把key points的的周圍資訊取出來
1. 提取周圍資訊並做正規化
1. 計算正規化區域的局部描述子，例如使用區域色彩資訊
1. 匹配局部描述子

## 好的 Local Features
* 區塊特徵萃取要有重複性與準確性
* 特徵是局部的獨特，對變形與雜亂背景有魯棒性
* 要能萃取夠多的特徵進行比對
* 計算方法越快越好

## 特徵檢測器相關論文
* Hessian & Harris [Beaudet ‘78], [Harris ‘88]
* Laplacian, DoG [Lindeberg ‘98], [Lowe ‘99]
* Harris-/Hessian-Laplace [Mikolajczyk & Schmid ‘01]
* Harris-/Hessian-Affine [Mikolajczyk & Schmid ‘04]
* EBR and IBR [Tuytelaars & Van Gool ‘04]
* MSER [Matas ‘02]
* Salient Regions [Kadir & Brady ‘01] 

## Harris corner
設計準則：可以很簡單的用一個小視窗當作視野範圍辨認出角點
如果在角點，往任意方向移動這個小視窗應該會有很大的亮度變化

![](/assets/img/post_img/harris-corner.png)

### Formulation

移動小視窗的中心座標點$$[x,y]到[x+u,y+v]$$來計算移動後的亮度變化

![](/assets/img/post_img/harris-corner-explain.png)

量測單點亮度變化公式：
$$ I(x+u,y+v) - I(x,y) $$

計算整個小視窗內的亮度變化公式：
$$\sum_{xy}w(x,y)[I(x+u,y+v)-I(x,y)]^2 $$

其中window function可以使用加權函數、高斯函數

$$I(x+u,y+v)$$利用泰勒展開式

![](/assets/img/post_img/Taylor-expansion.png)

其中一階近似為

![](/assets/img/post_img/Taylor-expansion-first.png)

將一階近似帶入harris corner公式

![](/assets/img/post_img/harris-corner-formula.png)

最終

![](/assets/img/post_img/harris-corner-formula-1.png)

其中M是一個2x2的矩陣用來計算影像導數

![](/assets/img/post_img/harris-corner-formula-2.png)

M是對稱矩陣，求其特徵值

![](/assets/img/post_img/harris-corner-formula-3.png)



## 參考

[Harris Corner Detector 公式推導以及具體含義](https://blog.csdn.net/u011534057/article/details/77775974)