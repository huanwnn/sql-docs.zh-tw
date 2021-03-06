---
title: managed_backup. sp_backup_master_switch （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_ backup_master_switch
- smart_admin.sp_backup_master_switch
- sp_ backup_master_switch_TSQL
- smart_admin.sp_backup_master_switch_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_ backup_master_switch
- smart_admin.sp_backup_master_switch
ms.assetid: 1ed2b2b2-c897-41cc-bed5-1c6bc47b9dd2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 242ef833cbb5a6a54b52fba0d1f435a7ca475cf0
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830362"
---
# <a name="managed_backupsp_backup_master_switch-transact-sql"></a>managed_backup. sp_backup_master_switch （Transact-sql）
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  暫停或繼續執行[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]。  
  
 使用此預存程序可暫停再繼續執行[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]。 如此可確保所有組態設定都會留下，並在作業繼續執行時保留。 暫停[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]時，不會強制執行保留期間。 這表示，不會檢查並判斷是否應該從儲存體中刪除檔案，或者是否發生備份檔案損毀或記錄鏈結中斷的情況。  
  

  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```sql  
EXEC managed_backup.sp_backup_master_switch   
                     [@new_state = ] { 0 | 1}  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>參量  
 @state  
 設定 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 的狀態。 @state參數為**BIT**。 當值設定為 0 時，作業會暫停；當值設定為 1 時，作業會繼續執行。  
  
## <a name="return-code-value"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="security"></a>安全性  
 描述與陳述式相關的安全性問題。加入＜權限＞小節 (H3 標題)。 考慮加入＜擁有權鏈結＞和＜稽核＞小節 (如果適用)。  
  
### <a name="permissions"></a>權限  
 需要**db_backupoperator**資料庫角色中的成員資格、具有**ALTER ANY CREDENTIAL**許可權，以及**Sp_delete_backuphistory**預存程式的**EXECUTE**許可權。  
  
## <a name="examples"></a>範例  
 下列範例可用來暫停在執行個體上執行的[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]：  
  
```  
Use msdb;  
GO  
EXEC managed_backup.sp_backup_master_switch @new_state=0;  
Go  
  
```  
  
 下列範例可用來繼續執行[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]。  
  
```  
Use msdb;  
GO  
EXEC managed_backup.sp_backup_master_switch @new_state=1;  
Go  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server 受控備份到 Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
