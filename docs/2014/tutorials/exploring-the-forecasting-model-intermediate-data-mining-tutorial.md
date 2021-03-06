---
title: 探索預測模型（元資料採礦教學課程） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0a00f409-050f-4b92-9763-ba31a6aa3052
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 607f300fbf2138796bb02c66c62386fcc93e6a45
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2020
ms.locfileid: "62992255"
---
# <a name="exploring-the-forecasting-model-intermediate-data-mining-tutorial"></a>探索預測模型 (中繼資料採礦教學課程)
  現在您已建立預測採礦模型，您可以使用資料採礦設計師的 [**採礦模型檢視器**] 索引標籤來探索結果。 時間序列檢視器包含兩個索引標籤： [**圖表**] 和 [模型]。 **Model** [!INCLUDE[msCoName](../includes/msconame-md.md)]  
  
 此外，您可以對所有模型使用 Microsoft 一般內容樹狀檢視器。 每個檢視針對時間序列模型中的資訊呈現略為不同的面貌。  
  
-   [圖表索引標籤](#bkmk_Charts)  
  
-   [模型索引標籤](#bkmk_Model)  
  
-   [Microsoft 一般內容樹狀檢視器](#bkmk_Content)  
  
##  <a name="charts-tab"></a><a name="bkmk_Charts"></a>圖表索引標籤  
 時間序列檢視器的 [圖表] 索引標籤會以圖形方式顯示每個數列，包括歷程記錄資料和預測。 **Charts** [!INCLUDE[msCoName](../includes/msconame-md.md)] 時間序列圖形中的每個線條代表由產品、區域和可預測屬性構成的唯一組合。  
  
 檢視器右側的圖例會根據下拉式清單中的選取項目列出時間序列。 您可以選取和清除圖例中的核取方塊，來控制圖形中所顯示的時間序列。  
  
 您也可以變更顯示選項，例如各時間序列所用的色彩，或值是否顯示在圖表中的資料點。  
  
#### <a name="to-select-a-time-series"></a>若要選取時間序列  
  
1.  如果看不到，請按一下 [**採礦模型檢視器**] 索引標籤的 [**圖表**] 索引標籤。  
  
2.  按一下圖表檢視右側的下拉式清單，選取所有核取方塊。 [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     圖表現在應包含 24 個不同的序列線條。  
  
3.  在圖表右側的核取方塊中，清除所有有關 [金額] 的方塊，以便暫時隱藏以金額為基礎的所有序列線條。  
  
     接著，清除與 R750 和 R250 自行車有關的核取方塊。  
  
     此圖表現在只包含下列六個序列線條，方便您比較 M200 和 T1000 自行車的趨勢。  
  
    -   **M200 Europe: Quantity**  
  
    -   **M200 North America: Quantity**  
  
    -   **M200 Pacific: Quantity**  
  
    -   **T1000 Europe: Quantity**  
  
    -   **T1000 North America: Quantity**  
  
    -   **T1000 Pacific: Quantity**  
  
 ![序列預測 M200 與 T1000 數量](../../2014/tutorials/media/6series-defaultforecasting.gif "序列預測 M200 與 T1000 數量")  
  
 此檢視器中顯示的圖表會包含歷程記錄資料和預測的資料。 預測的資料會加上陰影，以便和歷程記錄資料有所區別。 若要更輕鬆地比較不同序列，您也可以變更圖表中各線條的色彩。 如需詳細資訊，請參閱 [變更資料採礦檢視器中使用的色彩](../../2014/analysis-services/data-mining/change-the-colors-used-in-the-data-mining-viewer.md)。  
  
 從趨勢線，可以看到所有區域的總銷售量整體都在增加，且每 12 個月會有一個出現在 12 月的高峰。 此外，您還可以從圖表中看出 T1000 自行車資料的開始時間，比其他產品序列資料晚的多。 因為它是新產品，但此序列是以較少的資料為基礎，因此預測可能不準確。  
  
 根據預設，每個時間序列 (以點線表示) 顯示五個預測步驟。 您可以變更這個值，檢視更多或更少的預測。 您也可以在圖表中加入誤差線，以圖形方式檢視預測的標準差。  
  
#### <a name="to-change-prediction-and-display-options-in-the-chart-view"></a>變更圖表檢視中的預測和顯示選項  
  
1.  請嘗試逐漸變更**預測步驟**的值，將它從**5**增加為**10**，然後再轉換回**6**。  
  
     當歷程記錄資料中有大幅波動時，其波動通常會隨著預測數目增加而重複或甚至幅度加大。 這時您可能需要探究歷程記錄資料中暴增的原因，然後決定是要接受這些結果、尋求來源資料中的某種更正，還是在模型中套用某種平滑效果。  
  
2.  選取 [**顯示偏差**] 核取方塊。  
  
     此選項會顯示每個預測值的預估錯誤。  
  
3.  請注意 X 軸的小數位數。 歷程記錄和預測資料的變更永遠是以百分比表示，但實際值會自動調整，以便將所有值放在圖形上。 因此，在比較模型時需要特別小心，不要只依賴視覺項目。 若要取得確切的值，或預測的增加百分比和值，請將滑鼠停留在虛線或實線，或按一下線條以查看 [**挖掘圖例**] 中的值。  
  
     **提示**：如果看不到 [**挖掘圖例**]，請切換至 [**模型**視圖]，以滑鼠右鍵按一下任何節點，然後選取 [**顯示圖例**]。  
  
 檢視這些趨勢後，您關切某些序列缺少資料，想知道是否可根據模型或地區計算平均銷售量，取得更可靠的預測。 稍後在本教學課程中將探索此方法。  
  
 [回到頁首](#bkmk_Charts)  
  
##  <a name="model-tab"></a><a name="bkmk_Model"></a>模型索引標籤  
 [ **Model**資料採礦設計師] [!INCLUDE[msCoName](../includes/msconame-md.md)]中的時間序列檢視器的 [模型] 索引標籤可讓您以樹狀結構圖表的形式來查看預測模型。  
  
 首先，請注意，因為資料針對三個不同區域 (Europe、North America 和 Pacific) 中多個產品線 (T1000 等等) 的銷售描述兩個不同的量值 (Amount 和 Quantity)，所以建立的模型實際上包含 24 個不同的樹狀目錄，每個樹狀目錄代表不同區域、產品和可預測屬性之組合的銷售模式模型。  
  
 您可以從 [**模型**] 索引標籤上的 [**樹狀**] 下拉式清單中選取數列，以選擇您想要查看的產品線、地區和銷售度量的組合。  
  
 從樹狀檢視的模型中可學到什麼？ 例如，讓我們比較兩個模型，一個在樹狀結構中有數個層級，另一個則具有單一節點。  
  
-   當樹狀圖形包含單一節點時，這表示模型中的趨勢在一段時間後通常是同質性的。 您可以使用這個單一節點標記為 [**全部**]，以查看描述輸入變數與結果之間關聯性的公式。  
  
-   當時間序列的樹狀圖形有多個分支時，這表示偵測到的時間序列太複雜，無法以單一方程式表示。 相反地，樹狀圖表可能包含多個分支，每個分支都標示了導致樹狀結構*分割*的條件。 當樹狀目錄分割時，每個分支表示不同的時間區段，其中的趨勢可用單一方程式描述。  
  
     例如，如果您查看圖表圖形，並在9月底開始看到銷售量突然跳躍，並繼續進行年末的假日，您可以切換至**模型**視圖，以查看趨勢變更的確切日期。 樹狀結構中代表「9月前」和「9月之後」的分支會包含不同的公式：一個公式會以數學方式描述分割的銷售趨勢，另一個公式則描述「年9月」假期的銷售趨勢。  
  
#### <a name="to-explore-the-decision-tree-for-a-time-series-model"></a>瀏覽時間序列模型的決策樹  
  
1.  在檢視器的 [**模型**] 索引標籤上的 [**樹狀**] 清單中，選取 [ **T1000 歐洲：金額**] 數列。  
  
     按一下標示為 [**全部**] 的節點。  
  
     針對 [ **All** ] 節點，所顯示的工具提示會包含整個數列中的案例數目，以及衍生自資料分析的時間序列方程式等資訊。  
  
2.  如果看不到 [**挖掘圖例**]，請以滑鼠右鍵按一下節點，然後選取 [**顯示圖例**]。  
  
     [**挖掘圖例**] 提供工具提示中的相同資訊。 如果有任何離散的獨立變數，您也會看到顯示變數分佈在節點中的長條圖。  
  
3.  現在選取另一個要檢視的時間序列。 在檢視器的 [**模型**] 索引標籤上，使用**樹狀**清單，選取 [ **M200 北美洲：數量**] 數列。  
  
     樹狀結構圖形現在包含 [ **All** ] 節點和兩個子節點。 您可以透過查看子節點上的標籤，了解趨勢線在哪個時間點變更。  
  
     針對每個子節點，[**挖掘圖例**] 中的描述也會包含樹狀結構之每個分支中的案例計數。  
  
 下列清單說明樹狀檢視器的一些其他功能：  
  
-   您可以使用 [**背景**] 控制項來變更圖表中所表示的變數。 根據預設，較暗的節點會包含更多案例，因為**背景**的值會設定為 [擴展 **]。** 若只要查看節點中有多少案例，請將滑鼠停留在節點上，並查看顯示的工具提示，或按一下節點，並在 [**節點圖例**] 視窗中查看數位。  
  
-   也可以在工具提示中或透過按一下節點來檢視節點的迴歸公式。 如果您建立了混合模型，則會看到兩個公式，一個用於 ARTXP (在分葉節點中)，另一個用於 ARIMA (在樹狀目錄的根節點中)。  
  
-   小菱形用於表示連續數字的節點。 菱形所在的橫線上會顯示屬性的範圍。 菱形會在節點的平均值置中，而菱形的寬度代表在該節點的屬性變異數。  
  
 [回到頁首](#bkmk_Charts)  
  
##  <a name="optional-generic-content-tree-viewer"></a><a name="bkmk_Content"></a>選擇性一般內容樹狀檢視器  
 除了時間序列的自訂檢視器之外， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]還提供**MicrosoftGeneric 內容樹狀檢視器**，以用於所有資料採礦模型。 此檢視器具備一些優點：  
  
-   **Microsoft 時間序列檢視器**：此視圖會合並這兩種演算法的結果。 雖然您可以分別檢視每個序列，但無法判斷各演算法結果如何結合。 此外，在此檢視中，工具提示和採礦圖例只顯示最重要的統計資料。  
  
-   **一般內容樹狀檢視器**：可讓您一次流覽和查看模型中使用的所有資料數列，如果您已建立混合模型，ARIMA 和 ARTXP 樹狀目錄都會顯示在相同的圖形中。  
  
     您可以使用此檢視器取得兩個演算法的所有統計資料，以及值分佈。  
  
     建議想要深入了解 ARIMA 和 ARTXP 分析的資料採礦專家使用者採用。  
  
#### <a name="to-view-details-for-a-particular-data-series-in-the-generic-content-viewer"></a>在一般內容樹狀檢視器中檢視特定資料序列的詳細資料  
  
1.  在 [**採礦模型檢視器**] 索引標籤中，從 [**檢視器**] 下拉式清單中選取 [ **Microsoft 一般內容樹狀檢視器**]。  
  
2.  在 [**節點標題**] 窗格中，按一下最上方的 [（全部）] 節點。  
  
3.  在 [**節點詳細資料**] 窗格中，查看 ATTRIBUTE_NAME 的值。  
  
     這個值顯示這個節點包含哪一個序列或產品與區域組合。 在 AdventureWorks 範例中，最頂端的節點屬於 M200 Europe 序列。  
  
4.  在 [**節點標題**] 窗格中，找出具有子節點的第一個節點。  
  
     如果數列節點具有子系，則 Microsoft 時間序列檢視器的 [**模型**] 索引標籤上所顯示的樹狀檢視也會有分支結構。  
  
5.  展開該節點，並按一下其中一個子節點。  
  
     結構描述的 NODE_DESCRIPTION 資料行包含造成樹狀結構分岔的條件。  
  
6.  在 [**節點標題**] 窗格中，按一下最上層的 ARIMA 節點，然後展開節點，直到所有子節點都可見為止。  
  
7.  在 [**節點詳細資料**] 窗格中，查看 ATTRIBUTE_NAME 的值。  
  
     這個值會告訴您這個節點包含哪一個時間序列。 ARIMA 區段中最頂端的節點應該符合 (All) 區段中最頂端的節點。 在 AdventureWorks 範例中，這個節點包含 M200 Europe 序列的 ARIMA 分析。  
  
 如需詳細資訊，請參閱[時間序列模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)。  
  
 [回到頁首](#bkmk_Charts)  
  
## <a name="next-task-in-lesson"></a>本課程的下一項工作  
 [&#40;中繼資料採礦教學課程建立時間序列預測&#41;](../../2014/tutorials/creating-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>另請參閱  
 [時間序列模型查詢範例](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)   
 [Microsoft 時間序列演算法技術參考](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
