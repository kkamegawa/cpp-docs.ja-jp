---
title: コンパイラの警告 (レベル 2) C4150
ms.date: 11/04/2016
f1_keywords:
- C4150
helpviewer_keywords:
- C4150
ms.assetid: ff1760ec-0d9f-4d45-b797-94261624becf
ms.openlocfilehash: 5f55347dbe7843e67a3c6ef0ab83b91c8fa9d283
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052147"
---
# <a name="compiler-warning-level-2-c4150"></a>コンパイラの警告 (レベル 2) C4150

不完全な型 ' type ' へのポインターを削除しています。デストラクターが呼び出されません

**Delete**演算子は、宣言されているが定義されていない型を削除するために呼び出されます。そのため、コンパイラはデストラクターを見つけることができません。

次の例では、C4150 が生成されます。

```cpp
// C4150.cpp
// compile with: /W2
class  IncClass;

void NoDestruct( IncClass* pIncClass )
{
   delete pIncClass;
} // C4150, define class to resolve

int main()
{
}
```