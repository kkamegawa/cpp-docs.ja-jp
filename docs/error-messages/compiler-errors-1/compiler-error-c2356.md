---
title: コンパイラ エラー C2356
ms.date: 11/04/2016
f1_keywords:
- C2356
helpviewer_keywords:
- C2356
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
ms.openlocfilehash: e306c5a8f9175bc3c7902b20263aa2e451944182
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759933"
---
# <a name="compiler-error-c2356"></a>コンパイラ エラー C2356

翻訳単位で初期化セグメントを変更することはできません

次の原因が考えられます。

- セグメント初期化コードの前に `#pragma init_seg`

- 前に別の `#pragma init_seg` を `#pragma init_seg`

解決するには、セグメントの初期化コードをモジュールの先頭に移動します。 複数の領域を初期化する必要がある場合は、それらを別々のモジュールに移動します。

次の例では、C2356 が生成されます。

```cpp
// C2356.cpp
#pragma warning(disable : 4075)

int __cdecl myexit(void (__cdecl *)());
int __cdecl myexit2(void (__cdecl *)());

#pragma init_seg(".mine$m",myexit)
#pragma init_seg(".mine$m",myexit2)   // C2356
```
