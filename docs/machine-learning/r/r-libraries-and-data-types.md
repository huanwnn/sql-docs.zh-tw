---
title: 轉換 R 與 SQL 資料類型
description: 檢閱資料科學與機器學習解決方案中 R 與 SQL Server 之間的隱含與明確資料類型轉換。
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/08/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1f7a6a95033d16e7bc39f07d6b72324e3aea6634
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81486717"
---
# <a name="data-type-mappings-between-r-and-sql-server"></a>R 與 SQL Server 之間的資料類型對應
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

針對在 SQL Server 機器學服服務 R 整合功能上執行的 R 解決方案，請檢閱不支援的資料類型清單，以及當資料在 R 程式庫與 SQL Server 之間傳遞時，可能會隱含執行的資料類型轉換。

## <a name="base-r-version"></a>基底 R 版本

SQL Server 2016 R Services 與具有 R 的 SQL Server 機器學習服務，與特定的 Microsoft R Open 發行版本相符。 例如，最新版本的 SQL Server 機器學習服務是建置在 Microsoft R Open 3.3.3 之上。

若要檢視與特定 SQL Server 執行個體關聯的 R 版本，請開啟 **RGui**。 針對預設執行個體，路徑如下：`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64\`

此工具會載入基底 R 與其他程式庫。 在工作階段啟動時載入的每個套件，都會在通知中提供套件版本資訊。 

## <a name="r-and-sql-data-types"></a>R 與 SQL 資料類型

雖然 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援數十種資料類型，但 R 的純量資料類型 (數字、整數、複雜、邏輯、字元、日期/時間和原始) 數量有限。 因此，每當您在 R 指令碼中使用來自 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的資料時，資料可能會隱含地轉換為相容的資料類型。 不過，通常無法自動執行精確的轉換，而且會傳回錯誤，例如「未處理的 SQL 資料類型」。

此節列出所提供的隱含轉換，並列出不支援的資料類型。 針對在 R 與 SQL Server 之間對應資料類型，我們提供一些指導方針。

## <a name="implicit-data-type-conversions-between-r-and-sql-server"></a>R 與 SQL Server 之間的隱含資料類型轉換

下表顯示在 R 指令碼中使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的資料，然後傳回給 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]時，資料類型和值的變更。

|SQL 類型|R 類別|RESULT SET 類型|註解|
|-|-|-|-|
|**bigint**|`numeric`|**float**||
|**binary(n)**<br /><br /> n <= 8000|`raw`|**varbinary(max)**|只允許作為輸入參數和輸出|
|**bit**|`logical`|**bit**||
|**char(n)**<br /><br /> n <= 8000|`character`|**varchar(max)**||
|**datetime**|`POSIXct`|**datetime**|以 GMT 來表示|
|**date**|`POSIXct`|**datetime**|以 GMT 來表示|
|**decimal(p,s)**|`numeric`|**float**||
|**float**|`numeric`|**float**||
|**int**|`integer`|**int**||
|**money**|`numeric`|**float**||
|**numeric(p,s)**|`numeric`|**float**||
|**real**|`numeric`|**float**||
|**smalldatetime**|`POSIXct`|**datetime**|以 GMT 來表示|
|**smallint**|`integer`|**int**||
|**smallmoney**|`numeric`|**float**||
|**tinyint**|`integer`|**int**||
|**uniqueidentifier**|`character`|**varchar(max)**||
|**varbinary(n)**<br /><br /> n <= 8000|`raw`|**varbinary(max)**|只允許作為輸入參數和輸出|
|**varbinary(max)**|`raw`|**varbinary(max)**|只允許作為輸入參數和輸出|
|**varchar(n)**<br /><br /> n <= 8000|`character`|**varchar(max)**||


## <a name="data-types-not-supported-by-r"></a>R 不支援的資料類型

在 [SQL Server 類型系統](../../t-sql/data-types/data-types-transact-sql.md)所支援的資料類型類別中，以下幾個類型在傳遞到 R 程式碼時很有可能會造成問題：

+ 列在 SQL 類型系統文章中＜其他＞  一節的資料類型：**cursor**、**timestamp**、**hierarchyid**、**uniqueidentifier**、**sql_variant**、**xml**、**table**
+ 所有空間類型
+ **image**

## <a name="data-types-that-might-convert-poorly"></a>轉換效果可能不佳的資料類型

+ 除了 **datetimeoffset** 之外，大部分的 datetime 類型應該都能順利運作 
+ 支援大部分的數值資料類型，但 **money** 和 **smallmoney** 的轉換可能會失敗
+ 支援 **varchar**，但由於 SQL Server 一般使用 Unicode，因此建議您盡可能使用 **nvarchar** 及其他 Unicode 文字資料類型。
+ 來自 RevoScaleR 函數庫且具有 rx 前置詞的函數，可以處理 SQL 二進位資料類型 (**binary** 和 **varbinary**)，但在大部分案例中，這些類型都需要特別處理。 大部分的 R 程式碼都無法搭配二進位資料行使用。

  
 如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型的詳細資訊，請參閱[資料類型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)

## <a name="changes-in-data-types-between-sql-server-2016-and-earlier-versions"></a>SQL Server 2016 與舊版之間的資料類型變更

Microsoft SQL Server 2016 和更新版本包含資料類型轉換和幾個其他作業的改進。 這些改進大部分都為處理浮點數類型提供更高的精確度，以及對傳統 **datetime** 類型的作業做出次要變更。

當您使用 130 或更高的資料庫相容性層級時，這些改進預設都可供使用。 不過，如果您使用不同的相容性層級，或使用較舊版本連線到資料庫，則可能會看見不同的數值精確度或其他結果。 

如需詳細資訊，請參閱[處理某些資料類型和不常見作業的 SQL Server 2016 改進 (機器翻譯)](https://support.microsoft.com/help/4010261/sql-server-2016-improvements-in-handling-some-data-types-and-uncommon-)。
 

## <a name="verify-r-and-sql-data-schemas-in-advance"></a>預先驗證 R 和 SQL 資料結構描述 

一般而言，當您不清楚如何在 R 中使用特定的資料類型或資料結構時，皆可使用  `str()` 函數以取得 R 物件的內部結構和類型。 函數的結果會列印到 R 主控台，也會顯示在 **的 [訊息]** [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]索引標籤查詢結果中。 

當您從資料庫擷取要用於 R 程式碼的資料時，應該一律刪除無法用於 R 的資料行，以及其他對於分析沒有幫助的資料行，例如 GUIDS (Uniqueidentifier)、時間戳記和其他用於稽核的資料行，或是由 ETL 處理序建立的譜系資訊。 

請注意，包含不必要的資料行可能會大幅降低 R 程式碼的效能，尤其是使用高基數資料行做為因素的時候。 因此，我們建議您事先使用 SQL Server 系統預存程序和資訊檢視取得特定資料表的資料類型，並刪除或轉換不相容的資料行。 如需詳細資訊，請參閱 [Transact-SQL 中的資訊結構描述檢視](../../relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)

如果 R 不支援特定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型，但您需要在 R 指令碼中使用該資料的數個資料行，建議您先使用 [CAST 和 CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md) 函數，以確保資料類型轉換會如預期般地執行，再於 R 指令碼中使用該資料。  

> [!WARNING]
> 如果您在移動資料時使用 **rxDataStep** 來卸除不相容的資料行，請留意 **RxSqlServerData** 資料來源類型不支援引數 _varsToKeep_ 和 _varsToDrop_。


## <a name="examples"></a>範例

### <a name="example-1-implicit-conversion"></a>範例 1：隱含轉換

以下範例示範資料在 SQL Server 和 R 之間進行來回行程時的轉換方式。

查詢會從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表取得一系列的值，並使用預存程序 [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) 來使用 R 執行階段輸出值。

```sql
CREATE TABLE MyTable (    
 c1 int,    
 c2 varchar(10),    
 c3 uniqueidentifier    
);    
go    
INSERT MyTable VALUES(1, 'Hello', newid());    
INSERT MyTable VALUES(-11, 'world', newid());    
SELECT * FROM MyTable;    
  
