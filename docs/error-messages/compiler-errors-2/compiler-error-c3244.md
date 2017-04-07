---
title: "コンパイラ エラー C3244 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3244"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3244"
ms.assetid: dae6c49b-5212-4206-8f61-d4010c0b9969
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# コンパイラ エラー C3244
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'method': このメソッドは 'interface' によって \('interface' ではなく\) 導入されました  
  
 指定されたインターフェイスにはなく、別の基底クラスにあるメンバーを[明示的にオーバーライド](../../cpp/explicit-overrides-cpp.md)しようとしました。  
  
 次の例では C3244 が生成されます。  
  
```  
// C3244.cpp #pragma warning(disable:4199) __interface IX15A { void f(); }; __interface IX15B { void g(); }; class CX15 : public IX15A, public IX15B { public: void IX15A::f(); void IX15B::g(); }; void CX15::IX15A::g()   // C3244 occurs here { }  
```