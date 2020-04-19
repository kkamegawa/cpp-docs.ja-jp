---
title: コンパイラ エラー C3615
ms.date: 10/24/2017
f1_keywords:
- C3615
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
ms.openlocfilehash: e966295b5ab63350828ddb73d6791a9e30bb5c59
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404105"
---
# <a name="compiler-error-c3615"></a>コンパイラ エラー C3615

> constexpr 関数 '*関数*' 定数式で発生することはできません

関数は、*関数*として評価できませんでした`constexpr`コンパイル時にします。 ある`constexpr`、関数の呼び出すことができますのみ`constexpr`関数。

## <a name="example"></a>例

Visual Studio 2017 が正しく評価する条件付きで操作の左側のオペランドがで有効でないときに、エラーが発生する`constexpr`コンテキスト。 次のコードは、Visual Studio 2017 ではなく Visual Studio 2015 でコンパイルします。

```cpp
// C3615.cpp
// Compile with: /c

template<int N>
struct myarray
{
    int size() const { return N; }
};

constexpr bool f(const myarray<1> &arr)
{
    return arr.size() == 10 || arr.size() == 11; // C3615 starting in Visual Studio 2017
}
```

この問題を解決するいずれかを宣言、`array::size()`として機能`constexpr`または削除、`constexpr`から修飾子`f`します。