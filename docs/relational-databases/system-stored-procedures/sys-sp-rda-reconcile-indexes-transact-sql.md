---
title: sys.databases sp_rda_reconcile_indexes （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sp_rda_reconcile_indexes
- sp_rda_reconcile_indexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_indexes stored procedure
ms.assetid: 96b31ab9-bf84-46d6-9990-81f5c51f885a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 504085ff53415a7cf84bdb4aabf5eff567391a0c
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827395"
---
# <a name="syssp_rda_reconcile_indexes-transact-sql"></a>sys.databases sp_rda_reconcile_indexes （Transact-sql）
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  將架構工作排入佇列，以協調遠端資料表上的索引。 在此工作順利完成之後，遠端資料表的索引會存在於本機已啟用 Stretch 的資料表上。  
  
 當您呼叫**sp_rda_reconcile_indexes**時，如果有另一個排入佇列的工作要協調索引，這個預存程式不會將重複的工作排入佇列。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_rda_reconcile_indexes [@objname = ] 'objname'  
  
```  
  
## <a name="arguments"></a>引數  
 [ @objname =] *' objname '*  
 這是您要對其進行索引進行調整的已啟用 Stretch 之資料表的限定或非限定名稱。 只有當您指定限定的物件時，才需要引號。  
  
## <a name="return-code-values"></a>傳回碼值  
 0（成功）或 >0 （失敗）  
  
## <a name="see-also"></a>另請參閱  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
