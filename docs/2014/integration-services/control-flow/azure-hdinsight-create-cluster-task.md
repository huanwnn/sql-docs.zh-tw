---
title: Azure HDInsight 建立叢集工作 | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpcreatecltask.f1
- sql11.dts.designer.afpcreatecltask.f1
ms.assetid: a8ec413a-38d3-45df-887e-6f5f4d9f8465
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 133e09c81b17b9c30c061da62e5dbc45d70ae838
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37246868"
---
# <a name="azure-hdinsight-create-cluster-task"></a>Azure HDInsight 建立叢集工作
[Azure HDInsight 建立叢集工作] 可讓 SSIS 套件在指定的 Azure 訂用帳戶和資源群組中建立 Azure HDInsight 叢集。
  
> [!NOTE]  
> - 建立新的 HDInsight 叢集可能需要 10~20 分鐘。  
> - 建立與執行 Azure HDInsight 叢集需要支付相關成本。 如需詳細資料，請參閱 [HDInsight 價格](http://azure.microsoft.com/en-us/pricing/details/hdinsight/)。  
  
若要加入 [Azure HDInsight Create Cluster Task (Azure HDInsight 建立叢集工作)]，請將其拖放至 SSIS 設計師，並按兩下或在其上按一下滑鼠右鍵，然後按一下 [編輯]，即可看到以下 [Azure HDInsight Create Cluster Task Editor (Azure HDInsight 建立叢集工作編輯器)] 對話方塊。  
  
下表提供此對話方塊的欄位描述。  
  
|||  
|-|-|  
|**欄位**|**說明**|  
|AzureResourceManagerConnection|選取現有的 Azure Resource Manager 連線管理員或建立新的連線管理員，用以建立 HDInsight 叢集。|  
|AzureStorageConnection|選取現有的 Azure 儲存體連線管理員，或建立參考 Azure 儲存體帳戶的新連線管理員，該連線管理員會與 HDInsight 叢集建立關聯。|
|SubscriptionId|指定 HDInsight 叢集日後建立所在的訂用帳戶識別碼。|
|ResourceGroup|指定 HDInsight 叢集日後建立所在的 Azure 資源群組。|
|位置|指定 HDInsight 叢集的位置。 叢集必須建立在和 Azure 儲存體帳戶指定位置相同的位置。|  
|ClusterName|指定要建立的 HDInsight 叢集名稱。|  
|ClusterSize|指定要在叢集中建立的節點數目。|  
|BlobContainer|指定要與 HDInsight 叢集建立關聯的預設儲存體容器名稱。|  
|UserName|指定連線至 HDInsight 叢集要使用的使用者名稱。|  
|[密碼]|指定連線至 HDInsight 叢集要使用的密碼。|
|SshUserName|指定從遠端存取使用 SSH 的 HDInsight 叢集時所用的使用者名稱。|
|SshPassword|指定從遠端存取使用 SSH 的 HDInsight 叢集時所用的密碼。|
|FailIfExists|指定若叢集已存在則工作是否會失敗。|  
  
> [!NOTE]  
> HDInsight 叢集與 Azure 儲存體帳戶的位置必須相同。