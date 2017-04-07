---
title: "_CIatan2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CIatan2"
apilocation: 
  - "msvcr80.dll"
  - "msvcrt.dll"
  - "msvcr120.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr100.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "CIatan2"
  - "_CIatan2"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CIatan2 組み込み"
  - "CIatan2 組み込み"
ms.assetid: 31f8cc78-b79f-4576-b73b-8add18e08680
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# _CIatan2
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*x* と *y* がスタックの最上位の値である *x* \/ *y* のアークタンジェントを計算します。  
  
## 構文  
  
```  
void __cdecl _CIatan2();  
```  
  
## 解説  
 `atan2` 関数のこのバージョンにコンパイラが示すことがわかる特殊な呼び出し規約があります。  また、コピーは生成される高速化し、レジスタの割り当てとことを防ぐために実行されます。  
  
 結果値はスタックの上部に挿入されます。  
  
## 必要条件  
 **プラットフォーム:** x86  
  
## 参照  
 [関数リファレンス \(アルファベット順\)](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [atan、atanf、atanl、atan2、atan2f、atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)