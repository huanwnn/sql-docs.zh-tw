---
title: PageSize 屬性（ADO） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::PageSize
helpviewer_keywords:
- PageSize property [ADO]
ms.assetid: e57930a6-46c4-4a17-a3b6-f79e94d5c9c7
author: rothja
ms.author: jroth
ms.openlocfilehash: 97902985dcd2110b165498be5324393ad5588bac
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761967"
---
# <a name="pagesize-property-ado"></a>PageSize 屬性 (ADO)
指出有多少記錄構成[記錄集中](../../../ado/reference/ado-api/recordset-object-ado.md)的一個頁面。  
  
## <a name="settings-and-return-values"></a>設定和傳回值  
 設定或傳回**Long**值，指出頁面上有多少筆記錄。 預設值為**10**。  
  
## <a name="remarks"></a>備註  
 使用**PageSize**屬性來決定組成邏輯頁面的記錄數目。 建立頁面大小可讓您使用[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)屬性移至特定頁面的第一筆記錄。 當您想要讓使用者逐頁流覽資料、一次查看特定數目的記錄時，這在 Web 服務器案例中很有用。  
  
 您可以隨時設定此屬性，其值將用來計算特定頁面的第一筆記錄位置。  
  
## <a name="applies-to"></a>套用至  
 [Recordset 物件 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [AbsolutePage、PageCount 和 PageSize 屬性範例（VB）](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [AbsolutePage、PageCount 和 PageSize 屬性範例（VC + +）](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [AbsolutePage 屬性（ADO）](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [PageCount 屬性 (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)
