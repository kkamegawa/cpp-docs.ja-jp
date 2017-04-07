---
title: "コンパイラの警告 (レベル 1) C4097 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4097"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4097"
ms.assetid: 2525be51-fac2-43b2-b57c-3bbf1a2268f7
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# コンパイラの警告 (レベル 1) C4097
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

プラグマ パラメーターに 'restore' または 'off' が必要です。  
  
 プラグマに無効な値が渡されました。  
  
 次の例では C4097 が生成されます。  
  
```  
// C4097.cpp // compile with: /W1 #pragma runtime_checks("",test)   // C4097 // try the following line instead // #pragma runtime_checks("",off) int main() { }  
```