---
title: sys.databases fn_virtualfilestats （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 08/16/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_virtualfilestats_TSQL
- fn_virtualfilestats
dev_langs:
- TSQL
helpviewer_keywords:
- I/O [SQL Server], statistics
- fn_virtualfilestats function
- sys.fn_virtualfilestats function
- statistical information [SQL Server], I/O
ms.assetid: 96b28abb-b059-48db-be2b-d60fe127f6aa
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: aade9e02515e0d18e4edae188d72e5edafebbd3f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2020
ms.locfileid: "68059197"
---
# <a name="sysfn_virtualfilestats-transact-sql"></a>sys.fn_virtualfilestats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  傳回資料庫檔案的 I/O 統計資料，其中包括記錄檔。 在[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，您也可以從[dm_io_virtual_file_stats](../../relational-databases/system-dynamic-management-views/sys-dm-io-virtual-file-stats-transact-sql.md)動態管理檢視取得這項資訊。  

 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
fn_virtualfilestats ( { database_id | NULL } , { file_id | NULL } )  
```  
  
## <a name="arguments"></a>引數  
 *database_id* |Null  
 資料庫的識別碼。 *database_id* 為沒有預設值的 **int**。 請指定 NULL 來傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中之所有資料庫的資訊。  
  
 *file_id* |Null  
 檔案的識別碼。 *file_id*是**int**，沒有預設值。 請指定 NULL 來傳回資料庫中的所有檔案。  
  
## <a name="table-returned"></a>傳回的資料表  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**DbId**|**smallint**|資料庫識別碼。|  
|**FileId**|**smallint**|檔案識別碼。|  
|**TimeStamp**|**bigint**|取得資料的資料庫時間戳記。 **int**在之前[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)]的版本中為 int。 |  
|**NumberReads**|**bigint**|對檔案發出的讀取數。|  
|**BytesRead**|**bigint**|對檔案發出的讀取位元組數。|  
|**IoStallReadMS**|**bigint**|使用者等待完成檔案讀取 I/O 的時間總量 (以毫秒為單位)。|  
|**NumberWrites**|**bigint**|檔案所進行的寫入數。|  
|**BytesWritten**|**bigint**|檔案所進行的寫入位元組數。|  
|**IoStallWriteMS**|**bigint**|使用者等待完成檔案寫入 I/O 的時間總量 (以毫秒為單位)。|  
|**IoStallMS**|**bigint**|**IoStallReadMS**和**IoStallWriteMS**的總和。|  
|**FileHandle**|**bigint**|檔案控制代碼的值。|  
|**BytesOnDisk**|**bigint**|磁碟中的實體檔案大小 (位元組的計數)。<br /><br /> 針對資料庫檔案，此值與 sys.databases 中的**大小**相同 **。 database_files**，但以位元組表示，而不是分頁。<br /><br /> 如果是資料庫快照集疏鬆檔案，這是作業系統供檔案使用的空間。|  
  
## <a name="remarks"></a>備註  
 **fn_virtualfilestats**是提供統計資訊的系統資料表值函式，例如在檔案上執行的 i/o 總數。 您可以利用這個函數來協助您持續追蹤使用者必須等待讀取或寫入檔案的時間長度。 這個函數也可以協助您識別發生大量 I/O 活動的檔案。  
  
## <a name="permissions"></a>權限  
 需要伺服器的 VIEW SERVER STATE 權限。  
  
## <a name="examples"></a>範例  
  
### <a name="a-displaying-statistical-information-for-a-database"></a>A. 顯示資料庫的統計資訊  
 下列範例會顯示識別碼為 `1` 的資料庫中之檔案識別碼 1 的統計資訊。  
  
```sql  
SELECT *  
FROM fn_virtualfilestats(1, 1);  
GO  
```  
  
### <a name="b-displaying-statistical-information-for-a-named-database-and-file"></a>B. 顯示具名資料庫和檔案的統計資訊  
 下列範例會顯示 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 範例資料庫中之記錄檔的統計資訊。 系統函數`DB_ID`是用來指定*database_id*參數。  
  
```sql  
SELECT *  
FROM fn_virtualfilestats(DB_ID(N'AdventureWorks2012'), 2);  
GO  
```  
  
### <a name="c-displaying-statistical-information-for-all-databases-and-files"></a>C. 顯示所有資料庫和檔案的統計資訊  
 下列範例會顯示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中所有資料庫內所有檔案的統計資訊。  
  
```sql  
SELECT *  
FROM fn_virtualfilestats(NULL,NULL);  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [DB_ID &#40;Transact-sql&#41;](../../t-sql/functions/db-id-transact-sql.md)   
 [FILE_IDEX &#40;Transact-sql&#41;](../../t-sql/functions/file-idex-transact-sql.md)   
 [database_files &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  
