---
title: sys.databases （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- routes
- routes_TSQL
- sys.routes
- sys.routes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.routes catalog view
ms.assetid: 8fc65915-8bd6-425b-95d9-6a8468cb1e48
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 2769fcd0ec6dde419c9ebba2f3cfb0017cf74b0b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831384"
---
# <a name="sysroutes-transact-sql"></a>sys.routes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  這份目錄檢視會針對每個路由，各包含一個資料列。 Service Broker 使用路由來尋找服務的網路位址。   

|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|路由的名稱，它在資料庫中是唯一的。 不是 NULLABLE。|  
|**route_id**|**int**|路由的識別碼。 不是 NULLABLE。|  
|**principal_id**|**int**|擁有該路由的資料庫主體識別碼。 NULLABLE。|  
|**remote_service_name**|**nvarchar(256)**|遠端服務的名稱。 NULLABLE。|  
|**broker_instance**|**nvarchar(128)**|主控遠端服務的 Broker 識別碼。 NULLABLE。|  
|**期**|**datetime**|路由到期的日期和時間。 請注意，此值不使用當地的時區。 此值會顯示 UTC 格式的到期時間。 NULLABLE。|  
|**address**|**nvarchar(256)**|Service Broker 傳送遠端服務訊息至的網路位址。 NULLABLE。 針對 SQL Database 受控執行個體，位址必須是 local。|  
|**mirror_address**|**nvarchar(256)**|位址中所指定的伺服器之鏡像夥伴網路位址。 NULLABLE。|  
  
## <a name="permissions"></a>權限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
  
