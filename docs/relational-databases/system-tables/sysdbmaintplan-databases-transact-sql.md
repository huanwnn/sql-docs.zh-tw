---
title: sysdbmaintplan_databases （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdbmaintplan_databases
- sysdbmaintplan_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplan_databases system table
ms.assetid: f8413a44-8fcc-4899-84f2-b4afe0f8ec08
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b7e13af6a3cd091fb9b00eb6fcf0f668695062b3
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825822"
---
# <a name="sysdbmaintplan_databases-transact-sql"></a>sysdbmaintplan_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  此資料表包含在保留從舊版升級之實例的現有資訊 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本都不會變更此資料表的內容。 此資料表會儲存在**msdb**資料庫中。  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**plan_id**|**唯一**|維護計畫識別碼。|  
|**database_name**|**sysname**|資料庫維護計畫之相關資料庫的名稱。|  
  
  
