---
title: SQL 到 C 資料轉換範例 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from SQL to C types [ODBC], examples
- converting data from SQL to C types [ODBC], examples
ms.assetid: 0190c76c-7f9b-42f4-be9d-cef7284840fd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 96b10dd93c807aaa49a7e10e198f789fb47ccdeb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "81296648"
---
# <a name="sql-to-c-data-conversion-examples"></a>SQL 到 C 資料轉換範例

下表所示的範例說明驅動程式如何將 SQL 資料轉換成 C 資料：  
  
|SQL 類型<br /><br /> 識別碼 (identifier)|SQL 資料<br /><br /> value|C 類型<br /><br /> 識別碼 (identifier)|Buffer<br /><br /> 長度|**TargetValuePtr*|SQLSTATE|  
|-----------------------------|------------------------|---------------------------|-----------------------|------------------------|--------------|  
|SQL_CHAR|abcdef|SQL_C_CHAR|7|abcdef\0 [a]|n/a|  
|SQL_CHAR|abcdef|SQL_C_CHAR|6|abcde\0 [a]|01004|  
|SQL_DECIMAL|1234.56|SQL_C_CHAR|8|1234.56 \ 0 [a]|n/a|  
|SQL_DECIMAL|1234.56|SQL_C_CHAR|5|1234 \ 0 [a]|01004|  
|SQL_DECIMAL|1234.56|SQL_C_CHAR|4|----|22003|  
|SQL_DECIMAL|1234.56|SQL_C_FLOAT|忽略|1234.56|n/a|  
|SQL_DECIMAL|1234.56|SQL_C_SSHORT|忽略|1234|01S07|  
|SQL_DECIMAL|1234.56|SQL_C_STINYINT|忽略|----|22003|  
|SQL_DOUBLE|1.2345678|SQL_C_DOUBLE|忽略|1.2345678|n/a|  
|SQL_DOUBLE|1.2345678|SQL_C_FLOAT|忽略|1.234567|n/a|  
|SQL_DOUBLE|1.2345678|SQL_C_STINYINT|忽略|1|n/a|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_CHAR|11|1992-12-31 \ 0 [a]|n/a|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_CHAR|10|-----|22003|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_TIMESTAMP|忽略|1992，12，31，0，0，0，0 [b]|n/a|  
|SQL_TYPE_TIMESTAMP|1992-12-31 23：45：55.12|SQL_C_CHAR|23|1992-12-31 23：45： 55.12 \ 0 [a]|n/a|  
|SQL_TYPE_TIMESTAMP|1992-12-31 23：45：55.12|SQL_C_CHAR|22|1992-12-31 23：45： 55.1 \ 0 [a]|01004|  
|SQL_TYPE_TIMESTAMP|1992-12-31 23：45：55.12|SQL_C_CHAR|18|----|22003|  
  
 [a] "\ 0" 代表 null 終止位元組。 驅動程式一律會以 null 結束 SQL_C_CHAR 資料。  
  
 [b] 這份清單中的數位是儲存在 TIMESTAMP_STRUCT 結構之欄位中的數位。
