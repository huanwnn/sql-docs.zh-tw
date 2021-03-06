---
title: 建立資源集區 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- resource pools [SQL Server], create
- Resource Governor, resource pool create
ms.assetid: 44dd0567-a4c8-4c72-89ff-e76f6ddef344
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f4d18ef352c3e5ab6342e573d16bc3deaed5db72
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2020
ms.locfileid: "68211999"
---
# <a name="create-a-resource-pool"></a>建立資源集區
  您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]來建立資源集區。  
  
-   **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)  
  
-   **To create a resource pool, using:**  [SQL Server Management Studio](#CreRPProp), [Transact-SQL](#CreRPTSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> 限制事項  
 最大 CPU 百分比必須大於或等於最小 CPU 百分比。 最大記憶體百分比必須大於或等於最小記憶體百分比。  
  
 所有資源集區之最小 CPU 百分比和最小記憶體百分比的總和不得超過 100。  
  
###  <a name="permissions"></a><a name="Permissions"></a> 權限  
 建立資源集區需要 CONTROL SERVER 權限。  
  
##  <a name="create-a-resource-pool-using-sql-server-management-studio"></a><a name="CreRPProp"></a> 使用 SQL Server Management Studio 建立資源集區  
 **若要使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，開啟 [物件總管]，然後遞迴地向下展開 **[管理]** 節點至 **[資源管理員]**。  
  
2.  以滑鼠右鍵按一下 [資源管理員]****，然後按一下 [屬性]****。  
  
3.  在 **[資源集區]** 方格中，按一下空白資料列的第一個資料行。 這個資料行標示有星號 (*)。  
  
4.  按兩下 [名稱]**** 資料行中的空白儲存格。 輸入您想要用於資源集區的名稱。  
  
5.  在資料列中按一下或按兩下要變更的任何其他資料格，然後輸入新值。  
  
6.  若要儲存變更，請按一下 **[確定]**。  
  
##  <a name="create-a-resource-pool-using-transact-sql"></a><a name="CreRPTSQL"></a>使用 Transact-sql 建立資源集區  
 **若要使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]**  
  
1.  執行 `CREATE RESOURCE POOL` 陳述式，並指定要設定的屬性值。  
  
2.  執行**ALTER RESOURCE GOVERNOR 重新**設定語句。  
  
### <a name="example-transact-sql"></a>範例 &#40;Transact-SQL&#41;  
 下列範例會建立名稱為 `poolAdhoc`的資源集區。  
  
```  
CREATE RESOURCE POOL poolAdhoc  
WITH (MAX_CPU_PERCENT = 20);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [Resource Governor](resource-governor.md)   
 [啟用 Resource Governor](enable-resource-governor.md)   
 [Resource Governor 資源集區](resource-governor-resource-pool.md)   
 [變更資源集區設定](change-resource-pool-settings.md)   
 [刪除資源集區](delete-a-resource-pool.md)   
 [使用範本設定 Resource Governor](configure-resource-governor-using-a-template.md)   
 [Resource Governor 工作負載群組](resource-governor-workload-group.md)   
 [Resource Governor 分類函數](resource-governor-classifier-function.md)   
 [建立資源集區 &#40;Transact-sql&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
