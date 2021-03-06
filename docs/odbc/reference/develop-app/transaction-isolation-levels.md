---
title: 交易隔離等級（ODBC） |Microsoft Docs
ms.custom: seo-dt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- dirty reads [ODBC]
- isolation levels [ODBC]
- nonrepeatable reads [ODBC]
- read uncommitted [ODBC]
- read committed [ODBC]
- serializable reads [ODBC]
- phantoms [ODBC]
- transaction isolation [ODBC]
- repeatable reads [ODBC]
- transactions [ODBC], isolation
ms.assetid: 0d638d55-ffd0-48fb-834b-406f466214d4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 622b4cd7f0db259b5ecfd5be63b27df64be965e7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298031"
---
# <a name="transaction-isolation-levels-odbc"></a>交易隔離等級（ODBC）
*交易隔離等級*是交易隔離成功的範圍量值。 特別是，交易隔離等級是由下列現象的存在與否所定義：  
  
-   中途**讀取**當交易讀取尚未認可的資料時，就會發生中途*讀取*。 例如，假設交易1更新一個資料列。 交易2會在交易1認可更新之前讀取更新的資料列。 如果交易1回復變更，交易2將會有被視為永遠不存在的讀取資料。  
  
-   **不可重複讀取**當交易讀取相同的資料列兩次，但每次都取得不同的資料時，就會發生*不可重複讀取*。 例如，假設交易1讀取資料列。 Transaction 2 會更新或刪除該資料列，並認可更新或刪除。 如果交易1讀取資料列，它會抓取不同的資料列值，或探索是否已刪除資料列。  
  
-   **幻像**虛設*專案是符合*搜尋條件的資料列，但一開始並不會出現。 例如，假設交易1讀取一組滿足某些搜尋條件的資料列。 交易2會產生符合交易1搜尋條件的新資料列（透過更新或插入）。 如果交易 1 reexecutes 讀取資料列的語句，它會取得一組不同的資料列。  
  
 這四種交易隔離等級（如 SQL-92 所定義）是根據這些現象來定義。 在下表中，"X" 會標示每個可能發生的現象。  
  
|交易隔離等級|中途讀取|不可重複讀取|網域虛設物件|  
|---------------------------------|-----------------|-------------------------|--------------|  
|讀取未認可|X|X|X|  
|讀取認可|--|X|X|  
|可重複讀取|--|--|X|  
|可序列化|--|--|--|  
  
 下表描述 DBMS 可能會執行交易隔離等級的簡單方式。  
  
> [!IMPORTANT]  
>  大部分的 Dbms 使用比這些更複雜的配置來增加並行。 這些範例僅供說明之用。 特別是，ODBC 並不規定特定 Dbms 如何彼此隔離交易。  
  
|交易隔離|可能的執行|  
|---------------------------|-----------------------------|  
|讀取未認可|交易不會彼此隔離。 如果 DBMS 支援其他交易隔離等級，則會忽略它用來執行這些層級的任何機制。 因此，它們不會對其他交易造成負面影響，在讀取未認可層級執行的交易通常是唯讀的。|  
|讀取認可|交易會等待，直到其他交易的資料列被解除鎖定為止;這會防止它讀取任何「已變更」的資料。<br /><br /> 交易會保留讀取鎖定（如果它唯讀取資料列）或目前資料列的寫入鎖定（如果它更新或刪除資料列），以防止其他交易更新或刪除它。 當交易移出目前的資料列時，就會釋放讀取鎖定。 它會保留寫入鎖定，直到認可或回復為止。|  
|可重複讀取|交易會等待，直到其他交易的資料列被解除鎖定為止;這會防止它讀取任何「已變更」的資料。<br /><br /> 交易會在它傳回給應用程式的所有資料列上保留讀取鎖定，並在其插入、更新或刪除的所有資料列上寫入鎖定。 例如，如果交易包含**從 Orders 中選取\* **的 SQL 語句，則當應用程式提取資料列時，交易會讀取鎖定。 如果交易包含 SQL 語句 [**從訂單中刪除，其中狀態 = ' 已關閉**]，則在刪除資料列時，交易會將其鎖定。<br /><br /> 因為其他交易無法更新或刪除這些資料列，所以目前的交易會避免任何不可重複讀取。 交易會在認可或回復時釋放其鎖定。|  
|可序列化|交易會等待，直到其他交易的資料列被解除鎖定為止;這會防止它讀取任何「已變更」的資料。<br /><br /> 交易會在它所影響的資料列範圍內，保留讀取鎖定（如果唯讀取資料列）或寫入鎖定（如果可以更新或刪除資料列）。 例如，如果交易包含**從 Orders 選取\* **的 SQL 語句，範圍就是整個 orders 資料表;交易讀取會鎖定資料表，而且不允許將任何新的資料列插入其中。 如果交易包含 SQL 語句 [**從訂單中刪除，其中狀態 = ' 已關閉**]，則範圍為狀態為「已關閉」的所有資料列;交易寫入-鎖定 Orders 資料表中狀態為「已關閉」的所有資料列，且不允許插入或更新任何資料列，因此產生的資料列狀態為「已關閉」。<br /><br /> 因為其他交易無法更新或刪除範圍內的資料列，所以目前的交易會避免任何不可重複讀取。 因為其他交易無法插入範圍內的任何資料列，所以目前的交易會避免任何幻像。 交易會在認可或回復時釋放其鎖定。|  
  
 請務必注意，交易隔離等級並不會影響交易查看其本身變更的能力;交易一律會看到其所做的任何變更。 例如，交易可能由兩個**UPDATE**語句所組成，第一個會將所有員工的費用提高到10%，而第二個則會將任何員工的費用設定為該金額的最大金額。 這只會成功為單一交易，因為第二個**UPDATE**語句可以查看第一個的結果。
