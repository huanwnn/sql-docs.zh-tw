---
title: 快速入門：執行 Python 指令碼
description: 使用 SQL Server 機器學習服務執行一組簡單的 Python 指令碼。 了解如何使用預存程序 sp_execute_external_script 在 SQL Server 執行個體中執行指令碼。
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/17/2020
ms.topic: quickstart
author: cawrites
ms.author: chadam
ms.reviewer: garye
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6b15423d82a13485d343dc797bdf6e6efe25088f
ms.sourcegitcommit: dc965772bd4dbf8dd8372a846c67028e277ce57e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83606440"
---
# <a name="quickstart-run-simple-python-scripts-with-sql-server-machine-learning-services"></a>快速入門：使用 SQL Server 機器學習服務，執行簡單的 Python 指令碼
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
在此快速入門中，您將會使用 [SQL Server 機器學習服務](../sql-server-machine-learning-services.md)或在[巨量資料叢集](../../big-data-cluster/machine-learning-services.md)上執行一組簡單的 Python 指令碼。 您將會了解如何使用預存程序 [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) 在 SQL Server 執行個體中執行指令碼。
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
在此快速入門中，您將會使用 [SQL Server 機器學習服務](../sql-server-machine-learning-services.md)來執行一組簡單的 Python 指令碼。 您將會了解如何使用預存程序 [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) 在 SQL Server 執行個體中執行指令碼。
::: moniker-end

## <a name="prerequisites"></a>Prerequisites


::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
- SQL Server 機器學習服務。 如需如何安裝機器學習服務的相關資訊，請參閱 [Windows 安裝指南](../install/sql-machine-learning-services-windows-install.md)或 [Linux 安裝指南](../../linux/sql-server-linux-setup-machine-learning.md?toc=%2Fsql%2Fmachine-learning%2Ftoc.json)。 您也可以[啟用 SQL Server 巨量資料叢集上的機器學習服務](../../big-data-cluster/machine-learning-services.md)。
::: moniker-end

::: moniker range=">=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions"
- SQL Server 機器學習服務。 如需如何安裝機器學習服務的相關資訊，請參閱 [Windows 安裝指南](../install/sql-machine-learning-services-windows-install.md)或 [Linux 安裝指南](../../linux/sql-server-linux-setup-machine-learning.md?toc=%2Fsql%2Fmachine-learning%2Ftoc.json)。 您也可以[啟用 SQL Server 巨量資料叢集上的機器學習服務](../../big-data-cluster/machine-learning-services.md)。
::: moniker-end

- 您也需要工具來執行包含 Python 指令碼的 SQL 查詢。 您可以使用任何資料庫管理或查詢工具來執行這些指令碼，只要該工具可以連線到 SQL Server 執行個體，並執行 T-SQL 查詢或預存程序即可。 本快速入門使用 [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download-azure-data-studio)。

## <a name="run-a-simple-script"></a>執行簡單的指令碼

若要執行 Python 指令碼，請將它當做引數傳遞至系統預存程式，[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)。
這個系統預存程序會在 SQL Server 內容中啟動 Python 執行階段、將資料傳遞到 Python，安全地管理 Python 使用者工作階段，並將任何結果傳回用戶端。

在下列步驟中，您將在 SQL Server 執行個體中執行此範例 Python 指令碼：

```python
a = 1
b = 2
c = a/b
d = a*b
print(c, d)
```

1. 以連接至您 SQL Server 執行個體的 **Azure Data Studio** 開啟新的查詢視窗。

1. 將完整的 Python 指令碼傳遞至 `sp_execute_external_script` 預存程序。

   指令碼會透過 `@script` 引數傳遞。 `@script` 引數內的所有一切都必須是有效的 Python 程式碼。

    ```sql
    EXECUTE sp_execute_external_script @language = N'Python'
        , @script = N'
    a = 1
    b = 2
    c = a/b
    d = a*b
    print(c, d)
    '
    ```

1. 系統會計算正確的結果，且 Python `print` 函數會將結果傳回至 [訊息] 視窗。

   其外觀應該如下所示。

    **結果**

    ```text
    STDOUT message(s) from external script:
    0.5 2
    ```

## <a name="run-a-hello-world-script"></a>執行 Hello World 指令碼

典型的範例指令碼只會輸出字串 "Hello World"。 執行下列命令。

```sql
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'OutputDataSet = InputDataSet'
    , @input_data_1 = N'SELECT 1 AS hello'
WITH RESULT SETS(([Hello World] INT));
GO
```

`sp_execute_external_script` 預存程序的輸入包括：

| | |
|-|-|
| @language | 定義要呼叫的語言擴充功能，在本例中為 Python |
| @script | 定義要傳遞至 Python 執行階段的命令<br>您的整個 Python 指令碼必須以 Unicode 文字的格式包含在此引數中。 您也可以將文字新增至 **Nvarchar** 類型的變數，並呼叫該變數 |
| @input_data_1 | 查詢所傳回的資料會傳遞到 Python 執行階段，其會以資料框架的格式傳回資料 |
|使用結果集 | 子句會定義 SQL Server 傳回資料表的結構描述，然後加入 "Hello World" 做為資料行名稱，並將 **int** 用於資料類型 |


此命令會輸出下列文字：

| Hello World |
|-------------|
| 1 |

## <a name="use-inputs-and-outputs"></a>使用者輸入和輸出

