---
title: SQLTransact 對應 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLTransact
- SQLTransact function [ODBC], mapping
ms.assetid: 8a01041f-3572-46f9-8213-b817f3cf929c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6aaa056fca860a70f81ad7c3a4cd8539512bc25d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304879"
---
# <a name="sqltransact-mapping"></a>SQLTransact 對應
**SQLTransact**現在已由**SQLEndTran**取代。 這兩個函式的主要差異在於， **SQLEndTran**包含引數*HandleType*，這會指定要執行之工作的範圍。 *HandleType*引數可以指定環境或連接控制碼。 下列對**SQLTransact**的呼叫：  
  
```  
SQLTransact(henv, hdbc, fType)  
```  
  
 對應至  
  
```  
SQLEndTran(SQL_HANDLE_DBC, ConnectionHandle, CompletionType);  
```  
  
 如果*ConnectionHandle*不等於 SQL_Null_HDBC。 *ConnectionHandle*引數會設定為*hdbc*的值。  
  
 **SQL_Transact**對應至  
  
```  
SQLEndTran (SQL_HANDLE_ENV, EnvironmentHandle, CompletionType);  
```  
  
 如果*ConnectionHandle*等於 SQL_Null_HDBC。 *EnvironmentHandle*引數會設定為*henv*的值。  
  
 在上述兩種情況中， *CompletionType*引數會設定為與*fType*相同的值。
