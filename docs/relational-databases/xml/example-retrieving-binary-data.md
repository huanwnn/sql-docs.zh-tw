---
title: 範例：擷取二進位資料 | Microsoft Docs
ms.custom: ''
ms.date: 04/03/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, retrieving binary data example
ms.assetid: 5cea5d49-58ac-403a-a933-c4fd91de400b
author: RothJa
ms.author: jroth
ms.openlocfilehash: 8d66e1ec9c580030f1f65f030cdb0367d8f4f430
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664497"
---
# <a name="example-retrieving-binary-data"></a>範例：擷取二進位資料

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

下列查詢會傳回儲存在 **varbinary(max)** 類型資料行中的產品相片。 在查詢中指定 `BINARY BASE64` 選項，以便將二進位資料透過 Base64 編碼格式傳回。

## <a name="example"></a>範例

```sql
USE AdventureWorks2012;
GO
SELECT ProductPhotoID, ThumbNailPhoto
FROM Production.ProductPhoto
WHERE ProductPhotoID=1
FOR XML RAW, BINARY BASE64 ;
GO
```

預期會有下列結果：

```console
<row ProductModelID="1" ThumbNailPhoto="base64 encoded binary data"/>
```

## <a name="see-also"></a>另請參閱

[搭配 FOR XML 使用 RAW 模式](../../relational-databases/xml/use-raw-mode-with-for-xml.md)
