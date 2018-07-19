---
title: 假設狀況 （適用於 Excel 的資料表分析工具） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- what if scenario
- scenario analysis
ms.assetid: 4df5a5c5-1983-4009-a7c5-cd340649fd2f
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1edfd62ab4938970a2da22c71724d63953a507c8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249068"
---
# <a name="what-if-scenario-table-analysis-tools-for-excel"></a>假設狀況 (適用於 Excel 的資料表分析工具
  ![資料表分析工具中的假設狀況按鈕](media/tat-whatif.gif "那假設狀況資料表分析工具中的按鈕")  
  
 **What-if**狀況工具會分析現有的資料中的模式，然後可讓您評估變更一個資料行對不同的資料行值的效果。  
  
 例如，您可以探索某個項目漲價對總銷售額的影響。  
  
 此工具對於可建立的預測數目頗有彈性。 在完成初始分析之後，您可以預測資料表中所有資料的變更，或是一次輸入一個測試值。  
  
## <a name="using-the-what-if-scenario-tool"></a>使用假設狀況工具  
  
1.  開啟 Excel 資料表。  
  
2.  按一下 **案例**，然後選取**What-if**。  
  
3.  在 **案例**方塊中，選取 包含的值，您會變更，並為特定的值或變更 （無論是增加或減少） 的百分比指定變更的目前值的資料行。  
  
4.  在 **會發生什麼事**方塊中，指定您要評估其效果的資料行。  
  
5.  （選擇性） 按一下**選擇要用於分析的資料行**選取很可能會用於預測的資料行。 您也可以取消選取在偵測模式時可能不太有用的資料行，例如資料列識別碼或名稱。  
  
6.  在 **指定資料列或資料表**方塊中，選擇是否要針對目前選取的資料列，或一組完整的資料表中的資料來評估的影響。  
  
7.  如果您選取**在這個資料列上**，此工具會在對話方塊中顯示結果。 當對話方塊維持開啟狀態時，您可以修改您的選擇來測試其他狀況。  
  
8.  如果您選取**整份資料表**，此工具會在對話方塊中，顯示狀態訊息，並將兩個新的資料行加入至原始的資料表。 按一下 **關閉**工作表中檢視完整的結果。  
  
### <a name="requirements"></a>需求  
 此工具會使用 Microsoft 羅吉斯迴歸演算法，此演算法支援數值或離散值的預測。 但是，為了達成最好的結果，我們建議您採用以下最佳作法：  
  
-   選取包含有用資訊的資料行來進行分析。  
  
-   如果您包含太少的資料行，便可能會難以取得結果。  
  
-   如果您使用**值**選項時，您必須在方塊中輸入值，或從清單中選取值。  
  
-   如果您使用**百分比**選項，將變更設定為百分比增加或減少。 預設值為 120%，表示比目前的值增加 20%。  
  
> [!NOTE]  
>  如果您沒有設定值，便可能會收到錯誤。  
  
## <a name="understanding-the-results-of-what-if-analysis"></a>了解假設分析的結果  
 當您建立**What-if**案例中，此工具進行三項操作：  
  
-   建立資料採礦結構來儲存與資料表中的資料有關的關鍵事實。  
  
-   根據資料建立羅吉斯迴歸採礦模型。  
  
-   針對您所指定的每個值建立預測查詢。  
  
 您可以藉由指定輸出所有的預測一次**整份資料表**。 然後工具便會在原始的資料表中建立兩個新的資料行。  
  
 加入資料表中的資料行會包含兩種資訊類型：變更的預測值及其信心。 信心表示預測正確的機率。  
  
 您也可以在對話方塊中逐一輸入變更值，並以互動的方式檢視預測。 這是建立相同*單一預測查詢*。 預測查詢的結果是具有下列資訊的輸出：預測的成功或失敗、預測的值，以及信心層級。 信心層級會被顯示為包含虛線的列。 虛線越長，結果中的信心就越高。  
  
 例如，如果您嘗試判斷提高在客戶的意願，若要購買，並增加為 25，客戶的年齡將客戶的年齡**What-if**工具會查詢資料採礦模型，並傳回下列結果：  
  
 **Purchases Bicycle 的假設分析已找到方案。**  
  
 **'Purchases Bicycle' = 是**  
  
 **信心： 普通**  
  
 由於這項結果是根據資料表中的現有資料列，表示對於特定的客戶，如果其他關於客戶的一切都維持不變，客戶的年齡卻增加為 25，客戶便很可能會購買單車。  
  
 將預測輸出到原始資料表，可能會讓判斷預測是否有用更為容易。  
  
## <a name="related-tools"></a>相關工具  
 適用於 Excel 的資料採礦用戶端，是提供更為進階資料採礦功能的獨立增益集，其中包含的精靈可建立預測行為的資料採礦模型。 如需詳細資訊，請參閱 <<c0> [ 建立資料採礦模型](creating-a-data-mining-model.md)。  
  
 如需有關所使用的演算法**What-if**案例工具，請參閱 < Microsoft 羅吉斯迴歸演算法 > SQL Server 線上叢書 》 中的主題。  
  
## <a name="see-also"></a>另請參閱  
 [適用於 Excel 的資料表分析工具](table-analysis-tools-for-excel.md)  
  
  