---
title: "コンパイラ エラー C3175 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3175
dev_langs:
- C++
helpviewer_keywords:
- C3175
ms.assetid: 3f19d513-a05a-4b6c-806f-276fe5c36b90
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: 098a3c1fc910f28a2e3f7902c8a109adc5add710
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3175"></a>コンパイラ エラー C3175
'function1': 'function2' のアンマネージ関数からマネージ型のメソッドを呼び出すことはできません  
  
 アンマネージ関数には、マネージ クラスのメンバー関数を呼び出すことはできません。  
  
 次の例では、c3175 エラーが生成されます。  
  
```  
// C3175_2.cpp  
// compile with: /clr  
  
ref struct A {  
   static void func() {  
   }  
};  
  
#pragma unmanaged   // remove this line to resolve  
  
void func2() {  
   A::func();   // C3175  
}  
  
#pragma managed  
  
int main() {  
   A ^a = gcnew A;  
   func2();  
}  
```  
