---
title: コンパイラ エラー C3510
ms.date: 11/04/2016
f1_keywords:
- C3510
helpviewer_keywords:
- C3510
ms.assetid: c48387bc-0300-4a4d-97f7-3fb90f82a451
ms.openlocfilehash: 3f9dea77b739aa59474e60cf852fff2577ab6ba9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753628"
---
# <a name="compiler-error-c3510"></a>コンパイラ エラー C3510

依存タイプライブラリ ' type_lib ' が見つかりません

[no_registry](../../preprocessor/no-registry.md)と[auto_search](../../preprocessor/auto-search.md)は `#import` に渡されましたが、コンパイラは参照されているタイプライブラリを見つけることができませんでした。

このエラーを解決するには、すべてのタイプライブラリと参照されるタイプライブラリがコンパイラで使用可能であることを確認します。

次の例では、C3510 が生成されます。

次の2つのタイプライブラリがビルドされ、パスで C3510a が削除されたものとします。

```
// C3510a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library C3510aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12c")]
   enum E_C3510
   {
      one, two, three
   };
};
```

次に、2番目のタイプライブラリのソースコードを次に示します。

```
// C3510b.idl
// post-build command: del /f C3510a.tlb
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
library C3510bLib
{
   importlib ("C3510a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
   struct S_C3510 {
      enum E_C3510 e;
   };
};
```

次に、クライアントコードを次に示します。

```cpp
// C3510.cpp
#import "c3510b.tlb" no_registry auto_search   // C3510
int main() {
   C3510aLib::S_C4336 ccc;
}
```
