---
title: コンパイラ エラー C3533
ms.date: 11/04/2016
f1_keywords:
- C3533
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
ms.openlocfilehash: ce95bba417e9be3603f15376a0fd65a48f951a2f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755643"
---
# <a name="compiler-error-c3533"></a>コンパイラ エラー C3533

' type ': パラメーターに ' auto ' を含む型を指定することはできません

既定の[/zc: auto](../../build/reference/zc-auto-deduce-variable-type.md)コンパイラオプションが有効になっている場合、メソッドまたはテンプレートパラメーターを `auto` キーワードで宣言することはできません。

### <a name="to-correct-this-error"></a>このエラーを解決するには

1. パラメーター宣言から `auto` キーワードを削除します。

## <a name="example"></a>使用例

次の例では、`auto` キーワードを使用して関数パラメーターを宣言し、 **/zc: auto**を指定してコンパイルするため、C3533 が生成されます。

```cpp
// C3533a.cpp
// Compile with /Zc:auto
void f(auto j) {} // C3533
```

## <a name="example"></a>使用例

次の例では、C3533 キーワードを `auto` 使用してテンプレートパラメーターを宣言し、 **/zc: auto**を指定してコンパイルするため、c++ 14 モードでが生成されます。(C++ 17 では、これは、型が推測される単一の非型テンプレートパラメーターを持つクラステンプレートの有効な定義です)。

```cpp
// C3533b.cpp
// Compile with /Zc:auto
template<auto T> class C {}; // C3533
```

## <a name="see-also"></a>参照

[auto キーワード](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (変数の型の推測)](../../build/reference/zc-auto-deduce-variable-type.md)
