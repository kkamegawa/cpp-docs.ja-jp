---
title: "コンパイラの警告 (レベル 3) C4637 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4637"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4637"
ms.assetid: 5fd347c1-2de9-408f-9136-1bf1ff273622
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# コンパイラの警告 (レベル 3) C4637
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

XML ドキュメント コメント ターゲット: \<include\> タグは破棄されました。  理由  
  
 [\<include\>](../../ide/include-visual-cpp.md) タグの構文が正しくありません。  
  
 次の例では C4637 警告が生成されます。  
  
```  
// C4637.cpp // compile with: /clr /doc /LD /W3 using namespace System; /// Text for class MyClass. public ref class MyClass { public: /// <include file="c:\davedata\jtest\xml_include.doc"/> // Try the following line instead: // /// <include file='xml_include.doc' path='MyDocs/MyMembers/*' /> void MyMethod() { } };   // C4637  
```