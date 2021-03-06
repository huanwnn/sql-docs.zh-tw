---
title: 附錄-1 （OracleToSQL） |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e01f8be5-ce68-4c9f-bd13-d65e73a16470
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 85051c1138e2edd152ab5fce5b5a32f4ea6f297b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "68264526"
---
# <a name="appendix---1-oracletosql"></a>附錄 - 1 (OracleToSQL)
SSMA 主控台命令列選項的快速觀點：  
  
|Sl. 不可以。|Switch|必要項？|切換引數|允許的值|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s/腳本|是|scriptfile|有效的 XML 檔案名。<br /><br />主控台腳本定義檔。|  
|2|-v/變數|否|variablevaluefile|有效的 XML 檔案名。<br /><br />如果腳本檔案中使用了變數，則必須指定此檔案。|  
|3|-c/serverconnection|否|serverconnectionfile|有效的 XML 檔案名。<br /><br />此檔案包含伺服器連接資訊。|  
|4|-x/xmloutput|否|xmloutputfile|此選項表示 XML 格式的主控台輸出。 如果未指定此選項，則預設輸出為文字格式。<br /><br />如果未指定 xmloutputfile，則會將 XML 輸出導向`STDOUT`至。<br /><br />Xmloutputfile 是主控台輸出以 XML 格式寫入的檔案名。|  
|5|-l/log|否|logfile|有效的檔案名。|  
|6|-e/projectenvironment|否|projectenvironmentfolder|包含 SSMA 專案環境檔案的有效資料夾名稱。|  
|7|-p/securepassword|否|-a/add {<server_id> [,.。。n] &#124; all}-c&#124;serverconnection <伺服器-連接檔案> [-v&#124;變數 <變數-值-檔案>] [-o/覆寫]<br /><br />或<br /><br />-a/add {<server_id> [,.。。n] &#124; all}-s&#124;腳本 <腳本-檔案> [-v&#124;變數 <變數-值-檔案>] [-o/覆寫]<br /><br />-r/remove {<server_id> [，.。。n] &#124; 全部}<br /><br />-l/list<br /><br />-e/export {<伺服器識別碼> [，.。。n] &#124; all} <加密-密碼-檔案><br /><br />-i/import {<伺服器識別碼> [，.。。n] &#124; all} <加密-密碼-檔案>|若已指定，則此選項不得與任何其他選項結合。<br /><br />伺服器識別碼：為伺服器 {string} 提供的唯一識別碼<br /><br />伺服器-連接-檔案：伺服器定義檔（serverconnectionfile 或 scriptfile）。<br /><br />變數-值-檔案：它是變數定義檔，並用於伺服器連接檔案中。<br /><br />加密-密碼-檔案：這是使用使用者指定的傳遞片語加密的伺服器密碼檔案。|  
|8|-?|否|不適用|不適用|  
  
## <a name="see-also"></a>另請參閱  
[執行 SSMA 主控台（Oracle）](https://msdn.microsoft.com/7228ccba-c69f-4b4c-8664-01a2750183c5)  
  
