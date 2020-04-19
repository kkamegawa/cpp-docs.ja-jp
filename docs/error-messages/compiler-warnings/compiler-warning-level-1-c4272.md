---
title: コンパイラの警告 (レベル 1) C4272
ms.date: 11/04/2016
f1_keywords:
- C4272
helpviewer_keywords:
- C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
ms.openlocfilehash: 13c56c2261cd069e7edec63921c198e2bee56c95
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626692"
---
# <a name="compiler-warning-level-1-c4272"></a>コンパイラの警告 (レベル 1) C4272

' function ': __declspec (dllimport) とマークされています。関数をインポートするときは、ネイティブ呼び出し規約を指定する必要があります。

[__Clrcall](../../cpp/clrcall.md)呼び出し規約でマークされた関数をエクスポートするとエラーになります。 `__clrcall`とマークされた関数をインポートしようとすると、コンパイラはこの警告を発行します。

次の例では、C4272 が生成されます。

```cpp
// C4272.cpp
// compile with: /c /W1 /clr
__declspec(dllimport) void __clrcall Test();   // C4272
__declspec(dllimport) void Test2();   // OK
```