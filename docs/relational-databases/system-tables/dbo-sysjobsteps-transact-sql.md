---
title: dbo.sysjobsteps （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysjobsteps
- dbo.sysjobsteps_TSQL
- sysjobsteps
- sysjobsteps_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobsteps system table
ms.assetid: 978b8205-535b-461c-91f3-af9b08eca467
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4bf7ed1c52aedb63ffe1e2e257022e004b327787
ms.sourcegitcommit: dc6ea6665cd2fb58a940c722e86299396b329fec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84423371"
---
# <a name="dbosysjobsteps-transact-sql"></a>dbo.sysjobsteps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 所要執行之作業中各個步驟的資訊。 此資料表會儲存在**msdb**資料庫中。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|作業的識別碼。|  
|**step_id**|**int**|作業中步驟的識別碼。|  
|**step_name**|**sysname**|作業步驟的名稱。|  
|**子系統**|**nvarchar(40)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 用來執行作業步驟的子系統名稱。|  
|**command**|**nvarchar(max)**|要由**子系統**執行的命令。|  
|**flags**|**int**|已保留。|  
|**additional_parameters**|**ntext**|已保留。|  
|**cmdexec_success_code**|**int**|**CmdExec**子系統步驟傳回的錯誤層級值，表示成功。|  
|**on_success_action**|**tinyint**|當步驟執行成功時，所要執行的動作。<br /><br /> **1** = （預設值）結束並成功<br /><br /> **2** = 結束但失敗<br /><br /> **3** = 移至下一個步驟<br /><br /> **4** = 移至步驟_on_success_step_id_|
|**on_success_step_id**|**int**|當步驟執行成功時，所要執行的下一個步驟的識別碼。|  
|**on_fail_action**|**tinyint**|當步驟執行不成功時，所要執行的動作。<br /><br /> **1** = 成功結束<br /><br /> **2** = （預設值）結束但失敗<br /><br /> **3** = 移至下一個步驟<br /><br /> **4** = 移至步驟_on_fail_step_id_|
|**on_fail_step_id**|**int**|當步驟執行不成功時，所要執行的下一個步驟的識別碼。|  
|**伺服器**|**sysname**|已保留。|  
|**database_name**|**sysname**|當**子系統**是 TSQL 時，用來執行**命令**的資料庫名稱。|  
|**database_user_name**|**sysname**|當執行步驟時，將使用其帳戶的資料庫使用者名稱。|  
|**retry_attempts**|**int**|作業失敗時的重試次數。|  
|**retry_interval**|**int**|重試的間隔等待時間。|  
|**os_run_priority**|**int**|已保留。|  
|**output_file_name**|**nvarchar(200)**|當**子系統**是 TSQL、PowerShell 或**CmdExec**時，儲存步驟輸出的檔案名 _。_|  
|**last_run_outcome**|**int**|作業步驟上次執行的結果。<br /><br /> **0** = 失敗<br /><br /> **1** = 成功<br /><br /> **2** = 重試<br /><br /> **3** = 已取消<br /><br /> **5** = 未知|  
|**last_run_duration**|**int**|上次執行步驟的持續期間 (hhmmss)。|  
|**last_run_retries**|**int**|作業步驟上次執行的重試次數。|  
|**last_run_date**|**int**|上次開始執行步驟的日期 (yyyymmdd)。|  
|**last_run_time**|**int**|上次開始執行步驟的時間 (hhmmss)。|  
|**proxy_id**|**int**|作業步驟的 Proxy。|  
|**step_uid**|**uniqueidentifier**|作業步驟的識別碼。|  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Agent 資料表 &#40;Transact-sql&#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
