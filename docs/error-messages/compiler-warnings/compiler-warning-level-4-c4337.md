---
title: コンパイラの警告 (レベル 4) C4337
ms.date: 11/04/2016
f1_keywords:
- C4337
helpviewer_keywords:
- C4337
ms.assetid: 70bc72d9-aac5-45cd-abd3-ebe42a05897b
ms.openlocfilehash: 5080c600e37468d5c3617769ddb4596a31be47f0
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991220"
---
# <a name="compiler-warning-level-4-c4337"></a>コンパイラの警告 (レベル 4) C4337

' typelib2 ' の相互参照タイプライブラリ ' typelib1 ' が自動的にインポートされています

[#Import ディレクティブ](../../preprocessor/hash-import-directive-cpp.md)の auto_search 属性により、タイプライブラリが暗黙的にインポートされました。

次の2つのファイルから作成されたディスク上の2つのタイプライブラリを指定します (midl でコンパイル)。

```
// C4337a.idl
[
  uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12B)
]
library C4337aLib
{
   [uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12C)]
   enum E_C4337a
   {
      one = 0,
      two = 1,
      three = 2
    };
};
```

次に、2番目の .idl ファイルを

```
// C4337b.idl
[
   uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12D)
]

library C4337bLib
{
   importlib("c4337a.tlb");

   [uuid(F87070BA-C6D9-405C-A8E4-8CD9CA25C12E)]
   struct S_C4337b
   {
      enum E_C4337a e;
   };
};
```

次の例では、C4337 が生成されます。

```cpp
// C4337.cpp
// compile with: /W4 /LD
#import "c4337b.tlb" auto_search   // C4337
// explicitly #import all type libraries to resolve
// #import "C4337a.tlb"
// #import "C4337b.tlb"
```
