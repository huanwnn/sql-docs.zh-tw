---
title: 重新命名 Analysis Services 實例 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- instances of Analysis Services, renaming
- renaming instances of Analysis Services
- names [Analysis Services], renaming instances
- names [Analysis Services]
ms.assetid: 87494741-4a2e-4fed-8061-418fd1e111c3
author: minewiskan
ms.author: owend
ms.openlocfilehash: f92fdd7ea01cb9a373bafc3357de65fd2e622add
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84543780"
---
# <a name="rename-an-analysis-services-instance"></a>重新命名 Analysis Services 執行個體
  您可以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 使用 [**重新命名實例**] 對話方塊來重新命名現有的實例。  
  
> [!IMPORTANT]  
>  重新命名執行個體時， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instance Rename Tool 會以更高的權限執行，並更新與該執行個體相關聯的 Windows 服務名稱、安全性帳戶，以及登錄項目。 為確保執行這些動作，請務必以本機系統管理員身分執行此工具。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instance Rename Tool 不會修改針對原始執行個體建立的程式資料夾。 請勿修改程式資料夾名稱以符合您要重命名的執行個體。 變更程式資料夾名稱可以防止安裝程式修復或移除安裝。  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體重新命名工具不適用於叢集環境。  
  
### <a name="to-rename-an-instance-of-analysis-services"></a>若要重新命名 Analysis Services 的執行個體  
  
1.  從 C:\Program Files\Microsoft SQL Server\110\tools\binn\managementstudio 啟動**實例重新命名**工具， **asinstancerename.exe**  
  
2.  在 [重新命名執行個體]**** 對話方塊的 [要重新命名的執行個體]**** 清單中，選取您要重新命名的執行個體。  
  
3.  在 [新執行個體名稱]**** 方塊中，輸入執行個體的新名稱。  
  
4.  確認使用者名稱和密碼正確，然後按一下 [重新命名]****。  
  
     Analysis Services 執行個體將會停止，並在名稱變更時重新啟動。  
  
### <a name="post-rename-checklist"></a>重新命名後的清單  
  
1.  若要繼續存取在重新命名之執行個體上執行的資料庫，您必須在 Excel 或其他用戶端應用程式中手動更新資料連接。 此外，請檢查任何預先定義的連接，例如 Reporting Services 共用資料來源、Excel ODC 檔，或可能參考您剛重新命名之執行個體 BI 語意模型連接檔案。 如需相關資訊，請參閱 [連接到 Analysis Services](connect-to-analysis-services.md)。  
  
2.  更新您例行用來備份、同步處理或處理資料庫的 PowerShell 指令碼或 AMO 指令碼。  
  
3.  更新您在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中處理之 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]專案的專案屬性。 針對表格式模式伺服器執行個體，請務必更新 model.bim 檔案的 [工作空間伺服器] 屬性，以及專案的 [伺服器] 屬性。  
  
4.  根據您指定服務帳戶的方式而定，您可能需要更新授與資料存取權限給服務的資料庫登入或檔案權限 (例如，如果您使用服務帳戶處理資料或存取其他伺服器上的連結物件)。  
  
     如果您使用虛擬帳戶佈建服務，將需要更新資料庫登入或檔案權限。 虛擬帳戶是以執行個體名稱為基礎，因此，如果您重新命名執行個體，同時也會更新虛擬帳戶。 也就是說，您針對先前的執行個體所建立的任何先前登入或權限都不再有效。  
  
     下列範例提供說明。 假設您使用預設虛擬帳戶，將表格式模式伺服器安裝為名為 "表格式" 的實例，則會產生下列設定：  
  
    1.  實例名稱 = \<server> \TABULAR  
  
    2.  服務名稱 = MSOLAP$TABULAR  
  
    3.  虛擬帳戶 = NT Service\ MSOLAP$TABULAR  
  
     現在假設您將實例重新命名為 "TAB2"。 名稱變更之後，您的設定現在看起來如下：  
  
    1.  實例名稱 = \<server> \TAB2  
  
    2.  服務名稱 = MSOLAP$TAB2  
  
    3.  虛擬帳戶 = NT Service\ MSOLAP$TAB2  
  
     如您所見，先前授與 "NT Service \ MSOLAP $ 表格式" 的資料庫和檔案許可權已不再有效。 若要確保服務所執行的工作和作業如之前一樣執行，您現在需要將新的資料庫和檔案許可權授與 "NT Service \ MSOLAP $ TAB2"。  
  
  
