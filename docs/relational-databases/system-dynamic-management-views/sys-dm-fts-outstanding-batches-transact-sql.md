---
title: sys.databases dm_fts_outstanding_batches （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_fts_outstanding_batches
- dm_fts_outstanding_batches_TSQL
- sys.dm_fts_outstanding_batches_TSQL
- sys.dm_fts_outstanding_batches
dev_langs:
- TSQL
helpviewer_keywords:
- troubleshooting [SQL Server], full-text search
- sys.dm_fts_outstanding_batches dynamic management view
ms.assetid: c4d697ed-c906-4c28-b137-036a25e13c84
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2f0e03483ab0e2470df24fa2a00e6b7965b2199f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "68265894"
---
# <a name="sysdm_fts_outstanding_batches-transact-sql"></a>sys.dm_fts_outstanding_batches (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  傳回有關每個全文檢索索引批次的資訊。  
  
  |資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|database_id|**int**|資料庫的識別碼|  
|catalog_id|**int**|全文檢索目錄的識別碼|  
|table_id|**int**|包含全文檢索索引之資料表識別碼的識別碼。|  
|batch_id|**int**|批次識別碼|  
|memory_address|**varbinary(8)**|批次物件記憶體位址|  
|crawl_memory_address|**varbinary(8)**|搜耙物件記憶體位址 (父物件)|  
|memregion_memory_address|**varbinary(8)**|篩選背景程式主機 (fdhost.exe) 之輸出共用記憶體的記憶體區域記憶體位址|  
|hr_batch|**int**|此批次最近一次的錯誤碼|  
|is_retry_batch|**bit**|指示這是否為重試批次：<br /><br /> 0 = 否<br /><br /> 1 = 是|  
|retry_hints|**int**|批次所需的重試類型：<br /><br /> 0 = 無重試<br /><br /> 1 = 多執行緒重試<br /><br /> 2 = 單一執行緒重試<br /><br /> 3 = 單一和多執行緒重試<br /><br /> 5 = 多執行緒最後重試<br /><br /> 6 = 單一執行緒最後重試<br /><br /> 7 = 單一和多執行緒最後重試|  
|retry_hints_description|**nvarchar(120)**|所需之重試類型的描述：<br /><br /> NO RETRY<br /><br /> MULTI THREAD RETRY<br /><br /> SINGLE THREAD RETRY<br /><br /> SINGLE AND MULTI THREAD RETRY<br /><br /> MULTI THREAD FINAL RETRY<br /><br /> SINGLE THREAD FINAL RETRY<br /><br /> SINGLE AND MULTI THREAD FINAL RETRY|  
|doc_failed|**bigint**|批次中失敗的文件數目|  
|batch_timestamp|**timestamp**|建立批次時取得的時間戳記值。|  
  
## <a name="permissions"></a>權限  

在[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]上， `VIEW SERVER STATE`需要許可權。   
在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]高階層級上， `VIEW DATABASE STATE`需要資料庫的許可權。 在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] [標準] 和 [基本] 層上，需要**伺服器管理員**或**Azure Active Directory 系統管理員**帳戶。   
  
## <a name="examples"></a>範例  
 下列範例會了解目前針對伺服器執行個體內每一個資料表所處理的批次數。  
  
```  
SELECT database_id, table_id, COUNT(*) AS batch_count FROM sys.dm_fts_outstanding_batches GROUP BY database_id, table_id ;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [全文檢索搜尋和語義搜尋動態管理檢視和函數 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [全文檢索搜尋](../../relational-databases/search/full-text-search.md)  
  
  
