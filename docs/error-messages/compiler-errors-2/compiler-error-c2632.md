---
title: コンパイラエラー C2632
ms.date: 11/04/2016
f1_keywords:
- C2632
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
ms.openlocfilehash: f69d43bf50f5f13957e49d1e9ffa798a3db5a7b3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754694"
---
# <a name="compiler-error-c2632"></a>コンパイラエラー C2632

' type1 ' の後に続く ' type1 ' は無効です

このエラーは、2つの型指定子の間にコードが欠落している場合に発生する可能性があります。

次の例では、C2632 が生成されます。

```cpp
// C2632.cpp
int float i;   // C2632
```

このエラーは、Visual Studio .NET 2003 で実行されたコンパイラ準拠作業の結果として生成されることもあります。 `bool` が適切な型になりました。 以前のバージョンでは、`bool` は typedef であり、その名前で識別子を作成することができました。

次の例では、C2632 が生成されます。

```cpp
// C2632_2.cpp
// compile with: /LD
void f(int bool);   // C2632
```

このエラーを解決して、visual Studio .NET 2003 と visual Studio .NET の両方のバージョンの Visual C++studio でコードが有効になるようにするには、識別子の名前を変更します。
