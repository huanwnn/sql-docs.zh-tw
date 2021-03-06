---
title: SQLColAttribute 函式 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLColAttribute
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLColAttribute
helpviewer_keywords:
- SQLColAttribute function [ODBC]
ms.assetid: 8c45c598-cb01-4789-a571-e93619a18ed9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c94de3dfc7036277f8be56c401326cdab07a9606
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301288"
---
# <a name="sqlcolattribute-function"></a>SQLColAttribute 函數
**標準**  
 引進的版本： ODBC 3.0 標準合規性： ISO 92  
  
 **摘要**  
 **SQLColAttribute**會傳回結果集中資料行的描述項資訊。 描述元資訊會以字元字串、描述項相依值或整數值的形式傳回。  
  
> [!NOTE]  
>  如需在 ODBC 3 時，驅動程式管理員將此函式對應至哪個功能的詳細資訊。*x*應用程式正在使用 ODBC 2。*x*驅動程式，請參閱[對應取代函式以取得應用程式的回溯相容性](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
  
SQLRETURN SQLColAttribute (  
      SQLHSTMT        StatementHandle,  
      SQLUSMALLINT    ColumnNumber,  
      SQLUSMALLINT    FieldIdentifier,  
      SQLPOINTER      CharacterAttributePtr,  
      SQLSMALLINT     BufferLength,  
      SQLSMALLINT *   StringLengthPtr,  
      SQLLEN *        NumericAttributePtr);  
```  
  
## <a name="arguments"></a>引數  
 *StatementHandle*  
 源語句控制碼。  
  
 *ColumnNumber*  
 源IRD 中要從中抓取域值的記錄號碼。 這個引數會對應到結果資料的資料行數目，並以遞增的資料行順序順序排序，從1開始。 資料行可依任何順序描述。  
  
 可以在這個引數中指定資料行0，但 SQL_DESC_TYPE 和 SQL_DESC_OCTET_LENGTH 以外的所有值都會傳回未定義的值。  
  
 *FieldIdentifier*  
 源描述項控制碼。 這個控制碼會定義應該查詢 IRD 中的哪一個欄位（例如 SQL_COLUMN_TABLE_NAME）。  
  
 *CharacterAttributePtr*  
 輸出緩衝區的指標，如果欄位是字元字串，則會在 IRD 的*ColumnNumber*資料列的*FieldIdentifier*欄位中傳回值。 否則，就不會使用欄位。  
  
 如果*CharacterAttributePtr*為 Null， *StringLengthPtr*仍會傳回*CharacterAttributePtr*所指向的緩衝區中可傳回的位元組總數（不包括字元資料的 Null 終止字元）。  
  
 *BufferLength*  
 源如果*FieldIdentifier*是 ODBC 定義的欄位，而*CharacterAttributePtr*指向字元字串或二進位緩衝區，則這個引數應該是\* *CharacterAttributePtr*的長度。 如果*FieldIdentifier*是一個 ODBC 定義的欄位， \*而*CharacterAttribute*Ptr 是一個整數，則會忽略這個欄位。 如果* \*CharacterAttributePtr*為 Unicode 字串（在呼叫**SQLColAttributeW**時），則*BufferLength*引數必須是偶數。 如果*FieldIdentifier*是驅動程式定義的欄位，應用程式會藉由設定*BufferLength*引數來指出欄位對驅動程式管理員的本質。 *BufferLength*可以有下列值：  
  
-   如果*CharacterAttributePtr*是指標指標， *BufferLength*應該會有值 SQL_IS_POINTER。  
  
-   如果*CharacterAttributePtr*是字元字串的指標，則*BufferLength*是緩衝區的長度。  
  
-   如果*CharacterAttributePtr*是二進位緩衝區的指標，應用程式會將 SQL_LEN_BINARY_ATTR （*長度*）宏的結果放在*BufferLength*中。 這會將負數值放在*BufferLength*中。  
  
-   如果*CharacterAttributePtr*是固定長度資料類型的指標， *BufferLength*必須是下列其中一項： SQL_IS_INTEGER、SQL_IS_UNINTEGER、SQL_SMALLINT 或 SQLUSMALLINT。  
  
 *StringLengthPtr*  
 輸出緩衝區的指標，要在其中傳回 **CharacterAttributePtr*中可傳回的位元組總數（不包括字元資料的 null 終止位元組）。  
  
 針對字元資料，如果可傳回的位元組數目大於或等於*BufferLength*，則\* *CharacterAttributePtr*中的描述元資訊會截斷為*BufferLength*減去 null 終止字元的長度，而且驅動程式會以 null 終止。  
  
 對於所有其他類型的資料，會忽略*BufferLength*的值，而驅動程式會假設 **CharacterAttributePtr*的大小為32位。  
  
 *NumericAttributePtr*  
 輸出整數緩衝區的指標，如果欄位是數值描述元類型，則會在其中傳回 IRD 之*ColumnNumber*資料列的*FieldIdentifier*欄位中的值，例如 SQL_DESC_COLUMN_LENGTH。 否則，就不會使用欄位。 請注意，某些驅動程式可能只會寫入較低的32位或16位的緩衝區，並不會變更較高的順序位。 因此，在呼叫此函式之前，應用程式應該將值初始化為0。  
  
## <a name="returns"></a>傳回值  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR 或 SQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診斷  
 當**SQLColAttribute**傳回 SQL_ERROR 或 SQL_SUCCESS_WITH_INFO 時，可以藉由呼叫具有 SQL_HANDLE_STMT *HandleType*和*StatementHandle**控制碼*的**SQLGetDiagRec**來取得相關聯的 SQLSTATE 值。 下表列出**SQLColAttribute**常傳回的 SQLSTATE 值，並在此函式的內容中說明每一個值;「（DM）」標記法優先于驅動程式管理員所傳回之 SQLSTATEs 的描述。 除非另有說明，否則，與每個 SQLSTATE 值相關聯的傳回碼都是 SQL_ERROR。  
  
|SQLSTATE|錯誤|描述|  
|--------------|-----------|-----------------|  
|01000|一般警告|驅動程式特定的參考用訊息。 （函數會傳回 SQL_SUCCESS_WITH_INFO）。|  
|01004|字串資料，右邊已截斷|緩衝區\* *CharacterAttributePtr*不夠大，無法傳回整個字串值，因此字串值已被截斷。 Untruncated 字串值的長度會在 **StringLengthPtr*中傳回。 （函數會傳回 SQL_SUCCESS_WITH_INFO）。|  
|07005|備妥的語句不是資料*指標規格*|與*StatementHandle*相關聯的語句未傳回結果集，而且*FieldIdentifier*不 SQL_DESC_COUNT。 沒有要描述的資料行。|  
|07009|不正確描述項索引|（DM）為*ColumnNumber*指定的值等於0，而且已 SQL_UB_OFF SQL_ATTR_USE_BOOKMARKS 語句屬性。<br /><br /> 為引數*ColumnNumber*指定的值大於結果集中的資料行數目。|  
|HY000|一般錯誤|發生錯誤，但沒有任何特定 SQLSTATE，且未定義任何執行特定的 SQLSTATE。 **SQLGetDiagField**從診斷資料結構傳回的錯誤訊息描述錯誤及其原因。|  
|HY001|記憶體配置錯誤|驅動程式無法配置支援執行或完成函數所需的記憶體。|  
|HY008|已取消作業|已啟用*StatementHandle*的非同步處理。 已呼叫函式，在完成執行之前，會在*StatementHandle*上呼叫**SQLCancel**或**SQLCancelHandle** 。 然後在*StatementHandle*上再次呼叫函式。<br /><br /> 已呼叫函式，並在完成執行之前，從多執行緒應用程式中的不同執行緒在*StatementHandle*上呼叫**SQLCancel**或**SQLCancelHandle** 。|  
|HY010|函數順序錯誤|（DM）已針對與*StatementHandle*相關聯的連接控制碼呼叫以非同步方式執行的函式。 呼叫 SQLColAttribute 時，此 aynchronous 函數仍在執行中。<br /><br /> （DM）已針對*StatementHandle*呼叫**SQLExecute**、 **SQLExecDirect**或**SQLMoreResults** ，並 SQL_PARAM_DATA_AVAILABLE 傳回。 在抓取所有資料流程參數的資料之前，會呼叫這個函式。<br /><br /> （DM）在呼叫**SQLPrepare**、 **SQLExecDirect**或*StatementHandle*的目錄函數之前，已呼叫函式。<br /><br /> （DM）已針對*StatementHandle*呼叫非同步執行的函式（而非這個函式），而且在呼叫這個函數時仍在執行中。<br /><br /> （DM）已針對*StatementHandle*呼叫**SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**或**SQLSetPos** ，並傳回 SQL_NEED_DATA。 在傳送資料給所有資料執行中參數或資料行之前，已呼叫此函數。|  
|HY013|記憶體管理錯誤|無法處理函數呼叫，因為無法存取基礎記憶體物件，可能是因為記憶體不足的狀況。|  
|HY090|不正確字串或緩衝區長度|（DM） * \*CharacterAttributePtr*是字元字串，而*BufferLength*小於0，但不等於 SQL_NTS。|  
|HY091|不正確描述項欄位識別碼|為引數*FieldIdentifier*指定的值不是其中一個已定義的值，且不是實值定義的值。|  
|HY117|連接因未知的交易狀態而暫停。 僅允許中斷連線和唯讀功能。|（DM）如需暫停狀態的詳細資訊，請參閱[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)函式。|  
|HYC00|驅動程式不支援|驅動程式不支援為引數*FieldIdentifier*指定的值。|  
|HYT01|連接逾時已過期|在資料來源回應要求之前，連接逾時時間已過期。 連接逾時時間是透過**SQLSetConnectAttr**設定，SQL_ATTR_CONNECTION_TIMEOUT。|  
|IM001|驅動程式不支援此功能|（DM）與*StatementHandle*相關聯的驅動程式不支援此功能。|  
|IM017|非同步通知模式中的輪詢已停用|每當使用通知模型時，就會停用輪詢。|  
|IM018|尚未呼叫**SQLCompleteAsync**來完成這個控制碼上先前的非同步作業。|如果控制碼上先前的函式呼叫傳回 SQL_STILL_EXECUTING 而且如果啟用通知模式，則必須在控制碼上呼叫**SQLCompleteAsync** ，才能執行後置處理並完成作業。|  
  
 在**SQLPrepare**之後和**SQLExecute**之前呼叫時， **SQLColAttribute**可以傳回**SQLPrepare**或**SQLExecute**所能傳回的任何 SQLSTATE，視資料來源評估與*StatementHandle*相關聯的 SQL 語句而定。  
  
 基於效能的考慮，應用程式不應該在執行語句之前呼叫**SQLColAttribute** 。  
  
## <a name="comments"></a>評價  
 如需應用程式如何使用**SQLColAttribute**傳回之資訊的詳細資訊，請參閱[結果集中繼資料](../../../odbc/reference/develop-app/result-set-metadata.md)。  
  
 **SQLColAttribute**會傳回\* *NumericAttributePtr*或\* *CharacterAttributePtr*中的資訊。 整數資訊會在\* *NumericAttributePtr*中當做 SQLLEN 值傳回;所有其他的資訊格式會在\* *CharacterAttributePtr*中傳回。 當\* *NumericAttributePtr*中傳回信息時，驅動程式會忽略*CharacterAttributePtr*、 *BufferLength*和*StringLengthPtr*。 當\* *CharacterAttributePtr*中傳回信息時，驅動程式會忽略*NumericAttributePtr*。  
  
 **SQLColAttribute**會從 IRD 的描述項欄位傳回值。 會使用語句控制碼（而不是描述項控制碼）來呼叫函數。 **SQLColAttribute**針對本節稍後列出的*FieldIdentifier*值所傳回的值，也可以藉由呼叫具有適當 IRD 控制碼的**SQLGetDescField**來抓取。  
  
 目前定義的描述項欄位、引進它們的 ODBC 版本，以及在其中傳回信息的引數會在本節稍後顯示;驅動程式可能會定義更多的描述元類型，以利用不同的資料來源。  
  
 ODBC 3。*x*驅動程式必須傳回每個描述項欄位的值。 如果描述項欄位不適用於驅動程式或資料來源，除非另有說明，否則驅動程式會在\* *StringLengthPtr*中傳回0，或在 **CharacterAttributePtr*中傳回空字串。  
  
## <a name="backward-compatibility"></a>回溯相容性  
 ODBC 3。*x*函數**SQLColAttribute**會取代已被取代的 ODBC 2。*x*函式**SQLColAttributes**。 將**SQLColAttributes**對應至**SQLColAttribute**時（當 ODBC 2.*x*應用程式正在使用 ODBC 3。*x*驅動程式），或將**SQLColAttribute**對應至**SQLColAttributes** （當 ODBC 3 時）。*x*應用程式正在使用 ODBC 2。*x*驅動程式），驅動程式管理員會透過傳遞*FieldIdentifier*的值、將其對應至新的值，或傳回錯誤，如下所示：  
  
> [!NOTE]  
>  在 ODBC 3 的*FieldIdentifier*值中所使用的前置詞。*x*已從 ODBC 2 中使用的變更。*x*。 新的前置詞為 "SQL_DESC";舊的前置詞為 "SQL_COLUMN"。  
  
-   如果是 ODBC 2 的 **#define**值，則為。*x* *FieldIdentifier*與 ODBC 3 的 **#define**值相同。*x* *FieldIdentifier*，函式呼叫中的值只會透過傳遞。  
  
-   ODBC 2 的 **#define**值。*x* *FieldIdentifiers* SQL_COLUMN_LENGTH、SQL_COLUMN_PRECISION 和 SQL_COLUMN_SCALE 不同于 ODBC 3 的 **#define**值。*x* *FieldIdentifiers* SQL_DESC_PRECISION、SQL_DESC_SCALE 和 SQL_DESC_LENGTH。 ODBC 2。*x*驅動程式只需要支援 ODBC 2。*x*值。 ODBC 3。*x*驅動程式必須同時支援這三個*FieldIdentifiers*的 "SQL_COLUMN" 和 "SQL_DESC" 值。 這些值不同，因為在 ODBC 3 中的精確度、小數位數和長度的定義不同。*x* ，而非 ODBC 2。*x*。 如需詳細資訊，請參閱資料[行大小、小數位數、傳輸八位長度和顯示大小](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)。  
  
-   如果是 ODBC 2 的 **#define**值，則為。*x* *FIELDIDENTIFIER*不同于 ODBC 3 的 **#define**值。*x* *FIELDIDENTIFIER*，如同 COUNT、NAME 和 NullABLE 值所發生，函式呼叫中的值會對應至相對應的值。 例如，SQL_COLUMN_COUNT 會對應到 SQL_DESC_COUNT，而 SQL_DESC_COUNT 會對應到 SQL_COLUMN_COUNT，視對應的方向而定。  
  
-   如果*FieldIdentifier*是 ODBC 3 中的新值，則為。*x*，在 ODBC 2 中沒有對應的值。*x*，它不會在 ODBC 3 時對應。*x*應用程式會在對 ODBC 2 中**SQLColAttribute**的呼叫中使用它。*x*驅動程式，而呼叫會傳回 SQLSTATE HY091 （不正確描述項欄位識別碼）。  
  
 下表列出**SQLColAttribute**所傳回的描述元類型。 *NumericAttributePtr*值的類型是**SQLLEN \* **。  
  
|*FieldIdentifier*|資訊<br /><br /> 傳回于|描述|  
|-----------------------|---------------------------------|-----------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE （ODBC 1.0）|*NumericAttributePtr*|SQL_TRUE 資料行是否為自動遞增資料行。<br /><br /> 如果資料行不是自動遞增資料行，或不是數值，則為 SQL_FALSE。<br /><br /> 此欄位僅適用于數值資料類型資料行。 應用程式可以將值插入包含自動遞增資料行的資料列，但通常無法更新資料行中的值。<br /><br /> 當插入自動遞增資料行時，會在插入時將唯一值插入資料行。 增量未定義，但為數據源特定。 應用程式不應假設自動遞增資料行是從任何特定的點開始，或以任何特定的值遞增。|  
|SQL_DESC_BASE_COLUMN_NAME （ODBC 3.0）|*CharacterAttributePtr*|結果集資料行的基底資料行名稱。 如果基底資料行名稱不存在（就像是運算式的資料行），則這個變數會包含空字串。<br /><br /> 這項資訊會從 IRD 的 [SQL_DESC_BASE_COLUMN_NAME 記錄] 欄位傳回，這是唯讀欄位。|  
|SQL_DESC_BASE_TABLE_NAME （ODBC 3.0）|*CharacterAttributePtr*|包含資料行之基表的名稱。 如果基表名稱無法定義或不適用，則此變數包含空字串。<br /><br /> 這項資訊會從 IRD 的 [SQL_DESC_BASE_TABLE_NAME 記錄] 欄位傳回，這是唯讀欄位。|  
|SQL_DESC_CASE_SENSITIVE （ODBC 1.0）|*NumericAttributePtr*|如果將資料行視為區分大小寫的定序和比較，SQL_TRUE。<br /><br /> SQL_FALSE，如果資料行不會被視為區分大小寫的定序和比較，或非字元。|  
|SQL_DESC_CATALOG_NAME （ODBC 2.0）|*CharacterAttributePtr*|包含資料行之資料表的目錄。 如果資料行是運算式，或者資料行是視圖的一部分，則傳回的值會是「執行定義」。 如果資料來源不支援目錄，或無法判斷目錄名稱，則會傳回空字串。 此 VARCHAR 記錄欄位不限於128個字元。|  
|SQL_DESC_CONCISE_TYPE （ODBC 1.0）|*NumericAttributePtr*|精確的資料類型。<br /><br /> 若為 datetime 和 interval 資料類型，此欄位會傳回精簡的資料類型。例如，SQL_TYPE_TIME 或 SQL_INTERVAL_YEAR。 （如需詳細資訊，請參閱附錄 D：資料類型中的[資料類型識別碼和描述](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md)元）。<br /><br /> 這項資訊會從 IRD 的 [SQL_DESC_CONCISE_TYPE 記錄] 欄位中傳回。|  
|SQL_DESC_COUNT （ODBC 1.0）|*NumericAttributePtr*|結果集中可用的資料行數目。 如果結果集中沒有任何資料行，則會傳回0。 *ColumnNumber*引數中的值會被忽略。<br /><br /> 這項資訊會從 IRD 的 SQL_DESC_COUNT 標頭欄位中傳回。|  
|SQL_DESC_DISPLAY_SIZE （ODBC 1.0）|*NumericAttributePtr*|要從資料行顯示資料所需的最大字元數。 如需顯示大小的詳細資訊，請參閱附錄 D：資料類型中的資料[行大小、小數位數、傳輸八位長度和顯示大小](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)。|  
|SQL_DESC_FIXED_PREC_SCALE （ODBC 1.0）|*NumericAttributePtr*|SQL_TRUE，如果資料行具有固定的有效位數和非零的小數位數，且其為數據源特定。<br /><br /> SQL_FALSE，如果資料行沒有固定的有效位數和非零的小數位數，且其為數據源特定。|  
|SQL_DESC_LABEL （ODBC 2.0）|*CharacterAttributePtr*|資料行標籤或標題。 例如，名為 EmpName 的資料行可能會標示為 Employee Name，或可能以別名標示。<br /><br /> 如果資料行沒有標籤，則會傳回資料行名稱。 如果資料行未標記且未命名，則會傳回空字串。|  
|SQL_DESC_LENGTH （ODBC 3.0）|*NumericAttributePtr*|數值，這是字元字串或二進位資料類型的最大或實際字元長度。 這是固定長度資料類型的最大字元長度，或可變長度資料類型的實際字元長度。 其值一律會排除結束字元字串的 null 終止位元組。<br /><br /> 這項資訊會從 IRD 的 [SQL_DESC_LENGTH 記錄] 欄位中傳回。<br /><br /> 如需長度的詳細資訊，請參閱附錄 D：資料類型中的資料[行大小、小數位數、傳輸八位長度和顯示大小](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)。|  
|SQL_DESC_LITERAL_PREFIX （ODBC 3.0）|*CharacterAttributePtr*|此 VARCHAR （128）記錄欄位包含一個或多個字元，驅動程式會將該字元識別為此資料類型之常值的前置詞。 此欄位包含不適用常值前置詞之資料類型的空字串。 如需詳細資訊，請參閱常值前置詞[和尾碼](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md)。|  
|SQL_DESC_LITERAL_SUFFIX （ODBC 3.0）|*CharacterAttributePtr*|此 VARCHAR （128）記錄欄位包含一個或多個字元，驅動程式會將該字元辨識為此資料類型之常值的尾碼。 對於不適用常值尾碼的資料類型，此欄位包含空字串。 如需詳細資訊，請參閱常值前置詞[和尾碼](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md)。|  
|SQL_DESC_LOCAL_TYPE_NAME （ODBC 3.0）|*CharacterAttributePtr*|這個 VARCHAR （128）記錄欄位包含資料類型的任何當地語系化（原生語言）名稱，可能與資料類型的一般名稱不同。 如果沒有當地語系化的名稱，則會傳回空字串。 此欄位僅供顯示之用。 字串的字元集與地區設定相關，通常是伺服器的預設字元集。|  
|SQL_DESC_NAME （ODBC 3.0）|*CharacterAttributePtr*|資料行別名（如果適用的話）。 如果資料行別名不適用，則會傳回資料行名稱。 不論是哪一種情況，SQL_DESC_UNNAMED 都設為 SQL_NAMED。 如果沒有資料行名稱或資料行別名，則會傳回空字串，並 SQL_DESC_UNNAMED 設定為 SQL_UNNAMED。<br /><br /> 這項資訊會從 IRD 的 [SQL_DESC_NAME 記錄] 欄位中傳回。|  
|SQL_DESC_NullABLE （ODBC 3.0）|*NumericAttributePtr*|如果資料行可以有 Null 值，則 SQL_ 可為 null;SQL_NO_NullS，如果資料行沒有 Null 值，則為，或者，如果不知道資料行是否接受 Null 值，則 SQL_NullABLE_UNKNOWN。<br /><br /> 這項資訊會從 IRD 的 [SQL_DESC_NullABLE 記錄] 欄位中傳回。|  
|SQL_DESC_NUM_PREC_RADIX （ODBC 3.0）|*NumericAttributePtr*|如果 [SQL_DESC_TYPE] 欄位中的資料類型是近似數值資料類型，此 SQLINTEGER 欄位會包含值2，因為 [SQL_DESC_PRECISION] 欄位包含位的數目。 如果 [SQL_DESC_TYPE] 欄位中的資料類型是精確數值資料類型，此欄位會包含值10，因為 [SQL_DESC_PRECISION] 欄位包含小數位數。 針對所有非數值資料類型，此欄位會設定為0。|  
|SQL_DESC_OCTET_LENGTH （ODBC 3.0）|*NumericAttributePtr*|字元字串或二進位資料類型的長度（以位元組為單位）。 針對固定長度的字元或二進位類型，這是實際的長度（以位元組為單位）。 對於可變長度的字元或二進位類型，這是最大長度（以位元組為單位）。 這個值不包含 null 結束字元。<br /><br /> 這項資訊會從 IRD 的 [SQL_DESC_OCTET_LENGTH 記錄] 欄位中傳回。<br /><br /> 如需長度的詳細資訊，請參閱附錄 D：資料類型中的資料[行大小、小數位數、傳輸八位長度和顯示大小](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)。|  
|SQL_DESC_PRECISION （ODBC 3.0）|*NumericAttributePtr*|數值資料類型的數值，表示適用的有效位數。 針對 SQL_TYPE_TIME、SQL_TYPE_TIMESTAMP 和所有代表時間間隔之間隔資料類型的資料類型，其值為小數秒陣列件適用的有效位數。<br /><br /> 這項資訊會從 IRD 的 [SQL_DESC_PRECISION 記錄] 欄位中傳回。|  
|SQL_DESC_SCALE （ODBC 3.0）|*NumericAttributePtr*|數值資料類型的適用小數位數值。 對於 DECIMAL 和 NUMERIC 資料類型，這是定義的小數位數。 所有其他資料類型都未定義。<br /><br /> 這項資訊會從 IRD 的 [尺規記錄] 欄位中傳回。|  
|SQL_DESC_SCHEMA_NAME （ODBC 2.0）|*CharacterAttributePtr*|包含資料行之資料表的架構。 如果資料行是運算式，或者資料行是視圖的一部分，則傳回的值會是「執行定義」。 如果資料來源不支援架構，或無法判斷架構名稱，則會傳回空字串。 此 VARCHAR 記錄欄位不限於128個字元。|  
|SQL_DESC_SEARCHABLE （ODBC 1.0）|*NumericAttributePtr*|如果資料行不能用在 WHERE 子句中，SQL_PRED_NONE。 （這與 ODBC 2 中的 SQL_UNSEARCHABLE 值相同。*x*）。<br /><br /> SQL_PRED_CHAR，如果資料行可以在 WHERE 子句中使用，但只能用在 LIKE 述詞中。 （這與 ODBC 2 中的 SQL_LIKE_ONLY 值相同。*x*）。<br /><br /> SQL_PRED_BASIC，如果資料行可以在 WHERE 子句中與所有比較運算子搭配使用（例如）。 （這與 ODBC 2 中的 SQL_EXCEPT_LIKE 值相同。*x*）。<br /><br /> 如果資料行可以在 WHERE 子句中搭配任何比較運算子使用，則 SQL_PRED_SEARCHABLE。<br /><br /> SQL_LONGVARCHAR 和 SQL_LONGVARBINARY 類型的資料行通常會傳回 SQL_PRED_CHAR。|  
|SQL_DESC_TABLE_NAME （ODBC 2.0）|*CharacterAttributePtr*|包含資料行之資料表的名稱。 如果資料行是運算式，或者資料行是視圖的一部分，則傳回的值會是「執行定義」。<br /><br /> 如果無法判斷資料表名稱，則會傳回空字串。|  
|SQL_DESC_TYPE （ODBC 3.0）|*NumericAttributePtr*|指定 SQL 資料類型的數值。<br /><br /> 當*ColumnNumber*等於0時，會傳回可變長度書簽的 SQL_BINARY，而且會針對固定長度的書簽傳回 SQL_INTEGER。<br /><br /> 若為 datetime 和 interval 資料類型，此欄位會傳回 verbose 資料類型： SQL_DATETIME 或 SQL_INTERVAL。 （如需詳細資訊，請參閱附錄 D：資料類型中的[資料類型識別碼和描述](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md)元。<br /><br /> 這項資訊會從 IRD 的 [SQL_DESC_TYPE 記錄] 欄位中傳回。 **注意：** 以處理 ODBC 2。*x*驅動程式，請改用 SQL_DESC_CONCISE_TYPE。|  
|SQL_DESC_TYPE_NAME （ODBC 1.0）|*CharacterAttributePtr*|與資料來源相關的資料類型名稱;例如，"CHAR"、"VARCHAR"、"MONEY"、"LONG VARBINARY" 或 "CHAR （） FOR BIT DATA"。<br /><br /> 如果類型是未知的，則會傳回空字串。|  
|SQL_DESC_UNNAMED （ODBC 3.0）|*NumericAttributePtr*|SQL_NAMED 或 SQL_UNNAMED。 如果 IRD 的 SQL_DESC_NAME 欄位包含資料行別名或資料行名稱，則會傳回 SQL_NAMED。 如果沒有資料行名稱或資料行別名，則會傳回 SQL_UNNAMED。<br /><br /> 這項資訊會從 IRD 的 [SQL_DESC_UNNAMED 記錄] 欄位中傳回。|  
|SQL_DESC_UNSIGNED （ODBC 1.0）|*NumericAttributePtr*|如果資料行不帶正負號（或不是數值），SQL_TRUE。<br /><br /> 如果資料行已簽署，SQL_FALSE。|  
|SQL_DESC_UPDATABLE （ODBC 1.0）|*NumericAttributePtr*|資料行是由已定義常數的值所描述：<br /><br /> SQL_ATTR_READONLY SQL_ATTR_WRITE SQL_ATTR_READWRITE_UNKNOWN<br /><br /> SQL_DESC_UPDATABLE 描述結果集中資料行的更新性，而不是基表中的資料行。 結果集資料行所依據之基底資料行的可更新性可能與此欄位中的值不同。 資料行是否可更新，可以根據資料類型、使用者權限和結果集本身的定義而定。 如果資料行是否可更新，則應該傳回 SQL_ATTR_READWRITE_UNKNOWN。|  
  
 **SQLColAttribute**是**SQLDescribeCol**的可擴充替代方案。 **SQLDescribeCol**會根據 ANSI-89 SQL 傳回一組固定的描述項資訊。 **SQLColAttribute**可讓您存取 ANSI SQL-92 和 DBMS 廠商延伸模組中提供的更豐富描述項資訊集。  
  
## <a name="related-functions"></a>相關函數  
  
|如需下列資訊|請參閱|  
|---------------------------|---------|  
|將緩衝區系結至結果集內的資料行|[SQLBindCol 函數](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|取消語句處理|[SQLCancel 函式](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|傳回結果集中資料行的相關資訊|[SQLDescribeCol 函式](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|提取資料區塊或透過結果集進行滾動|[SQLFetchScroll 函式](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|提取多個資料列|[SQLFetch 函式](../../../odbc/reference/syntax/sqlfetch-function.md)|  
  
## <a name="example"></a>範例  
 下列範例程式碼不會釋放控制碼和連接。 請參閱[SQLFreeHandle 函數](../../../odbc/reference/syntax/sqlfreehandle-function.md)、[範例 ODBC 程式](../../../odbc/reference/sample-odbc-program.md)和[SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)函式，以取得程式碼範例以釋放控制碼和語句。  
  
```cpp  
// SQLColAttibute.cpp  
// compile with: user32.lib odbc32.lib  
  
#define UNICODE  
  
#include <windows.h>  
#include <sqlext.h>  
#include <strsafe.h>  
  
struct DataBinding {  
   SQLSMALLINT TargetType;  
   SQLPOINTER TargetValuePtr;  
   SQLINTEGER BufferLength;  
   SQLLEN StrLen_or_Ind;  
};  
  
void printStatementResult(SQLHSTMT hstmt) {  
   int bufferSize = 1024, i;  
   SQLRETURN retCode;  
   SQLSMALLINT numColumn = 0, bufferLenUsed;
   
   retCode = SQLNumResultCols(hstmt, &numColumn);  
   
   SQLPOINTER* columnLabels = (SQLPOINTER *)malloc( numColumn * sizeof(SQLPOINTER*) );  
   struct DataBinding* columnData = (struct DataBinding*)malloc( numColumn * sizeof(struct DataBinding) );  
  
   printf( "Columns from that table:\n" );  
   for ( i = 0 ; i < numColumn ; i++ ) {  
      columnLabels[i] = (SQLPOINTER)malloc( bufferSize*sizeof(char) );  
  
      retCode = SQLColAttribute(hstmt, (SQLUSMALLINT)i + 1, SQL_DESC_LABEL, columnLabels[i], (SQLSMALLINT)bufferSize, &bufferLenUsed, NULL);  
      wprintf( L"Column %d: %s\n", i, (wchar_t*)columnLabels[i] );  
   }  
  
   // allocate memory for the binding  
   for ( i = 0 ; i < numColumn ; i++ ) {  
      columnData[i].TargetType = SQL_C_CHAR;  
      columnData[i].BufferLength = (bufferSize+1);  
      columnData[i].TargetValuePtr = malloc( sizeof(unsigned char)*columnData[i].BufferLength );  
   }  
  
   // setup the binding   
   for ( i = 0 ; i < numColumn ; i++ ) {  
      retCode = SQLBindCol(hstmt, (SQLUSMALLINT)i + 1, columnData[i].TargetType,   
         columnData[i].TargetValuePtr, columnData[i].BufferLength, &(columnData[i].StrLen_or_Ind));  
   }  
  
   printf( "Data from that table:\n" );  
   // fetch the data and print out the data  
   for ( retCode = SQLFetch(hstmt) ; retCode == SQL_SUCCESS || retCode == SQL_SUCCESS_WITH_INFO ; retCode = SQLFetch(hstmt) ) {  
      int j;  
      for ( j = 0 ; j < numColumn ; j++ )  
         wprintf( L"%s: %hs\n", columnLabels[j], columnData[j].TargetValuePtr );  
      printf( "\n" );  
   }  
   printf( "\n" );   
}  
  
int main() {  
   int bufferSize = 1024, i, count = 1, numCols = 5;  
   wchar_t firstTableName[1024], * dbName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize ), * userName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize );  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
   SQLWCHAR connStrbuffer[1024];  
   SQLSMALLINT connStrBufferLen, bufferLen;  
   SQLRETURN retCode;  
  
   SQLHENV henv = NULL;   // Environment     
   SQLHDBC hdbc = NULL;   // Connection handle  
   SQLHSTMT hstmt = NULL;   // Statement handle  
  
   struct DataBinding* catalogResult = (struct DataBinding*) malloc( numCols * sizeof(struct DataBinding) );  
   SQLWCHAR* selectAllQuery = (SQLWCHAR *)malloc( sizeof(SQLWCHAR) * bufferSize );  
  
   // connect to database  
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLCHAR *)(void*)SQL_OV_ODBC3, -1);  
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);  
   retCode = SQLDriverConnect(hdbc, desktopHandle, L"Driver={SQL Server}", SQL_NTS, connStrbuffer, 1025, &connStrBufferLen, SQL_DRIVER_PROMPT);  
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   // display the database information  
   retCode = SQLGetInfo(hdbc, SQL_DATABASE_NAME, dbName, (SQLSMALLINT)bufferSize, (SQLSMALLINT *)&bufferLen);  
   retCode = SQLGetInfo(hdbc, SQL_USER_NAME, userName, (SQLSMALLINT)bufferSize, &bufferLen);  
  
   for ( i = 0 ; i < numCols ; i++ ) {  
      catalogResult[i].TargetType = SQL_C_CHAR;  
      catalogResult[i].BufferLength = (bufferSize + 1);  
      catalogResult[i].TargetValuePtr = malloc( sizeof(unsigned char)*catalogResult[i].BufferLength );  
   }  
  
   // Set up the binding. This can be used even if the statement is closed by closeStatementHandle  
   for ( i = 0 ; i < numCols ; i++ )  
      retCode = SQLBindCol(hstmt, (SQLUSMALLINT)i + 1, catalogResult[i].TargetType, catalogResult[i].TargetValuePtr, catalogResult[i].BufferLength, &(catalogResult[i].StrLen_or_Ind));  
  
   retCode = SQLTables( hstmt, (SQLWCHAR*)SQL_ALL_CATALOGS, SQL_NTS, L"", SQL_NTS, L"", SQL_NTS, L"", SQL_NTS );  
   retCode = SQLFreeStmt(hstmt, SQL_CLOSE);  
  
   retCode = SQLTables( hstmt, dbName, SQL_NTS, userName, SQL_NTS, L"%", SQL_NTS, L"TABLE", SQL_NTS );  
  
   for ( retCode = SQLFetch(hstmt) ; retCode == SQL_SUCCESS || retCode == SQL_SUCCESS_WITH_INFO ; retCode = SQLFetch(hstmt), ++count )  
      if ( count == 1 )  
         StringCchPrintfW( firstTableName, 1024, L"%hs", catalogResult[2].TargetValuePtr );  
   retCode = SQLFreeStmt(hstmt, SQL_CLOSE);  
  
   wprintf( L"Select all data from the first table (%s)\n", firstTableName );  
   StringCchPrintfW( selectAllQuery, bufferSize, L"SELECT * FROM %s", firstTableName );  
  
   retCode = SQLExecDirect(hstmt, selectAllQuery, SQL_NTS);  
   printStatementResult(hstmt);  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [ODBC API 參考](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC 標頭檔](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC 程式範例](../../../odbc/reference/sample-odbc-program.md)
