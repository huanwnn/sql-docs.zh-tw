---
title: sp_databases （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_databases_TSQL
- sp_databases
dev_langs:
- TSQL
helpviewer_keywords:
- sp_databases
ms.assetid: 2a83b92a-9ecc-43c4-8ff4-e91e3a940b5a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1c4cd06a540709b5e100a086a426fd5bdb46abf5
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82826228"
---
# <a name="sp_databases-transact-sql"></a>sp_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  列出在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中的資料庫，或可利用資料庫閘道來存取的資料庫。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_databases  
```  
  
## <a name="return-code-values"></a>傳回碼值  
 無  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**DATABASE_NAME**|**sysname**|資料庫的名稱。 在中 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ，這個資料行代表儲存在**sys.databases**目錄檢視中的資料庫名稱。|  
|**DATABASE_SIZE**|**int**|資料庫的大小 (以 KB 為單位)。|  
|**備註**|**Varchar （254）**|對於 [!INCLUDE[ssDE](../../includes/ssde-md.md)]，這個欄位一律會傳回 NULL。|  
  
## <a name="remarks"></a>備註  
 傳回的資料庫名稱可用來作為 USE 陳述式中的參數，以變更目前資料庫的內容。  
  
 **sp_databases**在開放式資料庫連接（ODBC）中沒有對等的。  
  
## <a name="permissions"></a>權限  
 需要 CREATE DATABASE、ALTER ANY DATABASE 或 VIEW ANY DEFINITION 權限，且必須擁有資料庫的存取權限。 無法拒絕 VIEW ANY DEFINITION 權限。  
  
## <a name="examples"></a>範例  
 下列範例會顯示如何執行 `sp_databases`。  
  
```sql  
USE master;  
GO  
EXEC sp_databases;  
```  
  
## <a name="see-also"></a>另請參閱  
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [HAS_DBACCESS &#40;Transact-sql&#41;](../../t-sql/functions/has-dbaccess-transact-sql.md)  
  
  
