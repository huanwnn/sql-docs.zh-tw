---
title: sys.databases endpoint_webmethods （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.endpoint_webmethods_TSQL
- sys.endpoint_webmethods
- endpoint_webmethods_TSQL
- sys.http_soap_methods_TSQL
- endpoint_webmethods
- sys.http_soap_methods
dev_langs:
- TSQL
helpviewer_keywords:
- sys.endpoint_webmethods catalog view
ms.assetid: 7dad0cf6-eafa-47cf-98cc-75ba8d3c7959
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1d3d9c528b7fd74055e5a98348b9766af320b7d7
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829707"
---
# <a name="sysendpoint_webmethods-transact-sql"></a>sys.endpoint_webmethods (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 包含定義在啟用 SOAP 之 HTTP 端點的一個資料列 FOR EACH SOAP 方法。 endpoint_id 和 namespace 資料行的組合是唯一的。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|endpoint_id|**int**|定義 webmethod 的端點識別碼。|  
|namespace|**Nvarchar （384）**|webmethod 的命名空間。|  
|method_alias|**Nvarchar （64）**|方法的別名。<br /><br /> 注意： [!INCLUDE[tsql](../../includes/tsql-md.md)] 識別碼允許在 WSDL 方法名稱中不合法的字元。<br /><br /> 這個別名用來將端點之 WSDL 描述所顯示的名稱，對應至當叫用 webmethod 時所呼叫的實際基礎 [!INCLUDE[tsql](../../includes/tsql-md.md)] 可執行物件。|  
|object_name|**Nvarchar （776）**|根據 NAME = 選項的指定，重新導向 webmethod 所至的物件名稱。 名稱部分是以句點（.）分隔，並使用方括弧分隔 `[``]` 。<br /><br /> 根據 WSDL 選項的指定，物件名稱必須是三部分名稱。|  
|result_schema|**tinyint**|決定哪一個 (如果有的話) XSD 會隨同回應被傳回的選項。<br /><br /> 0 = 無<br /><br /> 1 = 標準<br /><br /> 2 = 預設值|  
|result_schema_desc|**nvarchar(60)**|決定哪一個 (如果有的話) XSD 會隨同回應被傳回的選項描述。<br /><br /> 無<br /><br /> STANDARD<br /><br /> DEFAULT|  
|result_format|**tinyint**|決定回應中的結果如何格式化的選項。<br /><br /> 1 = ALL_RESULTS<br /><br /> 2 = ROWSETS_ONLY<br /><br /> 3 = NONE|  
|result_format_desc|**nvarchar(60)**|決定回應中的結果如何格式化的選項描述。<br /><br /> ALL_RESULTS<br /><br /> ROWSETS_ONLY<br /><br /> 無|  
  
## <a name="permissions"></a>權限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [端點目錄檢視 &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)   
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
