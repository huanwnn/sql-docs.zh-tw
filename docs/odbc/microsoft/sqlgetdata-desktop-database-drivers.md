---
title: SQLGetData （桌面資料庫驅動程式） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetData function [ODBC], Desktop Database Drivers
ms.assetid: c9d9a32d-5dc2-4189-9bfb-2b008bc3d6a3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2b102d8435831d45aad3c2049581513e0493de9a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304119"
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (桌面資料庫驅動程式)
此函式可以從任何資料行抓取資料，不論其是否有系結的資料行，以及是否會取得資料行的提取順序。  
  
> [!NOTE]  
>  \*當系結至 Jet 4.0 資料庫上超過510個字元的 ANSI 資料時， **SQLGetData**中的 pcbValue 可能會傳回兩倍的字元。 510或更少的字元值會傳回實際的 cbValue。
