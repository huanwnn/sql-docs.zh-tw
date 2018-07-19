---
title: 資料行屬性 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdt.designers.properties.Column.ColumnIdentitySpec
- vdt.designers.properties.Column
- vdt.tablecolumn
- vdt.designers.properties.Column.ColumnComputedColumnSpec
- vdt.designers.properties.Column.ColumnFulltextSpec
ms.assetid: e549a2a8-4154-4ec8-b146-614564169b39
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1aed3d78cbc0f9ef44c15310e2ae9085226c3413
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37236178"
---
# <a name="column-properties-visual-database-tools"></a>資料行屬性 (Visual Database Tools)
  有兩個集合的資料行屬性：您可以在資料表設計工具的 [資料行屬性] 索引標籤中看到的完整集合 (僅適用於 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫)，以及使用伺服器總管可以在 [屬性] 視窗中看到的子集。  
  
> [!NOTE]  
>  此主題中的屬性，是依類別目錄的順序排列，而非依字母排列。  
  
> [!NOTE]  
>  您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更您的設定，請在 [工具] 功能表上選擇 [匯入和匯出設定]。  
  
## <a name="properties-window"></a>屬性視窗  
 當您在伺服器總管中選取資料行時，這些屬性會出現在 [屬性] 視窗中。  
  
> [!NOTE]  
>  這些屬性可使用 [伺服器總管] 來存取，而且都是唯讀的。 若要編輯 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的資料行屬性，請在 [資料表設計工具] 中選取資料行。 本主題稍後將描述這些屬性。  
  
 **識別類別目錄**  
 展開以顯示 [名稱] 和 [資料庫] 屬性。  
  
 **名稱**  
 顯示資料行的名稱。  
  
 **[資料庫備份]**  
 顯示選取的資料行之資料來源的名稱。 (僅適用於 OLE DB)。  
  
 **其他類別目錄**  
 展開以顯示其餘屬性。  
  
 **資料類型**  
 顯示選取之資料行的資料類型。 如需詳細資訊，請參閱[資料類型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)。  
  
 **識別值增量**  
 針對識別欄位之每個後續的資料列，顯示將加到 [識別值種子] 的遞增量。 (只適用於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])。  
  
 **識別種子**  
 顯示針對識別欄位，指派給資料表中之第一個資料列的種子值。 (只適用於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])。  
  
 **為識別**  
 顯示選取的資料行是否為資料表的識別欄位。 (只適用於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])。  
  
 **長度**  
 顯示以字元為基礎的資料類型所允許的字元數。  
  
 **可為 Null**  
 顯示資料行是否允許 Null 值。  
  
 **有效位數**  
 顯示數值資料類型所允許的最大位數數目。 這個屬性會顯示 **0** 來表示非數字的資料類型。  
  
 **小數位數**  
 若為數值資料類型，顯示可在小數點右邊顯示的最大位數數目。 這個值必須小於或等於有效位數。 這個屬性會顯示 **0** 來表示非數字的資料類型。  
  
## <a name="column-properties-tab"></a>資料行屬性索引標籤  
 若要存取這些屬性，請在伺服器總管中，以滑鼠右鍵按一下資料行所屬的資料表，選擇 [開啟資料表定義]，然後在資料表設計工具裡選取資料表方格中的資料列。  
  
> [!NOTE]  
>  這些屬性只適用於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
 **一般類別目錄**  
 展開以顯示 [名稱]、[允許 Null]、[資料類型]、[預設值或繫結]、[長度]、[有效位數] 和 [小數位數]。  
  
 **名稱**  
 顯示資料行的名稱。 若要編輯名稱，請在文字方塊中輸入。  
  
