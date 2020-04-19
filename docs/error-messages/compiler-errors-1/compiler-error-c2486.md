---
title: コンパイラ エラー C2486
ms.date: 11/04/2016
f1_keywords:
- C2486
helpviewer_keywords:
- C2486
ms.assetid: 436da349-6461-4e32-bfca-4f3e620108e2
ms.openlocfilehash: 75705bd8ecc850839e22fccbed1abf08687b3823
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743511"
---
# <a name="compiler-error-c2486"></a>コンパイラ エラー C2486

' __LOCAL_SIZE ' は、' 生 ' 属性を持つ関数でのみ許可されています

インラインアセンブリ関数では、`__LOCAL_SIZE` 名前は、[生](../../cpp/naked-cpp.md)の属性を使用して宣言された関数用に予約されています。

次の例では、C2486 が生成されます。

```cpp
// C2486.cpp
// processor: x86
void __declspec(naked) f1() {
   __asm {
      mov   eax,   __LOCAL_SIZE
   }
}
void f2() {
   __asm {
      mov   eax,   __LOCAL_SIZE   // C2486
   }
}
```
