---
title: コンパイラエラー C2665
ms.date: 11/04/2016
f1_keywords:
- C2665
helpviewer_keywords:
- C2665
ms.assetid: a7f99b61-2eae-4f2b-ba75-ea68fd1e8312
ms.openlocfilehash: 95ca5ea846f9cd45bdb1e9706ae377589d37a285
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756020"
---
# <a name="compiler-error-c2665"></a>コンパイラエラー C2665

' function ': number1 オーバーロードは、パラメーター number2 を型 ' type ' から変換できません

オーバーロードされた関数のパラメーターは、必要な型に変換できません。  考えられる解決策は次のとおりです。

- 変換演算子を指定します。

- 明示的な変換を使用します。

## <a name="example"></a>使用例

次の例では、C2665 が生成されます。

```cpp
// C2665.cpp
void func(short, char*){}
void func(char*, char*){}

int main() {
   func(0, 1);   // C2665
   func((short)0, (char*)1);   // OK
}
```
