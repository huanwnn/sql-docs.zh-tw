---
title: Python 教學課程：分類客戶
titleSuffix: SQL machine learning
description: 在本教學課程系列中 (總共四個部分)，您將會使用 Python 搭配 SQL 機器學習，在資料庫中使用 K-Means 來叢集客戶。
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 04/15/2020
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8b3be490a6da01d34f8c762bf9c6cae1a35dbe40
ms.sourcegitcommit: dc965772bd4dbf8dd8372a846c67028e277ce57e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83606540"
---
# <a name="python-tutorial-categorizing-customers-using-k-means-clustering-with-sql-machine-learning"></a>Python 教學課程：使用 K-Means 叢集搭配 SQL Server 機器學習來分類客戶

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
在本教學課程系列中 (總共四個部分)，您將使用 Python，在 [SQL Server 機器學習服務](../sql-server-machine-learning-services.md)中或在[巨量資料叢集](../../big-data-cluster/machine-learning-services.md)上開發和部署 K-Means叢集模型，以分類客戶資料。
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
在本教學課程系列中 (總共四個部分)，您將使用 Python 在 [SQL Server 機器學習服務](../sql-server-machine-learning-services.md)中開和部署 K-Means叢集模型，以叢集客戶資料。
::: moniker-end

在此系列的第一部分中，您將設定本教學課程的必要條件，然後將範例資料集還原至資料庫。 在本系列稍後，您將使用此資料搭配 SQL 機器學習，在 Python 中定型和部署叢集模型。

在本系列的第二部分和第三部分中，您將在 Azure Data Studio 筆記本中開發一些 Python 指令碼來分析和準備您的資料，並將機器學習模型定型。 接著在第四部分中，您將使用預存程序在資料庫內執行這些 Python 指令碼。

*叢集*可以解釋成將資料組織成群組，而群組的成員在某些方面是相似的。 在本教學課程系列中，假設您有一家零售公司。 您將使用 **K-Means** 演算法在產品購買和退貨資料集中，執行客戶叢集。 透過將客戶叢集，您可以鎖定特定群組，以更有效率地專注於行銷工作。 K-Means 叢集是*非監督式學習*演算法，會根據相似性找出資料中的模式。

在本文中，您將學會如何：

> [!div class="checklist"]
> * 還原範例資料庫

在[第二部分](python-clustering-model-prepare-data.md)，您將了解如何準備資料庫中的資料，以執行叢集。

在[第三部分](python-clustering-model-build.md)，您將了解如何在 Python 中建立和定型 K-Means 叢集模型。

在[第四部分](python-clustering-model-deploy.md)，您將了解如何在資料庫中建立預存程序，以根據新的資料在 Python 中執行叢集。

## <a name="prerequisites"></a>Prerequisites

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
* [SQL Server 機器學習服務](../sql-server-machine-learning-services.md)與 Python 語言選項 - 請遵循 [Windows 安裝指南](../install/sql-machine-learning-services-windows-install.md)或 [Linux 安裝指南](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-machine-learning?toc=%2fsql%2fmachine-learning%2ftoc.json&view=sql-server-linux-ver15)中的安裝指示。 您也可以[啟用 SQL Server 巨量資料叢集上的機器學習服務](../../big-data-cluster/machine-learning-services.md)。
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
* [SQL Server 機器學習服務](../sql-server-machine-learning-services.md)與 Python 語言選項 - 請遵循 [Windows 安裝指南](../install/sql-machine-learning-services-windows-install.md)中的安裝指示。
::: moniker-end

* [Azure Data Studio](../../azure-data-studio/what-is.md)。 您會在 Azure Data Studio 中使用適用於 Python 與 SQL 的筆記本。 如需筆記本的詳細資訊，請參閱[如何在 Azure Data Studio 中使用筆記本](../../azure-data-studio/sql-notebooks.md)。

* 其他 Python 套件 - 本教學課程系列中範例所使用的 Python 套件您可能已安裝或尚未安裝。

  開啟 [命令提示字元] 並變更為您在 Azure Data Studio 中所使用 Python 版本的安裝路徑。 例如： `cd %LocalAppData%\Programs\Python\Python37-32` 。 然後執行下列命令，以安裝任何尚未安裝的套件。

  ```console
  pip install matplotlib
  pip install pandas
  pip install pyodbc
  pip install scipy
  pip install sklearn
  ```

## <a name="restore-the-sample-database"></a>還原範例資料庫

本教學課程中使用的範例資料集已儲存到 **.bak** 資料庫備份檔案中，供您下載和使用。 此資料集衍生自 [tpcx-bb](http://www.tpc.org/tpcx-bb/default.asp) 資料集 (由 [Transaction Processing Performance Council (TPC)](http://www.tpc.org/default.asp) 提供)。

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
> [!NOTE]
> 如果您是在巨量資料叢集上使用機器學習服務，請參閱如何[將資料庫還原至 SQL Server 巨量資料叢集主要執行個體](../../big-data-cluster/data-ingestion-restore-database.md)。
::: moniker-end

1. 下載 [tpcxbb_1gb.bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/tpcxbb_1gb.bak) 檔案。

1. 請遵循在 Azure Data Studio 中[從備份檔案還原資料庫](../../azure-data-studio/tutorial-backup-restore-sql-server.md#restore-a-database-from-a-backup-file)中的指示，使用下列詳細資料：

   * 從您下載的 **tpcxbb_1gb.bak** 檔案匯入
   * 將目標資料庫命名為 "tpcxbb_1gb"

1. 您可以藉由查詢 **dbo.customer** 資料表，確認資料集在還原資料庫後是否存在：

    ```sql
    USE tpcxbb_1gb;
    SELECT * FROM [dbo].[customer];
    ```

## <a name="clean-up-resources"></a>清除資源

如果您不打算繼續進行本教學課程，請刪除 tpcxbb_1gb 資料庫。

## <a name="next-steps"></a>後續步驟

在本教學課程系列的第一部分中，您已完成下列步驟：

* 還原範例資料庫

若要針對機器學習模型準備資料，請遵循本教學課程系列的第二部分進行：

> [!div class="nextstepaction"]
> [Python 教學課程：準備執行群集所需的資料](python-clustering-model-prepare-data.md)
