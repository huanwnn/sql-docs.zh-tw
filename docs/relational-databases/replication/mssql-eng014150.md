---
title: MSSQL_ENG014150 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014150 error
ms.assetid: c3dd3109-abf3-4b38-a4e9-ef48d0235656
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 2d006558894137ab627a53da8b2543a1ad57fbac
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "76287805"
---
# <a name="mssql_eng014150"></a>MSSQL_ENG014150
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>訊息詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|14150|  
|事件來源|MSSQLSERVER|  
|元件|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|符號名稱||  
|訊息文字|複寫 -%s：代理程式 %s 成功。 %s|  
  
## <a name="explanation"></a>說明  
 這個訊息表示複寫代理程式已順利地完成執行。 複寫使用下列代理程式：  
  
-   快照集代理程式。 此代理程式是由所有發行集使用。  
  
-   記錄讀取器代理程式。 此代理程式是由所有交易式發行集使用。  
  
-   佇列讀取器代理程式。 此代理程式是由為佇列更新訂閱而啟用的交易式發行集使用。  
  
-   散發代理程式。 此代理程式會同步處理交易式和快照式發行集的訂閱。  
  
-   合併代理程式。 此代理程式會同步處理合併發行集的訂閱。  
  
-   複寫維護作業。  
  
## <a name="user-action"></a>使用者動作  
 記錄讀取器代理程式、佇列讀取器代理程式，以及散發代理程式通常都是連續執行，而其他代理程式則通常是視需要或依排程執行。 如果不認為代理程式已完成執行，請檢查代理程式的狀態。 如需相關資訊，請參閱 [Monitor Replication Agents](../../relational-databases/replication/monitor/monitor-replication-agents.md)。  
  
## <a name="see-also"></a>另請參閱  
 [複寫代理程式管理](../../relational-databases/replication/agents/replication-agent-administration.md)   
 [錯誤和事件參考 &#40;複寫&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Replication Log Reader Agent](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [複寫佇列讀取器代理程式](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  