在預設情況下，`sp_execute_external_script` 會接受單一資料集做為輸入，這通常由您以有效的 SQL 查詢形式提供。 然後，它會傳回單一 Python 資料框架做為輸出。

現在，讓我們使用 `sp_execute_external_script` 的預設輸入和輸出變數：**InputDataSet** 和 **OutputDataSet**。

1. 建立測試資料的小型資料表。

    ```sql
    CREATE TABLE PythonTestData (col1 INT NOT NULL)
    
    INSERT INTO PythonTestData
    VALUES (1);
    
    INSERT INTO PythonTestData
    VALUES (10);
    
    INSERT INTO PythonTestData
    VALUES (100);
    GO
    ```

1. 使用 `SELECT` 陳述式查詢資料表。
  
    ```sql
    SELECT *
    FROM PythonTestData
    ```

    **結果**

    ![PythonTestData 資料表的內容](./media/select-pythontestdata.png)

1. 請執行下列 Python 指令碼。 它會使用 `SELECT` 陳述式來擷取資料表中的資料、透過 Python 執行階段傳遞，然後傳回資料做為資料框架。 `WITH RESULT SETS` 子句會為 SQL 定義傳回資料表的結構描述，新增資料行名稱 *NewColName*。

    ```sql
    EXECUTE sp_execute_external_script @language = N'Python'
        , @script = N'OutputDataSet = InputDataSet;'
        , @input_data_1 = N'SELECT * FROM PythonTestData;'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    **結果**

    ![從資料表傳回資料的 Python 指令碼輸出](./media/python-output-pythontestdata.png)

1. 現在變更輸入和輸出變數的名稱。 預設的輸入和輸出變數名稱是 **InputDataSet** 和 **OutputDataSet**，以下指令碼會將名稱變更為 **SQL_in** 和 **SQL_out**：

    ```sql
    EXECUTE sp_execute_external_script @language = N'Python'
        , @script = N'SQL_out = SQL_in;'
        , @input_data_1 = N'SELECT 12 as Col;'
        , @input_data_1_name  = N'SQL_in'
        , @output_data_1_name = N'SQL_out'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    請注意，Python 區分大小寫。 Python 指令碼 (**SQL_out** **SQL_in**) 中所使用的輸入和輸出變數必須比對以 `@input_data_1_name` 和 `@output_data_1_name` 定義的名稱，包括大小寫。

   > [!TIP]
   > 只有一個輸入資料集可以傳入作為參數，而且您只能傳回一個資料集。 不過，您可以從 Python 程式碼內部呼叫其他資料集，而且除了資料集之外，您還可以傳回其他類型的輸出。 您也可以為任何參數加上 OUTPUT 關鍵字，使其與結果一起傳回。

1. 您也可以在無輸入資料的情況下 (`@input_data_1` 設為空白)，只使用 Python 指令碼產生值。

   下列指令碼輸出文字 "hello" 和 "world"。

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   import pandas as pd
   mytextvariable = pandas.Series(["hello", " ", "world"]);
   OutputDataSet = pd.DataFrame(mytextvariable);
   '
       , @input_data_1 = N''
   WITH RESULT SETS(([Col1] CHAR(20) NOT NULL));
   ```

   **結果**

   ![使用 @script 做為輸入查詢結果](./media/python-data-generated-output.png)

> [!NOTE]
> Python 使用前置空格將陳述式分組。 因此當內嵌的 Python 指令碼跨越多行時 (如上述指令碼所示)，請勿嘗試將 Python 命令縮排以與 SQL 命令對齊。 例如，此指令碼將產生錯誤：

  ```text
  EXECUTE sp_execute_external_script @language = N'Python'
      , @script = N'
      import pandas as pd
      mytextvariable = pandas.Series(["hello", " ", "world"]);
      OutputDataSet = pd.DataFrame(mytextvariable);
      '
      , @input_data_1 = N''
  WITH RESULT SETS(([Col1] CHAR(20) NOT NULL));
  ```

## <a name="check-python-version"></a>檢查 Python 版本

如果您想要查看在 SQL Server 執行個體中所安裝的 Python 版本，請執行下列指令碼。

```sql
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import sys
print(sys.version)
'
GO
```

Python `print` 函數會將版本傳回到 [訊息] 視窗。 在下方的範例輸出中，您可以看到在此案例中安裝的是 Python 3.5.2 版。

**結果**

```text
STDOUT message(s) from external script: 
3.5.2 |Continuum Analytics, Inc.| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
```

## <a name="list-python-packages"></a>列出 Python 套件

Microsoft 提供一些透過 SQL Server 機器學習服務預先安裝在您 SQL Server 執行個體中的 Python 套件。

若要查看已安裝的 Python 套件清單 (包括版本)，請執行以下指令碼。

```SQL
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import pkg_resources
import pandas
dists = [str(d) for d in pkg_resources.working_set]
OutputDataSet = pandas.DataFrame(dists)
'
WITH RESULT SETS(([Package] NVARCHAR(max)))
GO
```

該清單是來自 Python 中的 `pkg_resources.working_set`，並以資料框架的形式傳回到 SQL。

**結果**

:::image type="content" source="media/python-package-list.png" alt-text="已安裝的 Python 套件清單":::

## <a name="next-steps"></a>後續步驟

若要了解如何在 SQL 機器學習中使用 Python 時使用資料結構，請遵循本快速入門：

> [!div class="nextstepaction"]
> [快速入門：在 SQL Server 機器學習服務中使用 Python 的資料結構和物件](quickstart-python-data-structures.md)

