---
title: コンパイラの警告 (レベル 4) C4336
ms.date: 11/04/2016
f1_keywords:
- C4336
helpviewer_keywords:
- C4336
ms.assetid: 93f199dd-d6dd-42c0-82d8-c12d101a7235
ms.openlocfilehash: e83bac9028980bdf3ef7449fbef065a8c9316d2d
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991337"
---
# <a name="compiler-warning-level-4-c4336"></a>コンパイラの警告 (レベル 4) C4336

' type_lib2 ' をインポートする前に、クロス参照タイプライブラリ ' type_lib1 ' をインポートします

[#Import](../../preprocessor/hash-import-directive-cpp.md)ディレクティブを使用して、タイプライブラリが参照されました。 ただし、タイプライブラリには、`#import`で参照されていない別のタイプライブラリへの参照が含まれていました。 この他の .tlb ファイルは、コンパイラによって検出されました。

次の2つのファイルから作成されたディスク上の2つのタイプライブラリを指定します (midl でコンパイル)。

```
// c4336a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library c4336aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12c")]
   enum E_C4336
   {
      one, two, three
   };
};
```

2番目のタイプライブラリ:

```
// c4336b.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
library C4336bLib
{
   importlib ("c4336a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
   struct S_C4336
   {
      enum E_C4336 e;
   };
};
```

次の例では、C4336 が生成されます。

```cpp
// C4336.cpp
// compile with: /W4 /LD
// #import "C4336a.tlb"
#import "C4336b.tlb"   // C4336, uncomment previous line to resolve
```
