---
title: "コンパイラ エラー C3024 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3024"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3024"
ms.assetid: 1c031c28-ce37-4de3-aead-cfe76b261856
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# コンパイラ エラー C3024
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'schedule\(runtime\)' : chunk\_size 式は使用できません  
  
 値をスケジュール句の実行時パラメーターに渡すことはできません。  
  
 次の例では C3024 が生成されます。  
  
```  
// C3024.cpp // compile with: /openmp /link vcomps.lib #include <stdio.h> #include "omp.h" int main() { int i; #pragma omp parallel for schedule(runtime, 10)   // C3024 for (i = 0; i < 10; ++i) ; #pragma omp parallel for schedule(runtime)   // OK for (i = 0; i < 10; ++i) ; }  
```