### 台灣牧場乳量預測

> 本專案為 AIdea 競賽「台灣牧場乳量預測」的解決方案，使用 XGBoost 模型進行預測。

* AIdea 競賽連結：https://aidea-web.tw/topic/fcc338da-e7ec-4d9e-a860-5dcdd85ba52b?focus=intro11

#### 簡介

* 根據統計 2019 年全球酪農業的預估營收超過 4,420 億美元 [1]，至 2019 年第二季農委會資料開放平台資料 [2] 顯示，全台乳牛飼養場數為 557 場，乳牛在養頭數為 115,685 頭，其中每牧場的平均飼養規模約 207 頭牛。依農委會 107 年農業統計年報 [3]- 畜牧生產之統計結果，產乳牛有 61,967 頭，產乳量約 419,342 公噸。隨著數位轉型，農牧業也開始擁抱新科技 [4]，在精簡人力的狀態下，每頭牛的平均產乳量已經超越澳洲、德國及中國等國，且仍在逐年提升，整體的酪農業實力正不斷追趕酪農業先進國 (如：美國與以色列… 等)。

* 本議題透過中華民國乳業協會所提供的**乳牛群性能改良計畫（Dairy Herd Improvement, DHI）資料庫**預測台灣不同地區牧場生產的乳量，希望參賽者能掌握預測乳量生產的關鍵，並對於台灣酪農後續在智慧化牧場管理與乳價擬定能有相當程度的助益。

#### 評估標準

* 參與本議題研究者在提供預測結果後，系統後台將根據評估方式計算分數，評估方式採用計算與實際值的均根差 (Root-Mean-Square Error, RMSE)

    RMSE = $\sqrt{\frac{1}{n}\sum_{i=1}^{n}(y_i - \hat{y}_i)^2}$

#### 預測目標

* 本議題預測目標為每牧場每月的乳量，預測結果為每牧場每月的乳量，單位為公斤 (kg)。
* 背景知識：母牛需要受孕才能生產乳量，因此每頭母牛每年的乳量會有一定的季節性，例如：春季為乳量最高的季節，夏季為乳量最低的季節。


#### 處理流程

* SOP
    1. df.info() 查看資料型態和確認資料是否有缺失值
    1.1 df.isnull().sum() 查看缺失值
    2. df.describe() 查看資料的統計量
    3. df.corr() 查看資料的相關性，心裡有個底哪一些和目標值有關
    # OPTION
    4. df.hist() 查看資料的分布
    6. df.boxplot() 查看資料的分布
    14. df.crosstab() 群組


1. Preprocessing
    1. drop columns (確認無用的欄位)
    2. fillna (填補缺失值)
    3. one-hot encoding (將類別型欄位轉為數值型欄位)
    4. convert to datetime (將日期欄位轉為 datetime 格式)



#### 參考資料
1. [農業知識家：「請問乳牛不懷孕可以產牛奶嗎？」](https://kmweb.coa.gov.tw/knowledge_view.php?id=7673)
2. 