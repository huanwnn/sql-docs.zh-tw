---
title: SMTP 連線管理員編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.smtpconnection.f1
helpviewer_keywords:
- SMTP Connection Manager Editor
ms.assetid: 2693de0d-b04d-4325-a856-ce667d2b8aa1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 527c8f647c963c2c1c03171eeb154a790ab1994a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2020
ms.locfileid: "66055554"
---
# <a name="smtp-connection-manager-editor"></a>SMTP 連接管理員編輯器
  使用 [SMTP 連線管理員編輯器]**** 對話方塊指定簡易郵件傳輸通訊協定 (SMTP) 伺服器。  
  
 若要深入了解 SMTP 連接管理員，請參閱＜ [SMTP Connection Manager](connection-manager/smtp-connection-manager.md)＞。  
  
## <a name="options"></a>選項。  
 **名稱**  
 提供唯一的名稱給連接管理員。  
  
 **描述**  
 描述連接管理員。 最佳作法是以其用途描述連接管理員，使封裝可以自我記錄並易於維護。  
  
 **SMTP 伺服器**  
 提供 SMTP 伺服器的名稱。  
  
 **[使用 Windows 驗證]**  
 選取此選項即可使用以 Windows 驗證來驗證伺服器存取權的 SMTP 伺服器，以便傳送郵件。  
  
> [!IMPORTANT]  
>  SMTP 連接管理員僅支援匿名驗證和 Windows 驗證， 而不支援基本驗證。  
  
> [!NOTE]  
>  使用 Microsoft Exchange 做為 SMTP 伺服器時，您可能需要將 [**使用 Windows 驗證**] `True`設定為。 Exchange 伺服器可以設定成不允許未驗證的 SMTP 連接。  
  
 **啟用安全通訊端層 (SSL)**  
 選擇在傳送電子郵件訊息時以安全通訊端層 (SSL) 將通訊加密。  
  
## <a name="see-also"></a>另請參閱  
 [Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
