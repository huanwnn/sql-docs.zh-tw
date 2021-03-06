---
title: 專案設定（遷移）（MySQLToSQL） |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 2a3cba9e-cd54-4a8b-b858-8fc4cf2580d9
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 2f3c989626f36c003937723869b5e17d1a405ea9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2020
ms.locfileid: "67908860"
---
# <a name="project-settings-migration-mysqltosql"></a>專案設定 (移轉) (MySQLToSQL)
[**專案設定**] 對話方塊的 [遷移] 頁面包含的設定，可自訂 SSMA 將資料從 MySQL 遷移至 SQL Server 的方式。  
  
[**專案設定**] 和 [**預設專案設定**] 對話方塊中會提供 [遷移] 窗格。  
  
-   若要指定所有 SSMA 專案的設定，請在 [**工具**] 功能表上，選取 [**預設專案設定**]，在您想要存取設定的 [**遷移目標版本**] 下拉式集中選取專案類型，按一下左窗格底部的 **[一般**]，然後按一下 [**遷移**]。  
  
-   若要指定目前專案的設定，請在 [**工具**] 功能表上，選取 [**專案設定**]，按一下左窗格底部的 **[一般**]，然後按一下 [**遷移**]。  
  
## <a name="options"></a>選項。  
  
### <a name="bulk-copy"></a>大量複製  
  
|詞彙|定義|  
|--------|--------------|  
|**批次大小**|指定資料移轉期間使用的批次大小。<br /><br />**預設模式**：1000<br /><br />**開放式模式**：1000<br /><br />**完整模式**：1000|  
|**檢查條件約束**|指定當 SSMA 將資料插入 SQL Server 資料表時，是否應檢查條件約束。<br /><br />**預設模式**： False<br /><br />**開放式模式**： False<br /><br />**完整模式**： False|  
|**引發觸發程序**|指定 SSMA 是否應該在將資料加入 SQL Server 資料表時，引發插入觸發程式。<br /><br />**預設模式**： False<br /><br />**開放式模式**： False<br /><br />**完整模式**： False|  
|**保留識別**|指定 SSMA 將資料新增至 SQL Server 時，是否保留 MySQL 身分識別值。 值為 False 會導致目的地指派識別值。<br /><br />**預設模式**： True<br /><br />**開放式模式**： True<br /><br />**完整模式**： True|  
|**保留 Null**|指定 SSMA 將資料新增至 SQL Server 時，是否在來源資料中保留 null 值，而不論 SQL Server 中指定的預設值為何。<br /><br />**預設模式**： True<br /><br />**開放式模式**： True<br /><br />**完整模式**： True|  
|**表鎖**|指定 SSMA 是否會在資料移轉期間將資料加入資料表時，鎖定資料表。 取得大量複製作業期間的大量更新鎖定。 如果值為 False，就會在資料列層級設定鎖定。<br /><br />**預設模式**： False<br /><br />**開放式模式**： False<br /><br />**完整模式**： False|  
  
### <a name="data-modification"></a>資料修改  
  
|詞彙|定義|  
|--------|--------------|  
|**不正確日期遷移**|指定如何以日期和日期時間格式，以類似 ' 2007-04-23 ' 或 ' 2000-06-31 10:00:00 ' 的方式遷移不正確日期。<br /><br />**預設模式**：設定 Null<br /><br />**開放式模式**：設定 Null<br /><br />**Full 模式**：設定 Null|  
|**負值時間值遷移**|指定如何在時間資料行中遷移負數值，例如 '-30:11:00 '。<br /><br />**預設模式**：設定 Null<br /><br />**開放式模式**：設定 Null<br /><br />**Full 模式**：設定 Null|  
|**超過24小時的時間值遷移**|指定如何在時間資料行中遷移大於 ' 23:59:59 ' 的時間值。<br /><br />**預設模式**：設定 Null<br /><br />**開放式模式**：設定 Null<br /><br />**Full 模式**：設定 Null|  
|**截斷二進位值以符合資料行**|如果是，SSMA 會從不符合 SQL 資料表資料行的 MySQL 中截斷二進位值，並產生適當的錯誤訊息。 如果否，資料列會造成錯誤<br /><br />**預設模式**：否<br /><br />**開放式模式**：否<br /><br />**完整模式**：否|  
|**截斷字元值以符合資料行**|SSMA 會從 MySQL 截斷不符合 SQL 資料表資料行的字元值，並產生適當的錯誤訊息。<br /><br />**預設模式**：否<br /><br />**開放式模式**：否<br /><br />**完整模式**：否|  
|**零日期遷移**|指定如何在日期和日期時間資料行中遷移零個日期，例如 ' 0000-00-00 ' 或 ' 0000-00-00 00:00:00 '。<br /><br />**預設模式**：設定 Null<br /><br />**開放式模式**：設定 Null<br /><br />**Full 模式**：設定 Null|  
|**在日期遷移中為零**|指定如何在日期和日期時間資料行中遷移零部分的日期，例如 ' 2009-01-00 ' 或 ' 2000-00-00 11:00:00 '。<br /><br />**預設模式**：設定 Null<br /><br />**開放式模式**：設定 Null<br /><br />**Full 模式**：設定 Null|  
  
