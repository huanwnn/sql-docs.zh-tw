---
title: sys. firewall_rules （Azure SQL Database） |Microsoft Docs
ms.date: 03/26/2019
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.firewall_rules
- firewall_rules
- sys.firewall_rules_TSQL
- firewall_rules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- firewall_rules
- sys.firewall_rules
ms.assetid: 140d2cd8-9aa1-4cc5-870d-e1dbc873b3fe
author: CarlRabeler
ms.author: carlrab
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 91c3a4101f19afe4a986514fea8dab207c6d9b48
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "70155545"
---
# <a name="sysfirewall_rules-azure-sql-database"></a>sys.firewall_rules (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  傳回與您[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]的相關聯之伺服器層級防火牆設定的詳細資訊。  
  
  檢視表包含下列資料行：  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|id|**INT**|伺服器層級防火牆設定的識別碼。|  
|NAME|**NVARCHAR （128）**|您選擇用來描述和區分伺服器層級防火牆設定的名稱。|  
|start_ip_address|**VARCHAR （45）**|伺服器層級防火牆設定範圍中最低的 IP 位址。 等於或大於這個位址的 IP 位址可以嘗試連接至 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 伺服器。 可能的最低 IP 位址為 `0.0.0.0`。|  
|end_ip_address|**VARCHAR （45）**|伺服器層級防火牆設定範圍中最高的 IP 位址。 等於或小於這個位址的 IP 位址可以嘗試連接至 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 伺服器。 可能的最高 IP 位址為 `255.255.255.255`。<br /><br /> 注意：當此欄位和 [ **start_ip_address** ] 欄位等於`0.0.0.0`時，便允許 Azure 連接嘗試。|  
|create_date|**從中**|建立伺服器層級防火牆設定時的 UTC 日期和時間。<br /><br /> 注意： UTC 是國際標準時間的縮寫。|  
|modify_date|**從中**|上次修改伺服器層級防火牆設定時的 UTC 日期和時間。|  
  
## <a name="remarks"></a>備註

 若要傳回與您的 Microsoft Azure SQL Database 相關聯之資料庫層級防火牆設定的詳細資訊，請使用[sys.databases database_firewall_rules &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)。  
  
## <a name="permissions"></a>權限

 此視圖的唯讀存取權可供所有具有連接到**master**資料庫之許可權的使用者使用。  
  
## <a name="see-also"></a>另請參閱

[sp_set_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)  
[sp_delete_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-delete-firewall-rule-azure-sql-database.md)   
[sp_set_database_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)  
[sp_delete_database_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)  
[database_firewall_rules &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
[設定資料庫引擎存取的 Windows 防火牆](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)     
[為 FILESTREAM 存取設定防火牆](../../relational-databases/blob/configure-a-firewall-for-filestream-access.md)  
[設定供報表伺服器存取的防火牆](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md) 
