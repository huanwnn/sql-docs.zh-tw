---
title: trace_xe_event_map （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- trace_xe_event_map_TSQL
- trace_xe_event_map
dev_langs:
- TSQL
helpviewer_keywords:
- trace_xe_event_map
- extended events [SQL Server], tables
ms.assetid: 537aa292-3540-47e8-be28-56dc01abc343
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8f3908fb257b761d5bee12aec07141b191e0328e
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82806226"
---
# <a name="extended-events-tables---trace_xe_event_map"></a>擴充事件資料表 - trace_xe_event_map
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  針對對應至 SQL 追蹤事件類別的每個「擴充事件」事件包含一個資料列。 此資料表儲存在主資料庫的 sys 架構中。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|trace_event_id|**smallint**|正在對應之 SQL 追蹤事件類別的識別碼。|  
|package_name|**nvarchar(60)**|對應事件所在之擴充事件封裝的名稱。|  
|xe_event_name|**nvarchar(60)**|對應至 SQL 追蹤事件類別之「擴充事件」事件的名稱。|  
  
## <a name="remarks"></a>備註  
 您可以使用下列查詢來識別相當於 SQL 追蹤事件類別的「擴充事件」事件：  
  
```  
SELECT te.name, xe.package_name, xe.xe_event_name  
FROM sys.trace_events AS te  
LEFT JOIN sys.trace_xe_event_map AS xe  
   ON te.trace_event_id = xe.trace_event_id  
WHERE xe.trace_event_id IS NOT NULL  
```  
  
 並非所有事件類別都有對等的「擴充事件」事件。 您可以使用下列查詢來列出沒有擴充事件對等用法的事件類別：  
  
```  
SELECT te.trace_event_id, te.name  
FROM sys.trace_events AS te  
LEFT JOIN sys.trace_xe_event_map AS xe  
   ON te.trace_event_id = xe.trace_event_id  
WHERE xe.trace_event_id IS NULL  
```  
  
 在先前查詢中，傳回的事件類別大部分都是稽核相關的。 我們建議您使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit 進行稽核。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit 會使用擴充事件來協助建立稽核。 如需詳細資訊，請參閱 [SQL Server Audit &#40;Database Engine&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)。  
  
## <a name="see-also"></a>另請參閱  
 [trace_xe_action_map &#40;Transact-SQL&#41;](../../relational-databases/system-tables/extended-events-tables-trace-xe-action-map.md)  
  
  
