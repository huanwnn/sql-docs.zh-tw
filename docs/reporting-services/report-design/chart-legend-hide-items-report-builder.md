---
title: 隱藏圖表上的圖例項目 (報表產生器) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 92256240-0cd5-4be4-8904-d1e3b93cb6b3
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 784258433329832bbff3f8737086ef906eecfd64
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "77081334"
---
# <a name="chart-legend---hide-items-report-builder"></a>圖表圖例 - 隱藏項目 (報表產生器)
根據預設，加入到 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 分頁報表中非形狀圖的任何數列都會當做圖例中的項目加入。 至於圓形圖、環圈圖、漏斗圖與金字塔圖，加入到圖表中的任何數列則會在圖例中加入個別的資料點。  
  
 您可以隱藏圖例上的任何項目。 當您隱藏圖例項目時，該項目仍然會出現在圖表中。 當您不要顯示加入至圖表中之數列的詳細資訊時，此功能相當實用。 例如，如果您已經加入導出數列，例如圖表的移動平均，您可能想要在圖例中隱藏這個項目，只顯示原始數列的詳細資訊。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-hide-an-item-from-display-in-the-legend"></a>隱藏圖例中顯示的項目  
  
1.  以滑鼠右鍵按一下您要隱藏的數列，然後選取 [數列屬性]  。  
  
2.  按一下 **[圖例]** 。 選取 **[不要在圖例中顯示此數列]** 選項。  
  
    > [!NOTE]  
    >  您無法針對一個群組而不在其他群組中隱藏數列。 如果您已經將欄位加入到 **[數列群組]** 區域，將會隱藏屬於此群組的所有數列。  
  
## <a name="see-also"></a>另請參閱  
 [在圖表上格式化圖例 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/chart-legend-formatting-report-builder.md)   
 [格式化圖表上的資料點 &#40;報表產生器和 SSRS&#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [變更圖例項目的文字 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/chart-legend-change-item-text-report-builder.md)   
 [將移動平均新增至圖表 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/add-a-moving-average-to-a-chart-report-builder-and-ssrs.md)   
 [圖例屬性對話方塊、一般 &#40;報表產生器及 SSRS&#41;](https://msdn.microsoft.com/library/db718f8f-f185-422f-871c-96f0749e5893)  
  
  