EXECUTE sp_execute_external_script    
 @language = N'R'    
 , @script = N'    
inputDataSet["cR"] <- c(4, 2)    
str(inputDataSet)    
outputDataSet <- inputDataSet'    
 , @input_data_1 = N'SELECT c1, c2, c3 FROM MyTable'    
 , @input_data_1_name = N'inputDataSet'    
 , @output_data_1_name = N'outputDataSet'    
 WITH RESULT SETS((C1 int, C2 varchar(max), C3 varchar(max), C4 float));  
```

**結果**

||||||
|-|-|-|-|-|
||C1|C2|C3|C4|
|1|1|您好|6e225611-4b58-4995-a0a5-554d19012ef1|4|
|1|-11|world|6732ea46-2d5d-430b-8ao1-86e7f3351c3e|2|

請注意，在 R 中使用 `str` 函數可取得輸出資料的結構描述。 此函數傳回下列資訊：

<code>'data.frame':2 obs. of  4 variables:</code>
<code> $ c1: int  1 -11</code>
<code> $ c2: Factor w/ 2 levels "Hello","world": 1 2</code>
<code> $ c3: Factor w/ 2 levels "6732EA46-2D5D-430B-8A01-86E7F3351C3E",..: 2 1</code>
<code> $ cR: num  4 2</code>

從這裡開始，您可以看到下列資料類型轉換會與這項查詢一起以隱含方式執行：

-   **資料行 C1**。 資料行在 **ssNoversion** 中會表示為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，在 R 中會表示為 `integer` 而在輸出結果集中則為 **ssNoversion** 。  
  
     未執行任何類型轉換。  
  
-   **資料行 C2**。 資料行在 **ssNoversion** 中會表示為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，在 R 中會表示為 `factor` 而在輸出結果集中則為 **varchar(max)** 。  
  
     請注意輸出的變更方式；來自 R 的任何字串 (因素或一般字串) 不管字串的長度為何，皆會以 **varchar(max)** 表示。  
  
-   **資料行 C3**。  資料行在 **ssNoversion** 中會表示為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，在 R 中會表示為 `character` 而在輸出結果集中則為 **varchar(max)** 。
  
     請注意所發生的資料類型轉換。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援 **ssNoversion** ，但 R 則否，因此識別項會表示為字串。
  
-   **資料行 C4**。 資料行包含由 R 指令碼產生且不存在於原始資料的值。


## <a name="example-2-dynamic-column-selection-using-r"></a>範例 2：使用 R 進行動態資料行選取

以下範例示範如何使用 R 程式碼來檢查無效的資料行類型。 程式碼會使用 SQL Server 系統檢視來取得指定資料表的結構描述，並移除任何具有指定無效類型的資料行。

```R
connStr <- "Server=.;Database=TestDB;Trusted_Connection=Yes"
data <- RxSqlServerData(connectionString = connStr, sqlQuery = "SELECT COLUMN_NAME FROM TestDB.INFORMATION_SCHEMA.COLUMNS WHERE TABLE_NAME = N'testdata' AND DATA_TYPE <> 'image';")
columns <- rxImport(data)
columnList <- do.call(paste, c(as.list(columns$COLUMN_NAME), sep = ","))
sqlQuery <- paste("SELECT", columnList, "FROM testdata")
```

## <a name="see-also"></a>另請參閱

