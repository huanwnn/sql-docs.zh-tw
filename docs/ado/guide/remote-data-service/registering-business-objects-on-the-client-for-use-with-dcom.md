---
title: 在用戶端上註冊商務物件以搭配 DCOM 使用 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- business objects in RDS [ADO]
ms.assetid: 75a21910-607f-463a-ae18-a17130dafb7e
author: rothja
ms.author: jroth
ms.openlocfilehash: 79f88f36b7eae83163ef2754f9b2c2265550c684
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2020
ms.locfileid: "82747662"
---
# <a name="registering-business-objects-on-the-client-for-use-with-dcom"></a>在用戶端上註冊商務物件以用於 DOM
自訂商務物件必須確保用戶端能夠將其程式名稱（ProgId）對應至可透過 DCOM 使用的識別碼（CLSID）。 因此，DCOM 物件的 ProgID 必須在用戶端登錄中，並對應至伺服器端商務物件的類別識別碼。 對於其他支援的通訊協定（HTTP、HTTPS 和同進程），這不是必要的。  
  
> [!IMPORTANT]
>  從 Windows 8 和 Windows Server 2012 開始，Windows 作業系統不再包含 RDS 伺服器元件（如需詳細資訊，請參閱 Windows 8 和[Windows Server 2012 相容性操作手冊](https://www.microsoft.com/download/details.aspx?id=27416)）。 RDS 用戶端元件將會在未來的 Windows 版本中移除。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 使用 RDS 的應用程式應該遷移至[WCF 資料服務](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
 例如，如果您使用特定類別識別碼公開名為 MyBObj 的伺服器端商務物件（例如 "{00112233-4455-6677-8899-00AABBCCDDEE}"），請確定已將下列專案新增至用戶端登錄：  
  
```console
[HKEY_CLASSES_ROOT]  
\MyBObj\Clsid\(Default) "{00112233-4455-6677-8899-00AABBCCDDEE}"  
```


