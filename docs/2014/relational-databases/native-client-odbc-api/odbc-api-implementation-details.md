---
title: ODBC API 執行詳細資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, functions
- SQL Server Native Client ODBC driver, SQL Server-specific behaviors
- ODBC, SQL Server-specific behaviors
- functions [ODBC]
ms.assetid: dca92489-f179-4b1f-997c-adcc46aa17a3
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: dae96ba17ee792b703e96ceff2200d1f8f629a01
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/01/2020
ms.locfileid: "82706410"
---
# <a name="odbc-api-implementation-details"></a>ODBC API 實作詳細資料
  本章節會記載搭配 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式使用時的 ODBC 函數，這些函數可呈現 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 特有的行為。 並非所有的 ODBC 函數都有記載在這裡。 個別主題只會討論 ODBC 函數的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 特有問題， 並不是 ODBC 函數的完整參考。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式會使用 ODBC 3.51 規格編譯，而且如果您正在使用 Windows 7 SDK，就會使用 ODBC 3.8 規格編譯。 如需完整的 ODBC 參考，請參閱線上的 Odbc 程式設計[人員參考](https://go.microsoft.com/fwlink/?LinkId=45250)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [SQLBindCol](sqlbindcol.md)  
  
-   [SQLBindParameter](sqlbindparameter.md)  
  
-   [SQLBrowseConnect](sqlbrowseconnect.md)  
  
-   [SQLCancel](sqlcancel.md)  
  
-   [SQLCloseCursor](sqlclosecursor.md)  
  
-   [SQLColAttribute](sqlcolattribute.md)  
  
-   [SQLColumnPrivileges](sqlcolumnprivileges.md)  
  
-   [SQLColumns](sqlcolumns.md)  
  
-   [SQLConfigDataSource](sqlconfigdatasource.md)  
  
-   [SQLConnect](sqlconnect.md)  
  
-   [SQLDescribeCol](sqldescribecol.md)  
  
-   [SQLDescribeParam](sqldescribeparam.md)  
  
-   [SQLDriverConnect](sqldriverconnect.md)  
  
-   [SQLDrivers](sqldrivers.md)  
  
-   [SQLEndTran](sqlendtran.md)  
  
-   [SQLExecDirect](sqlexecdirect.md)  
  
-   [SQLExecute](sqlexecute.md)  
  
-   [SQLFetch](sqlfetch.md)  
  
-   [SQLFetchScroll](sqlfetchscroll.md)  
  
-   [SQLForeignKeys](sqlforeignkeys.md)  
  
-   [SQLFreeHandle](sqlfreehandle.md)  
  
-   [SQLFreeStmt](sqlfreestmt.md)  
  
-   [SQLGetConnectAttr](sqlgetconnectattr.md)  
  
-   [SQLGetCursorName](sqlgetcursorname.md)  
  
-   [SQLGetData](sqlgetdata.md)  
  
-   [SQLGetDescField](sqlgetdescfield.md)  
  
-   [SQLGetDescRec](sqlgetdescrec.md)  
  
-   [SQLGetDiagField](sqlgetdiagfield.md)  
  
-   [SQLGetFunctions](sqlgetfunctions.md)  
  
-   [SQLGetInfo](sqlgetinfo.md)  
  
-   [SQLGetStmtAttr](sqlgetstmtattr.md)  
  
-   [SQLGetTypeInfo](sqlgettypeinfo.md)  
  
-   [SQLMoreResults](sqlmoreresults.md)  
  
-   [SQLNativeSql](sqlnativesql.md)  
  
-   [SQLNumParams](sqlnumparams.md)  
  
-   [SQLNumResultCols](sqlnumresultcols.md)  
  
-   [SQLParamData](sqlparamdata.md)  
  
-   [SQLPrimaryKeys](sqlprimarykeys.md)  
  
-   [SQLProcedureColumns](sqlprocedurecolumns.md)  
  
-   [SQLProcedures](sqlprocedures.md)  
  
-   [SQLPutData](sqlputdata.md)  
  
-   [SQLRowCount](sqlrowcount.md)  
  
-   [SQLSetConnectAttr](sqlsetconnectattr.md)  
  
-   [SQLSetDescField](sqlsetdescfield.md)  
  
-   [SQLSetDescRec](sqlsetdescrec.md)  
  
-   [SQLSetEnvAttr](sqlsetenvattr.md)  
  
-   [SQLSetStmtAttr](sqlsetstmtattr.md)  
  
-   [SQLSpecialColumns](sqlspecialcolumns.md)  
  
-   [SQLStatistics](../statistics/statistics.md)  
  
-   [SQLTablePrivileges](sqltableprivileges.md)  
  
-   [SQLTables](sqltables.md)  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Native Client &#40;ODBC&#41; 參考](../../database-engine/dev-guide/sql-server-native-client-odbc-reference.md)   
 [使用 SQL Server Native Client 建置應用程式](../native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
