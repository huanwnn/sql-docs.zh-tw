---
title: 預設追蹤記錄檔已停用 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c27761e6-75ed-4ee4-a236-0cbc42e500a1
caps.latest.revision: 10
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: daf6232dadd58244213c1f254eec3fd306a9ee63
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37270754"
---
# <a name="default-trace-log-files-disabled"></a>預設追蹤記錄檔已停用
  此規則會檢查 sp_configure 預存程序 default trace enabled 選項的值，以判斷預設追蹤是否設定為 ON (1) 或 OFF (0)。 當啟用這個選項時，預設追蹤會提供有關組態及 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]之 DDL 變更的資訊。 在某些情況下，當客戶和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客戶服務及支援中心在排除 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的問題時，這項資訊對於他們很有幫助。  
  
## <a name="best-practices-recommendations"></a>最佳做法建議  
 使用 sp_configure 預存程序，將 default trace enabled 設定為 1 的值來啟用追蹤。  
  
## <a name="for-more-information"></a>詳細資訊  
 [伺服器組態選項 &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用原則式管理來監視和強制最佳做法](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  