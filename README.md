# ntut_107ab0732曾子芸

在ch8章節中，
用到了hashing trick和機器學習
機器學習用了python的sklearn中的RandomForestClassifier(隨機森林)和FeatureHasher套件
利用機器學習提取特徵的惡意軟件
程式中scores就是預測出來的結果
如程式碼中：
metrics.roc_curve
fpr, tpr, thresholds = metrics.roc_curve(test_y, scores)
以 test_y 為標準值 1為陽性 0為陰性
同時繪製ROC曲線以檢查檢測器的檢測閾值之間的關係及其正確和錯誤的陽性率

從附檔的圖Visualizing the detector’s ROC curve中
我們可以看到檢測器的假陽性率約為1％，可以檢測到約94％的惡意軟件樣本。

以下是詳細的程式碼解說部分：

1、由於 sh檔內 args.malware_paths 、args.benignware_paths 、args.evaluate都有輸入，所以會執行以下這段程式：
X, y = get_training_data(args.benignware_paths,args.malware_paths,hasher)
cv_evaluate(X,y,hasher)
2、get_training_data 這函式是將 malware_paths 和 benignware_paths 內的檔案取得 training data
X : 從 get_string_features() 得到檔名的特徵值 y : [ 1 x malware_paths 內檔案數量 ] [0 x benignware_paths 內檔案數量]

3、cv_evaluate
RandowForestClassifier 使用隨機森林決策樹model 進行訓練
(請參考以下的程式)
classifier = RandomForestClassifier(64)
classifier.fit(training_X,training_y)
scores = classifier.predict_proba(test_X)[:,-1]

其中有提過scores就是預測出來的結果

接著metrics.roc_curve
fpr, tpr, thresholds = metrics.roc_curve(test_y, scores)
我們以上面所言 test_y 為標準值 1為陽性 0為陰性

test_y 的index 對應 scores 的index

接下來選取一個閾值計算TPR/FPR,閾值的選取規則是在scores值中從大到小的以此選取。 scores中大於等於閥值的就設為1 小於閥值就是0 公式如下：

FPR = FP / (FP+TN)
TPR = TP/ (TP + FN)
FPR : test_y 陰性對應 score中 大於等於閥值中的比例

TPR : test_y 陽性對應 score中 大於等於閥值中的比例

閥值會從大到小重複以上公式

最終就會產生圖裡的曲線


心得：
這些技術與觀念對我而言就像完全全新的領域
可能自己本身對這些知識就是不夠的
這次的練習至少讓自己多操作了些
對程式碼也有近一步的了解
雖然還是不太用會github
希望老師見諒
