---
title: sp_defaultdb （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_defaultdb_TSQL
- sp_defaultdb
dev_langs:
- TSQL
helpviewer_keywords:
- sp_defaultdb
ms.assetid: 663b859f-c6da-4942-95a6-60b93d05654e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 09c28c955dd89a889600982882c6bdafdc2b10cb
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833395"
---
# <a name="sp_defaultdb-transact-sql"></a>sp_defaultdb (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  變更登入的預設資料庫 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]請改用[ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md) 。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_defaultdb [ @loginame = ] 'login', [ @defdb = ] 'database'   
```  
  
## <a name="arguments"></a>引數  
`[ @loginame = ] 'login'`這是登入名稱。 *login*是**sysname**，沒有預設值。 *login*可以是現有的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入或 Windows 使用者或群組。 如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中沒有 Windows 使用者或群組的登入，則會自動加入。  
  
`[ @defdb = ] 'database'`這是新預設資料庫的名稱。 *資料庫*是**sysname**，沒有預設值。 *資料庫*必須已經存在。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="remarks"></a>備註  
 **sp_defaultdb**會呼叫 ALTER LOGIN。 這個陳述式支援其他選項。 如需變更預設資料庫的詳細資訊，請參閱[ALTER LOGIN &#40;transact-sql&#41;](../../t-sql/statements/alter-login-transact-sql.md)。  
  
 **sp_defaultdb**不能在使用者自訂交易內執行。  
  
## <a name="permissions"></a>權限  
 需要 ALTER ANY LOGIN 權限。  
  
## <a name="examples"></a>範例  
 下列範例會將 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 設為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入 `Victoria` 的預設資料庫。  
  
```  
EXEC sp_defaultdb 'Victoria', 'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的安全性預存程式](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-sql&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [sp_addlogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_droplogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
