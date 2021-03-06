---
title: sp_dropremotelogin （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropremotelogin
- sp_dropremotelogin_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropremotelogin
ms.assetid: 9f097652-a286-40b2-be73-568d77ada698
ms.author: vanto
author: VanMSFT
ms.openlocfilehash: c316f48f3e590fcba419e125f8e327b25ee1ede6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "67933827"
---
# <a name="sp_dropremotelogin-transact-sql"></a>sp_dropremotelogin (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  移除對應至本機登入的遠端登入，它可以對執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的本機伺服器執行遠端預存程序。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]請改用連結伺服器和連結伺服器預存程序。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
sp_dropremotelogin [ @remoteserver = ] 'remoteserver'   
     [ , [ @loginame = ] 'login' ]   
     [ , [ @remotename = ] 'remote_name' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @remoteserver = ] 'remoteserver'`這是對應至要移除之遠端登入的遠端伺服器名稱。 *remoteserver*是**sysname**，沒有預設值。 *remoteserver*必須已經存在。  
  
`[ @loginame = ] 'login'`這是本機伺服器上與遠端伺服器相關聯的選擇性登入名稱。 *login* 是預設值為 NULL 的 **sysname**。 若已指定，*登*入必須已經存在。  
  
`[ @remotename = ] 'remote_name'`這是從遠端伺服器登入時，對應至*登*入之遠端登入的選擇性名稱。 *remote_name*是**sysname**，預設值是 Null。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="remarks"></a>備註  
 如果只指定*remoteserver* ，則會從本機伺服器移除該遠端伺服器的所有遠端登入。 如果同時指定*login* ，則會從本機伺服器移除對應至該特定本機登入之*remoteserver*的所有遠端登入。 如果也指定了*remote_name* ，則只會從本機伺服器移除*remoteserver*中該遠端使用者的遠端登入。  
  
 若要新增本機伺服器使用者，請使用**sp_addlogin**。 若要移除本機伺服器使用者，請使用**sp_droplogin**。  
  
 只有當您使用舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，才需要遠端登入。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 版和更新的版本，都改用連結伺服器登入。 使用**sp_addlinkedsrvlogin**和**sp_droplinkedsrvlogin**加入和移除連結的伺服器登入。  
  
 **sp_dropremotelogin**不能在使用者自訂交易內執行。  
  
## <a name="permissions"></a>權限  
 需要**系統管理員（sysadmin** ）或**securityadmin**固定伺服器角色中的成員資格。  
  
## <a name="examples"></a>範例  
  
### <a name="a-dropping-all-remote-logins-for-a-remote-server"></a>A. 卸除遠端伺服器所有的遠端登入  
 下列範例會移除遠端伺服器 `ACCOUNTS` 的項目，因而移除本機伺服器的登入，以及遠端伺服器的遠端登入之間所有的對應。  
  
```sql
EXEC sp_dropremotelogin 'ACCOUNTS';  
```  
  
### <a name="b-dropping-a-login-mapping"></a>B. 卸除登入對應  
 下列範例會移除將遠端伺服器 `ACCOUNTS` 的遠端登入對應至本機登入 `Albert` 的項目。  
  
```sql
EXEC sp_dropremotelogin 'ACCOUNTS', 'Albert';  
```  
  
### <a name="c-dropping-a-remote-user"></a>C. 卸除遠端使用者  
 下列範例會針對遠端伺服器 `Chris` 上對應至本機登入 `ACCOUNTS` 的遠端登入 `salesmgr`，而移除登入。  
  
```sql
EXEC sp_dropremotelogin 'ACCOUNTS', 'salesmgr', 'Chris';  
```  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的安全性預存程式](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addlogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_addremotelogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md)   
 [sp_addserver &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_droplinkedsrvlogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md)   
 [sp_droplogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_helpremotelogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
