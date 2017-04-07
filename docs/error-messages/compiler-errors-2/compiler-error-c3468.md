---
title: "コンパイラ エラー C3468 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3468"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3468"
ms.assetid: cfd320db-2f6e-4e0d-ba02-e79ece87e1e0
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# コンパイラ エラー C3468
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': 型は次のアセンブリにのみ転送できます:  
  
 '`file`' はアセンブリではありません  
  
 アセンブリ内の型のみを転送することができます。  
  
 詳細については、「[Type Forwarding \(C\+\+\/CLI\)](../../windows/type-forwarding-cpp-cli.md)」を参照してください。  
  
## 使用例  
 モジュールを作成する例を次に示します。  
  
```  
// C3468.cpp // compile with: /LN /clr public ref class R {};  
```  
  
## 使用例  
 次の例では C3468 が生成されます。  
  
```  
// C3468_b.cpp // compile with: /clr /c #using "C3468.netmodule" [ assembly:TypeForwardedTo(R::typeid) ];   // C3468  
```