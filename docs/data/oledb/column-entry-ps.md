---
title: "COLUMN_ENTRY_PS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COLUMN_ENTRY_PS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_ENTRY_PS マクロ"
ms.assetid: 563c12b0-3376-49d5-a14f-aa68d1e63a7a
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# COLUMN_ENTRY_PS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

行セット内の特定の列に行セットのバインディングを表します。  
  
## 構文  
  
```  
  
COLUMN_ENTRY_PS(  
nOrdinal  
,   
nPrecision  
,   
nScale  
,   
data  
 )  
  
```  
  
#### パラメーター  
 *OLE DB Programmer's Reference*の [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) を参照してください。  
  
 `nOrdinal`  
 \[入力\] 列番号。  
  
 `nPrecision`  
 \[\]、バインドし列の最大の精度。  
  
 `nScale`  
 \[\]、バインドしたい列の小数点以下桁数。  
  
 `data`  
 \[\]ユーザー レコードと対応するデータ メンバー。  
  
## 解説  
 割り当て、バインドし列の有効桁数とスケールを指定できます。  これは、次の場所で使用されています:  
  
-   [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md) の [BEGIN\_COLUMN\_MAP](../Topic/BEGIN_COLUMN_MAP.md) とマクロ中。  
  
-   [END\_ACCESSOR](../Topic/END_ACCESSOR.md) の [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md) とマクロ中。  
  
-   [END\_PARAM\_MAP](../../data/oledb/end-param-map.md) の [BEGIN\_PARAM\_MAP](../Topic/BEGIN_PARAM_MAP.md) とマクロ中。  
  
## 必要条件  
 **ヘッダー:** atldbcli.h  
  
## 参照  
 [OLE DB コンシューマー テンプレート用マクロおよびグローバル関数](../Topic/Macros%20and%20Global%20Functions%20for%20OLE%20DB%20Consumer%20Templates.md)   
 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN\_COLUMN\_MAP](../Topic/BEGIN_COLUMN_MAP.md)   
 [COLUMN\_ENTRY](../../data/oledb/column-entry.md)   
 [COLUMN\_ENTRY\_EX](../../data/oledb/column-entry-ex.md)   
 [COLUMN\_ENTRY\_LENGTH](../../data/oledb/column-entry-length.md)   
 [COLUMN\_ENTRY\_PS\_LENGTH](../../data/oledb/column-entry-ps-length.md)   
 [COLUMN\_ENTRY\_LENGTH\_STATUS](../../data/oledb/column-entry-length-status.md)   
 [COLUMN\_ENTRY\_PS\_LENGTH\_STATUS](../Topic/COLUMN_ENTRY_PS_LENGTH_STATUS.md)   
 [COLUMN\_ENTRY\_STATUS](../../data/oledb/column-entry-status.md)   
 [COLUMN\_ENTRY\_PS\_STATUS](../Topic/COLUMN_ENTRY_PS_STATUS.md)   
 [END\_ACCESSOR](../Topic/END_ACCESSOR.md)   
 [END\_ACCESSOR\_MAP](../../data/oledb/end-accessor-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)