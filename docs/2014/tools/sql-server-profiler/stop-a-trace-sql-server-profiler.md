---
title: 停止追蹤 (SQL Server Profiler) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], stopping
- stopping traces
ms.assetid: 47c4f33d-63e0-4444-bec8-4c1c91f8e25c
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9df984950c730b94527811f9f2ea3cca3ff220d9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37230028"
---
# <a name="stop-a-trace-sql-server-profiler"></a>停止追蹤 (SQL Server Profiler)
  此主題說明如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]來停止執行中的追蹤。  
  
 停止追蹤便會停止擷取資料。 追蹤一旦停止，重新啟動之後將會遺失先前所擷取的資料，除非已經將資料擷取到追蹤檔或追蹤資料表。 您也可以在停止追蹤之後，將收集的資料儲存至資料表或檔案。 追蹤停止時，先前所選取的所有追蹤屬性將會保留。 此時您可以變更名稱、事件、欄位及篩選條件。  
  
### <a name="to-stop-a-trace"></a>若要停止追蹤  
  
1.  選擇執行中的追蹤。  
  
2.  在 **[檔案]** 功能表上，按一下 **[停止追蹤]**。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  