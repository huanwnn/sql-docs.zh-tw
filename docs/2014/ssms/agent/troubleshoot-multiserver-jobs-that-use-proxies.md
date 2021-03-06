---
title: 針對使用 Proxy 的多伺服器作業進行疑難排解 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], multiserver jobs
- jobs [SQL Server Agent], multiserver jobs using proxies
ms.assetid: fc579bd3-010c-4f72-8b5c-d0cc18a1f280
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 47e3c3991bd4732d542bf1ce79e83000e738ff77
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2020
ms.locfileid: "63245417"
---
# <a name="troubleshoot-multiserver-jobs-that-use-proxies"></a>針對使用 Proxy 的多伺服器作業進行疑難排解
  這是在目標伺服器上，於 Proxy 帳戶的環境下執行 Proxy 之相關聯步驟的散發式作業。 如果使用 Proxy 帳戶從主要伺服器下載的作業步驟失敗，請在 **msdb** 資料庫的 **sysdownloadlist** 資料表中，檢查 **error_message** 資料行，以了解下列錯誤訊息：  
  
-   「作業步驟需要 Proxy 帳戶，不過目標伺服器上已停用 Proxy 比對。」  
  
     若要解決此錯誤，請設定**\ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT\MICROSOFT SQL Server\MSSQL.**> **\SQLServerAgent\AllowDownloadedJobsToMatchProxyName** _ \<n_\SQLServerAgent\AllowDownloadedJobsToMatchProxyName 登錄子機碼為**1 （true）**。 根據預設，這個子機碼設定**0**為 0`false`（）。 MSSQL 的值 **。**\< *n*> 是實例名稱;例如， **mssql. 1**或**mssql. 3**。  
  
-   「找不到 Proxy。」  
  
     若要解決此錯誤，請確定目標伺服器上有 Proxy 帳戶，且帳戶名稱與執行該作業步驟的主要伺服器 Proxy 帳戶相同。  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [建立多伺服器環境](create-a-multiserver-environment.md)  
  
  
