---
title: IBCPSession (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: COM
helpviewer_keywords:
- IBCPSession interface
ms.assetid: 00d0311f-8b71-4ad6-824d-0e89119347a3
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 653bd8aad3a10a3929b7ced76e28e4d570733ad3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307339"
---
# <a name="ibcpsession-ole-db"></a>IBCPSession (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **IBCPSession** 介面會公開以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 檔案為基礎之大量複製作業的支援。 **IBCPSession**介面會在與會話相同[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]層級的 Native Client OLE DB 提供者中公開。 在[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者中，資料來源物件是會話物件的 factory，而大量複製作業則是在連接屬性 SSPROP_ENABLEBULKCOPY 中指定。 此外，SSPROP_ENABLEFASTLOAD 屬性應該要設定為 true。  
  
 然後，呼叫 **IDBCreateSession::CreateSession** 方法將會導致建立 **BulkCopySession** 物件。 所有透過 **IBCPSession** 物件公開之以檔案為基礎的大量複製方法會變成可在這個 **IBCPSession** 物件的 **IBCPSession** 介面上使用幾乎相同的簽章進行呼叫。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者支援透過[IRowsetFastLoad](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md)介面進行以記憶體為基礎的大量複製作業。  
  
 如需有關使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者進行大量複製作業的詳細資訊，請參閱[執行大量複製作業](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)。  
  
 如需示範如何使用 **IBCPSession** 介面的範例，請參閱 [IBCPSession::BCPDone &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpdone-ole-db.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
|方法|描述|  
|------------|-----------------|  
|[IBCPSession::BCPColFmt &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md)|在程式變數與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料行之間建立繫結。|  
|[IBCPSession::BCPColumns &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md)|設定要繫結至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表中之資料行的欄位數目。|  
|[IBCPSession::BCPControl &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md)|設定大量複製作業的選項。|  
|[IBCPSession::BCPDone &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpdone-ole-db.md)|認可要傳送至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的其餘資料列。|  
|[IBCPSession::BCPExec &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpexec-ole-db.md)|執行大量複製作業。|  
|[IBCPSession::BCPInit &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)|初始化大量複製結構、執行一些錯誤檢查、確認資料和格式檔案名稱正確無誤，然後開啟這些項目。|  
|[IBCPSession::BCPReadFmt &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md)|從格式檔案中讀取每個資料行的格式資訊。|  
|[IBCPSession::BCPWriteFmt &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md)|將每個資料行的格式資訊寫入格式檔案。|  
  
## <a name="see-also"></a>另請參閱  
 [介面 &#40;OLE DB&#41;](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  
