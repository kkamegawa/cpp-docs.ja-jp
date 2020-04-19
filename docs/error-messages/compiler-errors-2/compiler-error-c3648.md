---
title: コンパイラ エラー C3648
ms.date: 11/04/2016
f1_keywords:
- C3648
helpviewer_keywords:
- C3648
ms.assetid: 5d042989-41cb-4cd0-aa50-976b70146aaf
ms.openlocfilehash: 3b26be9890bbbdf6276c61023e6867160528e236
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751834"
---
# <a name="compiler-error-c3648"></a>コンパイラ エラー C3648

この明示的なオーバーライド構文には/clr: oldSyntax が必要です

最新のマネージ構文に対してコンパイルする場合、サポートされなくなった以前のバージョンの明示的なオーバーライド構文がコンパイラによって検出されました。

詳細については、「[明示的なオーバーライド](../../extensions/explicit-overrides-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C3648 が生成されます。

```cpp
// C3648.cpp
// compile with: /clr
public interface struct I {
   void f();
};

public ref struct R : I {
   virtual void I::f() {}   // C3648
   // try the following line instead
   // virtual void f() = I::f{}
};
```
