---
title: コンパイラの警告 (レベル 1) C4688
ms.date: 11/04/2016
f1_keywords:
- C4688
helpviewer_keywords:
- C4688
ms.assetid: a027df3c-b2b8-4c49-8539-c2bc42db74e8
ms.openlocfilehash: bc869b7e22bc8bce0230892dc9a67d6aaec09f46
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052502"
---
# <a name="compiler-warning-level-1-c4688"></a>コンパイラの警告 (レベル 1) C4688

'constraint': 制約リストはアセンブリ プライベート型 'type' を含んでいます

制約リストにアセンブリ プライベート型があります。つまり、型にアセンブリの外部からアクセスする場合は、このリストを使用できません。 詳細については、「[ジェネリック](../../extensions/generics-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>例

次の例では C4688 警告が生成されます。

```cpp
// C4688.cpp
// compile with: /clr /c /W1
ref struct A {};   // private type
public ref struct B {};

// Delete the following 3 lines to resolve.
generic <class T>
where T : A   // C4688
public ref struct M {};

generic <class T>
where T : B
public ref struct N {};
```