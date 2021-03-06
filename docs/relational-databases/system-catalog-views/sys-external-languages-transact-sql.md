---
title: sys. external_languages （Transact-sql）-SQL Server |Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- external_languages
- external_languages_TSQL
- sys.external_languages
- sys.external_languages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_languages catalog view
author: nelgson
ms.author: negust
ms.reviewer: dphansen
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 053a7cdcf21775525b0eb8d46bbbfdf03098e03c
ms.sourcegitcommit: 1be90e93980a8e92275b5cc072b12b9e68a3bb9a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84627277"
---
# <a name="sysexternal_languages-transact-sql"></a>sys.databases external_languages （Transact-sql）
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

此目錄檢視會提供資料庫中的外部語言清單。 **R** 和 **Python** 為保留的名稱，且不能使用這些特定的名稱來建立任何外部語言。

## <a name="sysexternal_languages"></a>sys.external_languages

目錄檢視 sys. external_languages 會針對資料庫中的每個外部語言列出一個資料列。

|資料行名稱 |資料類型 | 描述|
|------|------|------|
|external_language_id |int | 外部語言的識別碼|
|語言 |sysname |外部語言的名稱。 在資料庫中，這是唯一的。 R 和 Python 是每個實例的保留名稱|
|create_date |datetime2 |建立的日期和時間|
|principal_id |int |擁有此外部程式庫之主體的識別碼|

## <a name="see-also"></a>另請參閱  

+ [sys.external_language_files](sys-external-language-files-transact-sql.md)  
+ [建立外部語言](../../t-sql/statements/create-external-language-transact-sql.md) 
