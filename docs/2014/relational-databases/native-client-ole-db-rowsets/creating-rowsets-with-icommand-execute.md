---
title: '使用 icommand:: Execute 建立資料列集 |Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
- Execute method
ms.assetid: 9b530b7d-8165-49d4-a978-5ced17c6705e
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 28bfeafa028ce88b0d8132d0fdd2e29eab85b246
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420767"
---
# <a name="creating-rowsets-with-icommandexecute"></a>使用 ICommand:: Execute 建立資料列集
  使用所建立的資料列集**icommand:: Execute**方法，您想要在產生的資料列集的屬性可以限制命令的文字。 這對於支援動態命令文字的取用者而言，特別重要。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者無法使用[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料指標支援許多命令所產生的多個資料列集結果。 如果取用者要求需要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料指標支援的資料列集，當命令文字產生多個單一資料列集做為其結果時，會發生錯誤。 如需詳細資訊，請參閱 <<c0> [ 命令產生多個資料列集結果](../native-client-ole-db-commands/commands-generating-multiple-rowset-results.md)。  
  
 可捲動[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者資料列集都受到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料指標。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會針對受其他資料庫使用者所進行之變更影響的資料指標，強制施行限制。 特別是，某些資料指標中的資料列無法進行排序，而且嘗試使用包含 SQL ORDER BY 子句的命令建立資料列集可能會失敗。 如需詳細資訊，請參閱 <<c0> [ 資料列集和 SQL Server 資料指標](rowsets-and-sql-server-cursors.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料列集](rowsets.md)  
  
  