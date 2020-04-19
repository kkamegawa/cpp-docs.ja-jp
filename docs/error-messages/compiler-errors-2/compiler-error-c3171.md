---
title: コンパイラエラー C3171
ms.date: 11/04/2016
f1_keywords:
- C3171
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
ms.openlocfilehash: a3af19fa6b4f4def9bb42325f648109cfafcdaef
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761752"
---
# <a name="compiler-error-c3171"></a>コンパイラエラー C3171

' module ': プロジェクトで異なるモジュール属性を指定することはできません

異なるパラメーターリストを持つ[モジュール](../../windows/module-cpp.md)属性が、コンパイルの2つのファイルに見つかりました。 コンパイルごとに指定できる一意の `module` 属性は1つだけです。

同一の `module` 属性は、複数のソースコードファイルで指定できます。

たとえば、次の `module` 属性が見つかったとします。

```cpp
// C3171.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.0") ];
int main() {}
```

この場合、次のようになります。

```cpp
// C3171b.cpp
// compile with: C3171.cpp
// C3171 expected
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.1") ];
```

コンパイラは C3171 を生成します (異なるバージョンの値に注意してください)。
