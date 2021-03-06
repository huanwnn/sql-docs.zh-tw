---
title: 定量運算式（XQuery） |Microsoft Docs
description: 瞭解如何在 XQuery 中使用量化運算式，將存在或通用定量套用至一或多個序列的運算式。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- universal quantifiers
- effective Boolean value [XQuery]
- quantified expressions [XQuery]
- XQuery, quantified expressions
- every expression [XQuery]
- existential quantifiers [XQuery]
- some expression [XQuery]
- EBV
- expressions [XQuery], quantifiers
ms.assetid: a3a75a6c-8f67-4923-8406-1ada546c817f
author: rothja
ms.author: jroth
ms.openlocfilehash: 5f7c79cd185b88b8681460d2811f0d0ac4c20557
ms.sourcegitcommit: 9921501952147b9ce3e85a1712495d5b3eb13e5b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84215244"
---
# <a name="quantified-expressions-xquery"></a>定量運算式 (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  存在和通用的數量詞可指定布林運算式的不同語意，以適用於兩種時序。 如下表所示。  
  
 *存在數量詞*  
 根據所使用的比較運算子，如果在第一個時序中有任何項目符合第二個時序中的項目，則傳回的值將為 True。  
  
 *通用數量詞*  
 假使有兩個時序，如果在第一個時序中的每個項目都在第二個時序中有符合的項目，則傳回的值將為 True。  
  
 XQuery 支援下列形式的定量運算式：  
  
```  
( some | every ) <variable> in <Expression> (,...) satisfies <Expression>  
```  
  
 您可以在查詢中使用這些運算式，以明確地將存在或通用定量套用至一或多個時序中的運算式。 在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中，`satisfies` 子句中的運算式必須產生下列其中一個：節點時序、空白時序或布林值。 該運算式所產生的有效布林值結果將用於定量中。 如果數量詞所系結的至少一個值在滿足運算式中產生 True 結果，則使用**部分**的存在定量會傳回 true。 針對數量詞所系結的所有值，使用**每個**的通用定量都必須為 True。  
  
 例如，下列查詢會檢查每個 \<Location> 元素，以查看它是否有 LocationID 屬性。  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
        if (every $WC in //AWMI:root/AWMI:Location   
            satisfies $WC/@LocationID)  
        then  
             <Result>All work centers have workcenterLocation ID</Result>  
         else  
             <Result>Not all work centers have workcenterLocation ID</Result>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 因為 LocationID 是元素的必要屬性 \<Location> ，所以您會收到預期的結果：  
  
```  
<Result>All work centers have Location ID</Result>   
```  
  
 除了使用[query （）方法](../t-sql/xml/query-method-xml-data-type.md)，您可以使用[value （）方法](../t-sql/xml/value-method-xml-data-type.md)將結果傳回給關聯式世界，如下列查詢所示。 如果所有的工作中心位置都有 LocationID 屬性，查詢將會傳回 True。 否則，查詢會傳回 False。  
  
```  
SELECT Instructions.value('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
        every $WC in  //AWMI:root/AWMI:Location   
            satisfies $WC/@LocationID',   
  'nvarchar(10)') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 下列查詢檢查其中一個產品圖片是否為小型的。 在產品目錄 XML 中，每個不同大小的產品圖片均以各種角度儲存。 您可能會想要確保每個產品目錄 XML 至少包含一個小型圖片。 下列查詢可達成此目的：  
  
```  
SELECT ProductModelID, CatalogDescription.value('  
     declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     some $F in /PD:ProductDescription/PD:Picture  
        satisfies $F/PD:Size="small"', 'nvarchar(20)') as SmallPicturesStored  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 以下是部份結果：  
  
```  
ProductModelID SmallPicturesStored   
-------------- --------------------  
19             true        
```  
  
## <a name="implementation-limitations"></a>實作限制  
 以下為其限制：  
  
-   在定量運算式中不支援類型判斷做為繫結變數的一部份。  
  
## <a name="see-also"></a>另請參閱  
 [XQuery 運算式](../xquery/xquery-expressions.md)  
  
  
