---
title: sys.databases dm_exec_compute_nodes （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_COMPUTE_NODES_TSQL
- DM_EXEC_COMPUTE_NODES
- SYS.DM_EXEC_COMPUTE_NODES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_compute_nodes management view
- PolyBase, views
- PolyBase management views
- dm_exec_compute_nodes management view
ms.assetid: 0de4b7a4-401f-4e2d-9ab0-c54587e05154
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e8b7148904df1a9c59bb6b12fd521945b70e2f4d
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830653"
---
# <a name="sysdm_exec_compute_nodes-transact-sql"></a>sys.databases dm_exec_compute_nodes （Transact-sql）
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  保存與 PolyBase 資料管理搭配使用之節點的相關資訊。 它會針對每個節點列出一個資料列。  
  
 使用此 DMV 查看相應放大叢集中的所有節點清單及其角色、名稱和 IP 位址。  
  
|資料行名稱|資料類型|說明|範圍|  
|-----------------|---------------|-----------------|-----------|  
|compute_node_id|**int**|與節點相關聯的唯一數值識別碼。 此視圖的索引鍵。|跨向外延展叢集（不論類型為何）都是唯一的。|  
|類型|**nvarchar(32)**|節點的類型。|「計算」、「HEAD」|  
|name|**nvarchar(32)**|節點的邏輯名稱。|適當長度的任何字串。|  
|address|**nvarchar(32)**|此節點的 IP 位址。|IP 位址範圍|  
  
## <a name="see-also"></a>另請參閱  
 [使用動態管理檢視進行 PolyBase 疑難排解](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [動態管理 Views 和函數 &#40;Transact-sql&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [資料庫相關的動態管理檢視 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
