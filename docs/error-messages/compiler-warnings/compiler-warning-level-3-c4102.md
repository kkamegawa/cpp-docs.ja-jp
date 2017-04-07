---
title: "コンパイラの警告 (レベル 3) C4102 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4102"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4102"
ms.assetid: 349f308a-daf3-48c6-bd53-6c38b73f8880
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# コンパイラの警告 (レベル 3) C4102
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'label': 参照されていないラベル  
  
 ラベルが定義されていますが、一度も参照されていません。 コンパイラはこのラベルを無視します。  
  
 次の例では C4102 警告が生成されます。  
  
```  
// C4102.cpp // compile with: /W3 int main() { int a; test:   // C4102, remove the unreferenced label to resolve a = 1; }  
```