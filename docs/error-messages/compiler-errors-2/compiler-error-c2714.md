---
title: コンパイラエラー C2714
ms.date: 11/04/2016
f1_keywords:
- C2714
helpviewer_keywords:
- C2714
ms.assetid: 401a5a42-660c-4bad-9d63-1a2d092bc489
ms.openlocfilehash: b5bfa56ca95cc93680c7eab227d658134b248976
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760557"
---
# <a name="compiler-error-c2714"></a>コンパイラエラー C2714

__alignof (void) は使用できません

演算子に無効な値が渡されました。

詳細については、「 [__Alignof 演算子](../../cpp/alignof-operator.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C2714 が生成されます。

```cpp
// C2714.cpp
int main() {
   return __alignof(void);   // C2714
   return __alignof(char);   // OK
}
```