### <a name="migration-engine"></a>遷移引擎  
  
|詞彙|定義|  
|--------|--------------|  
|**遷移引擎**|指定資料移轉期間所使用的資料庫引擎。 用戶端資料移轉指的是 SSMA 用戶端從來源抓取資料，並將該資料大量插入 SQL Server。 伺服器端資料移轉指的是在 SQL Server box 上執行的 SSMA 資料移轉引擎（大量複製程式），作為 SQL 代理程式作業，從來源抓取資料並直接插入 SQL Server，因此可避免額外的用戶端躍點（較佳的效能）。<br /><br />**預設模式**：用戶端資料移轉引擎<br /><br />**開放式模式**：用戶端資料移轉引擎<br /><br />**完整模式**：用戶端資料移轉引擎|  
  
> [!IMPORTANT]  
> 當 [**遷移引擎**] 選項設定為 [**伺服器端資料移轉引擎**] 時，會顯示新的專案設定選項 [**使用32位伺服器端資料移轉引擎**]。 它會指定是否使用32位或64位大量複製程式（BCP）公用程式來遷移資料。  
  
### <a name="misc"></a>其他  
  
|詞彙|定義|  
|--------|--------------|  
|**擴充資料移轉選項**|在個別的 [詳細資料] 索引標籤中顯示每個資料表的額外資料移轉選項。<br /><br />**預設模式**：隱藏<br /><br />**開放式模式**：隱藏<br /><br />**完整模式**：隱藏|  
|**發生錯誤時**|發生錯誤時停止資料移轉。 它有三個選項：<br /><br />**停止遷移：** 停止資料移轉作業<br /><br />**繼續進行下一個資料表：** 停止對目前資料表的資料移轉，並繼續進行下一個工作<br /><br />**繼續進行下一個批次：** 停止對目前批次的資料移轉，並繼續進行下一個<br /><br />**預設模式**：繼續進行下一個批次<br /><br />**開放式模式**：繼續進行下一個批次<br /><br />**完整模式**：繼續進行下一個批次|  
  
### <a name="parallel-data-migration"></a>平行資料移轉  
  
|詞彙|定義|  
|--------|--------------|  
|**平行資料移轉模式**|指定用來分叉執行緒以啟用平行資料移轉的模式。 在 Auto 模式中，SSMA 會選擇分叉的執行緒數目（預設為10），以遷移資料。 在自訂模式中，使用者可以指定分叉到遷移資料的執行緒數目（最小值為1，最大值為100）。 目前，只有用戶端資料移轉引擎支援平行資料移轉。<br /><br />**預設模式**：自動<br /><br />**開放式模式**：自動<br /><br />**完整模式**：自動|  
  
> [!IMPORTANT]  
> 當 [**平行資料移轉模式]** 選項設定為 [**自訂**] 時，會顯示新的專案設定選項 [**執行緒計數**]。 它會指定用於資料移轉的執行緒數目。  
  
### <a name="spatial-data"></a>空間資料  
  
|詞彙|定義|  
|--------|--------------|  
|**處理錯誤**|指定如何在遷移空間資料類型的值時處理錯誤。 如果指定了 ' Replace with Null '，則造成錯誤的所有空間值都會以 Null 取代。 否則，不會進行取代。<br /><br />**預設模式**：產生錯誤<br /><br />**開放式模式**：產生錯誤<br /><br />**完整模式**：產生錯誤|  
|**值驗證**|指定如何處理不正確空間值。 如果指定了 [Try Valid]，則會嘗試修改不正確值，使其生效。<br /><br />**預設模式**：設為有效<br /><br />**開放式模式**：不變更<br /><br />**完整模式**：設為有效|  
  
