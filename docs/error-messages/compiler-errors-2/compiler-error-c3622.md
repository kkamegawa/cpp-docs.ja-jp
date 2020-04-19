---
title: コンパイラ エラー C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: 2adcee4cb20c39c39b06e0ac2087478cfe2d8937
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740898"
---
# <a name="compiler-error-c3622"></a>コンパイラ エラー C3622

' class ': ' keyword ' として宣言されたクラスはインスタンス化できません

[Abstract](../../extensions/abstract-cpp-component-extensions.md)としてマークされたクラスのインスタンスを作成しようとしました。 `abstract` としてマークされたクラスは基底クラスにすることができますが、インスタンス化することはできません。

## <a name="example"></a>使用例

次の例では、C3622 が生成されます。

```cpp
// C3622.cpp
// compile with: /clr
ref class a abstract {};

int main() {
   a aa;   // C3622
}
```
