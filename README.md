# ntut_107ab0732曾子芸

在ch8章節中
用到了hashing trick和機器學習
機器學習用了python的sklearn中的RandomForestClassifier(隨機森林)和FeatureHasher套件
利用機器學習提取特徵的惡意軟件
程式中scores就是預測出來的結果
如程式碼中
metrics.roc_curve
fpr, tpr, thresholds = metrics.roc_curve(test_y, scores)
以 test_y 為標準值 1為陽性 0為陰性

同時繪製ROC曲線以檢查檢測器的檢測閾值之間的關係及其正確和錯誤的陽性率

從附檔的圖Visualizing the detector’s ROC curve中
我們可以看到檢測器的假陽性率約為1％，可以檢測到約94％的惡意軟件樣本。


心得：
這些技術與觀念對我而言就像完全全新的領域
可能自己本身對這些知識就是不夠的
這次的練習至少讓自己多操作了些
對程式碼也有近一步的了解
雖然還是不太用會github
希望老師見諒
