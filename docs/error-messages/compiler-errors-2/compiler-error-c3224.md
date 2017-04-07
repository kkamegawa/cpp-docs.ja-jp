---
title: "コンパイラ エラー C3224 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3224"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3224"
ms.assetid: 129be22f-8f3e-4fc6-9ccd-d27d8ef91251
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# コンパイラ エラー C3224
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': オーバーロードされたジェネリック クラスには、'number' ジェネリック型引数を指定できません  
  
 コンパイラは、適切なオーバーロードを見つけることができませんでした。  
  
 次の例では C3224 が生成されます。  
  
```  
// C3224.cs // compile with: /target:library public class C<T> {} public class C<T,U> {}  
```  
  
 この場合、次のようになります。  
  
```  
// C3224b.cpp // compile with: /clr #using "C3224.dll" int main() { C<int,int,int>^ c = gcnew C<int,int,int>();   // C3224 C<int,int>^ c2 = gcnew C<int,int>();   // OK }  
```