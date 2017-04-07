---
title: "致命的なエラー C1310 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1310"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1310"
ms.assetid: ac48aa51-8023-42fe-b844-3f8bf228fbef
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 致命的なエラー C1310
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ガイド付き最適化のプロファイルは OpenMP と共に使用できません  
  
 [\/GL](../../build/reference/gl-whole-program-optimization.md) を使用してコンパイルしたモジュールを [\/LTCG:PGI](../../build/reference/ltcg-link-time-code-generation.md) でリンクさせることはできません。  
  
 次の例では C1310 が生成されます。  
  
```  
// C1310.cpp // compile with: /openmp /GL /link /LTCG:PGI // C1310 expected int main() { int i = 0, j = 10; #pragma omp parallel { #pragma omp for for (i = 0; i < 0; i++) --j; } }  
```