> [!CAUTION]  
>  如果現有的查詢、檢視、使用者自訂函數、預存程序或程式參考資料行，修改名稱就會使這些物件無效。  
  
 **允許 Null**  
 顯示資料行的資料類型是否允許 Null 值。  
  
 **資料類型**  
 顯示選取之資料行的資料類型。 若要編輯這個屬性，請按一下該屬性的值，並展開下拉式清單，然後選擇另一個值。 如需詳細資訊，請參閱[資料類型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)。  
  
 **預設值或繫結**  
 沒有為此資料行指定值時，顯示此資料行的預設值。 下拉式清單包含資料來源中所定義的所有全域預設值。 若要將資料行繫結到全域預設值，請從下拉式清單中選取。 此外，若要為資料行建立預設條件約束，請直接將預設值當作文字輸入。  
  
 **長度**  
 顯示以字元為基礎的資料類型所允許的字元數。 此屬性只適用於以字元為主的資料類型。  
  
 **有效位數**  
 顯示數值資料類型所允許的最大位數數目。 這個屬性會顯示 **0** 來表示非數字的資料類型。 此屬性僅適用於數值資料類型。  
  
 **小數位數**  
 若為數值資料類型，顯示可在小數點右邊顯示的最大位數數目。 這個值必須小於或等於有效位數。 這個屬性會顯示 **0** 來表示非數字的資料類型。 此屬性僅適用於數值資料類型。  
  
 **資料表設計工具類別目錄**  
 展開以顯示其餘屬性。  
  
 **定序**  
 顯示選取之資料行的定序設定。 若要變更此設定，請按一下 [定序]，然後按一下值右邊的省略符號 (**…**)。  
  
 **計算資料行規格類別目錄**  
 展開以顯示 [公式] 和 [為永續性] 的屬性。 如果資料行為計算的，則也會顯示公式。 若要編輯公式，請展開此類別目錄，並在 [公式] 屬性中編輯它。  
  
 **公式**  
 如果選取之資料行是計算的資料行，則顯示該資料行所使用的公式。 在此欄位中，您可以輸入或變更公式。  
  
 **為保存的**  
 允許您將計算的資料行與資料來源儲存在一起。 保存的計算資料行可以建立索引。  
  
 **資料類型扼要**  
 顯示欄位的資料類型資訊，使用與 SQL CREATE TABLE 陳述式相同的格式。 例如，包含可變長度字串 (最大長度為 20 個字元) 的欄位可表示為「varchar(20)」。 若要變更這個屬性，請直接輸入屬性值。  
  
 **說明**  
 顯示資料行的描述。 若要查看完整的描述，或要編輯它，請按一下 [描述]，然後按一下屬性右邊的省略符號 ( **…** )。  
  
 **全文檢索規格類別目錄**  
 展開以顯示全文檢索資料行特定的屬性。  
  
 **為全文檢索索引**  
 指出此資料行是否為全文檢索索引。 只有在此資料行的資料類型能以全文檢索搜尋，以及此資料行所屬的資料表具有為其指定的全文檢索索引時，才能將這個屬性設定為 [是]。 若要變更此值，請按一下它，展開下拉式清單，然後選擇新的值。  
  
 **全文檢索類型資料行**  
 顯示哪個資料行是用來定義影像類型資料行的文件類型。 影像資料類型可用來儲存從 .doc 檔至 xml 檔案的各種文件。  
  
 **語言**  
 指出用來建立資料行索引的語言。  
  
 **統計語意**  
 選取是否要針對選取的資料行啟用統計語意索引。 如需詳細資訊，請參閱[語意搜尋 &#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md)。  
  
 如果您在選取 **[統計語意]** 之前選取 **[語言]**，而且選取的語言沒有相關聯的語意語言模型，則 **[統計語意]** 選項會設定為 **[否]** ，而且無法修改。 如果您在選取 **[語言]** 之前針對 **[統計語意]** 選項選取 **[是]**，則 **[語言]** 欄中的可用語言將受限為有語意語言模型支援的語言。  
  
 **有非 SQL Server 訂閱者**  
 顯示資料行是否具有非 Microsoft SQL Server 訂閱者。  
  
 **識別規格類別目錄**  
 展開以顯示 [為識別]、[識別值增量] 和 [識別種子] 的屬性。  
  
 **為識別**  
 顯示選取的資料行是否為資料表的識別欄位。 若要變更屬性，請在資料表設計工具中開啟資料表，並在 [屬性] 視窗中編輯屬性。 此設定僅適用於以數值為基礎之資料類型的資料行，例如 *int*。  
  
 **識別值增量**  
 針對每個後續的資料列，顯示將加到 [識別種子] 的遞增量。 如果將這個資料格保留空白，則預設會指派值 1。 若要編輯這個屬性，請直接輸入新值。  
  
 **識別種子**  
 顯示指派至資料表之中第一個資料列的值。 如果將這個資料格保留空白，則預設會指派值 1。 若要編輯這個屬性，請直接輸入新值。  
  
 **為決定性的**  
 顯示是否可以確定地決定選取之資料行的資料類型。  
  
 **為以 DTS 發行**  
 顯示資料行是否為以 DTS 發行。  
  
 **為可編索引**  
 顯示選取的資料行是否可以建立索引。 例如，不具決定性之計算的資料行不可以建立索引。  
  
 **為合併發行**  
 顯示資料行是否為合併發行。  
  
 **為不可複寫**  
 指出在複寫期間是否保留原始識別值。 若要編輯這個屬性，請按一下該屬性的值，並展開下拉式清單，然後選擇另一個值。  
  
 **為已複寫**  
 顯示此資料行是否在其他位置已複寫。  
  
 **為 RowGuid**  
 指出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是否會使用資料行當做 ROWGUID。 您可以將此值設定為 **[是]** 只會針對具有的資料類型的資料行`uniqueidentifier`。 若要編輯這個屬性，請按一下該屬性的值，並展開下拉式清單，然後選擇另一個值。  
  
 **大小**  
 以位元組為單位，顯示資料行之資料類型所允許的大小。 例如，`nchar` 資料類型的長度可能是 10 (字元數)，但是針對 Unicode 字元集，大小就會是 20。  
  
> [!NOTE]  
>  每個資料列的 `varchar(max)` 資料類型長度都會不同。 sp_help 會傳回 (-1) 的長度`varchar(max)`資料行。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 會顯示 -1 當作資料行大小。  
  
  