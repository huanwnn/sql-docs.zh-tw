---
title: 全文檢索索引屬性（排程頁面） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.schedule.f1
ms.assetid: a828e284-097e-4854-8c49-931934eb73bf
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9dda41e229e36c0c4b86c5bdb00782c3b5871bfa
ms.sourcegitcommit: 18a7c77be31f9af92ad9d0d3ac5eecebe8eec959
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83858643"
---
# <a name="full-text-index-properties-schedules-page"></a>全文檢索索引屬性 (排程頁面)
  您可以使用這個頁面來檢視和建立執行 SQL Server Agent 作業的排程，以便針對全文檢索索引的基底資料表啟動更新的累加母體擴展。 如果基底資料表或檢視表沒有包含 `timestamp` 資料類型的資料行，就會執行完整母體擴展。  
  
 **若要檢視或變更全文檢索索引的屬性**  
  
-   [管理全文檢索索引](../relational-databases/indexes/indexes.md)  
  
## <a name="ui-element-list"></a>UI 元素清單  
 **排程**  
 針對全文檢索索引的基底資料表列出每個排程的累加母體擴展 (如果有的話)。  
  
 **名稱**  
 顯示每個排程母體擴展的名稱。  
  
 **母體類型**  
 顯示每個排程母體擴展的類型。  
  
 **已啟用**  
 指出排程的母體擴展目前為啟用或停用。  
  
 **描述**  
 顯示建立排程時所指定的描述。  
  
 **新增**  
 按一下即可建立擴展全文檢索索引的新排程。  
  
## <a name="see-also"></a>另請參閱  
 [使用全文檢索索引 Wizard](../relational-databases/search/use-the-full-text-indexing-wizard.md)   
 [擴展全文檢索索引](../relational-databases/search/populate-full-text-indexes.md)  
  
  
