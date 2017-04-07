---
title: "致命的なエラー C1022 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1022"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1022"
ms.assetid: edada720-dc73-49bc-bd93-a7945a316312
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 致命的なエラー C1022
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#endif が必要です。  
  
 `#if`、`#ifdef`、`#ifndef` の各ディレクティブに対応する `#endif` ディレクティブがありません。 各 `#if`、`#ifdef`、`#ifndef` に対応する `#endif` を指定してください。  
  
 次の例では C1022 が生成されます。  
  
```  
// C1022.cpp #define true 1 #if (true) #else #else    // C1022  
```  
  
 考えられる解決策:  
  
```  
// C1022b.cpp // compile with: /c #define true 1 #if (true) #else #endif  
```