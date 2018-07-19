---
title: 以指令碼工作來擴充套件 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- scripts [Integration Services]
- SSIS Script task
- tasks [Integration Services], scripts
- Script task [Integration Services], about Script task
- scripts [Integration Services], about Script task with packages
- SSIS Script task, about Script task
ms.assetid: 911e6d26-a6fd-4fc3-a111-bf5f048e9bff
caps.latest.revision: 56
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5b4fa549a03fd7f74baf98aa7aa489323da7b1ce
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37254550"
---
# <a name="extending-the-package-with-the-script-task"></a>以指令碼工作擴充封裝
  指令碼工作會以 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# 所撰寫、並且在套件執行階段編譯並執行的自訂程式碼，來擴充 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 套件的執行階段功能。 當 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 所含的工作未完全滿足您的需求時，指令碼工作可簡化自訂執行階段工作的開發。 指令碼工作會為您撰寫所有必要的基礎結構程式碼，讓您專門著重在自訂處理所需的程式碼。  
  
 指令碼工作透過全域 `Dts` 物件與容器封裝互動，這個物件是公開在指令碼編寫環境中的 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> 類別之執行個體。 您可以在指令碼工作中撰寫程式碼，以修改儲存在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 變數的值；之後，封裝可以使用這些更新的值來決定其工作流程的路徑。 指令碼工作也可以使用 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 命名空間和 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 類別庫以及自訂組件，來實作自訂功能。  
  
 指令碼工作以及它為您產生的基礎結構程式碼，可大幅簡化開發自訂工作的程序。 不過，若要了解指令碼工作如何運作，閱讀[開發自訂工作](../../extending-packages-custom-objects/task/developing-a-custom-task.md)一節，以了解開發自訂工作所需的步驟，可能會非常有用。  
  
 如果您建立一個計劃在多個封裝中重複使用的工作，應該考慮開發自訂工作，而不要使用指令碼工作。 如需詳細資訊，請參閱[比較指令碼解決方案和自訂物件](../comparing-scripting-solutions-and-custom-objects.md)。  
  
## <a name="in-this-section"></a>本節內容  
 下列主題提供有關指令碼工作的詳細資訊。  
  
 [在指令碼工作編輯器設定指令碼工作](configuring-the-script-task-in-the-script-task-editor.md)  
 說明在**指令碼工作編輯器**中設定的屬性如何影響指令碼工作中程式碼的功能與效能。  
  
 [編碼和偵錯指令碼工作](../../control-flow/script-task.md)  
 說明如何使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) 以開發包含在指令碼工作中的指令碼。  
  
 [在指令碼工作中使用變數](using-variables-in-the-script-task.md)  
 說明如何透過 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 屬性使用變數。  
  
 [在指令碼工作中連線至資料來源](connecting-to-data-sources-in-the-script-task.md)  
 說明如何透過 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> 屬性使用連接。  
  
 [在指令碼工作中引發事件](raising-events-in-the-script-task.md)  
 說明如何透過 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> 屬性引發事件。  
  
 [在指令碼工作中記錄](logging-in-the-script-task.md)  
 說明如何透過 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> 方法記錄資訊。  
  
 [從指令碼工作傳回結果](returning-results-from-the-script-task.md)  
 說明如何透過 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> 屬性與 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> 屬性傳回結果。  
  
 [指令碼工作範例](../../extending-packages-scripting-task-examples/script-task-examples.md)  
 提供簡單的範例，以示範指令碼工作的幾個可能用途。  
  
![Integration Services 圖示 （小）](../../media/dts-16.gif "Integration Services 圖示 （小）")**保持最多包含 Integration Services 的日期  **<br /> 最新下載、 文章、 範例和影片[!INCLUDE[msCoName](../../../includes/msconame-md.md)]，以及選取的解決方案，從社群，請瀏覽[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]MSDN 上的頁面：<br /><br /> [瀏覽 MSDN 上的 Integration Services 頁面](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> 若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。  
  
## <a name="see-also"></a>另請參閱  
 [指令碼工作](../../control-flow/script-task.md)   
 [比較指令碼工作和指令碼元件](../../extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
  
  