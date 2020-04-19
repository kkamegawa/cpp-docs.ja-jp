---
title: コンパイラエラー C3170
ms.date: 11/04/2016
f1_keywords:
- C3170
helpviewer_keywords:
- C3170
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
ms.openlocfilehash: e2d74a637e2902fcf636b49068882f32aa706f94
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761765"
---
# <a name="compiler-error-c3170"></a>コンパイラエラー C3170

プロジェクト内で異なるモジュール識別子を持つことはできません

異なる名前の[モジュール](../../windows/module-cpp.md)属性が、コンパイルの2つのファイルに見つかりました。 コンパイルごとに指定できる一意の `module` 属性は1つだけです。

同一の `module` 属性は、複数のソースコードファイルで指定できます。

たとえば、次のモジュール属性が見つかったとします。

```cpp
// C3170.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
int main() {}
```

この場合、次のようになります。

```cpp
// C3170b.cpp
// compile with: C3170.cpp
// C3170 expected
[ module(name="MyModule1", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
```

コンパイラは C3170 を生成します (異なる名前に注意してください)。
