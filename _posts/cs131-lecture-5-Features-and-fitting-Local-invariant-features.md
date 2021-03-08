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