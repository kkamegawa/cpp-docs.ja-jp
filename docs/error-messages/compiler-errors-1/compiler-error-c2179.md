---
title: "コンパイラ エラー C2179 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2179"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2179"
ms.assetid: f929bfc6-3964-4e54-87d6-7529b9b6c0b9
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# コンパイラ エラー C2179
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'型' : 属性引数は型パラメーターを使用することはできません。  
  
 ジェネリック型のパラメーターは実行時に解決されます。  しかし、属性パラメーターはコンパイル時に解決する必要があります。  このため、ジェネリック型のパラメーターを属性への引数として使用することはできません。  
  
## 使用例  
 次の例では C2179 エラーが生成されます。  
  
```  
// C2179.cpp  
// compile with: /clr  
using namespace System;  
  
public ref struct Attr : Attribute {  
   Attr(Type ^ a) {  
      x = a;  
   }  
  
   Type ^ x;  
};  
  
ref struct G {};  
  
generic<typename T>   
public ref class Z {   
public:  
   Type ^ d;  
   [Attr(T::typeid)]   // C2179  
   // try the following line instead  
   // [Attr(G::typeid)]  
   T t;  
};  
```