---
title: 參數標記 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- parameter markers [ODBC]
ms.assetid: 07213d04-cd31-45fd-a8c8-2e16e09eeaf4
author: David-Engel
ms.author: v-daenge
ms.reviewer: ''
ms.openlocfilehash: 132473de586094f79dd34c999d44f6dd59aefaef
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303569"
---
# <a name="parameter-markers"></a>參數標記
根據 SQL-92 規格，應用程式無法將參數標記放在下列位置。 如需更完整的清單，請參閱 SQL-92 規格。  
  
-   在**選取**清單中  
  
-   做為*比較*述詞中的兩個*運算式*  
  
-   做為二元運算子的兩個運算元  
  
-   當做**BETWEEN**運算的第一個和第二個運算元  
  
-   當做**BETWEEN**運算的第一個和第三個運算元  
  
-   同時做為**IN**運算的運算式和第一個值  
  
-   做為一元 + 或-運算的運算元  
  
-   當做*集合函數參考*的引數  
  
 如需參數標記的詳細資訊，請參閱 SQL-92 規格。 如需參數的詳細資訊，請參閱[語句參數](../../../odbc/reference/develop-app/statement-parameters.md)。
