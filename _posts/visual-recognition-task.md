常見視覺辨識任務
* Objection Detection
* Objection localization
* VQA(Visual Question Answering)

## Challenges And KNN

參考[cs231n Image Classification](https://yanzzzzzzzzz.github.io/posts/cs231n-Image-Classification/)

## Simple object recognition pipeline

建造一個架構，用來辨識影像，輸入影像後會輸出對應類別結果

![](/assets/img/post_img/object-recognition-pipeline.png)

訓練階段重點：
* 輸入的訓練影像數量與標記類別
* 定義要擷取的影像特徵
* 訓練方法


![](/assets/img/post_img/Image-features.png)

這邊提到了幾個特徵提取方法
* 量化色彩資訊
* PCA
* 形狀特徵
* 