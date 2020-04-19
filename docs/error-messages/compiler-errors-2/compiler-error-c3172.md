---
title: コンパイラエラー C3172
ms.date: 11/04/2016
f1_keywords:
- C3172
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
ms.openlocfilehash: 1da2676d660d23e3fb71b56263779b1f1edacbf9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761739"
---
# <a name="compiler-error-c3172"></a>コンパイラエラー C3172

' module_name ': プロジェクトで異なる idl_module 属性を指定することはできません

同じ名前で `dllname` または `version` パラメーターが異なる[idl_module](../../windows/idl-module.md)属性が、コンパイルの2つのファイルに見つかりました。 コンパイルごとに指定できる一意の `idl_module` 属性は1つだけです。

同一の `idl_module` 属性は、複数のソースコードファイルで指定できます。

たとえば、次の `idl_module` 属性が見つかったとします。

```cpp
// C3172.cpp
[module(name="MyMod")];
[ idl_module(name="x", dllname="file.dll", version="1.1") ];
int main() {}
```

この場合、次のようになります。

```cpp
// C3172b.cpp
// compile with: C3172.cpp
// C3172 expected
[ idl_module(name="x", dllname="file.dll", version="1.0") ];
```

コンパイラは C3172 を生成します (異なるバージョンの値に注意してください)。
