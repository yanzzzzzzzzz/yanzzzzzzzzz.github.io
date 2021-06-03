

Visual bag of words 詞袋模型

概念：將影像取出具有特徵的地方，存在待比對區域中，新影像進來時，逐一比對影像符合詞袋中哪個的特徵比較多，就跟詞袋中的影像越相似

有特徵的地方：代表可以表現這張影像與其他影像不同之處


![](/assets/img/post_img/Visual-bag-of-words.png)


## 實作流程 & 方法
1. 取出特徵
1. 學習出"視覺詞彙"
1. 量化特徵
1. 通過“視覺詞”的頻率表示圖像

### 特徵提取

特徵取得方式參考文本分析方法，文本分析中由單詞出現的頻率來去做分析，圖片則是由紋理特徵出現的頻率高低作分析

而課程中提到的方法的關鍵字：
1. Regular grid 把影像切分成正方型的網格狀
1. Interest point detector 感興趣點檢測 
1. Ramdom sampling 隨機採樣
1. Segmentation-based patches 