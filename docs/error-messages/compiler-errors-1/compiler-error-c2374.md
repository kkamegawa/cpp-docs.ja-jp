---
title: "コンパイラ エラー C2374 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2374"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2374"
ms.assetid: 73b51965-e91c-4e21-9732-f71c1449d22e
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# コンパイラ エラー C2374
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 再定義されています。2 回以上初期化されています  
  
 識別子が 2 回以上初期化されています。  
  
 次の例では C2374 が生成されます。  
  
```  
// C2374.cpp // compile with: /c int i = 0; int i = 1;   // C2374 int j = 1;   // OK  
```