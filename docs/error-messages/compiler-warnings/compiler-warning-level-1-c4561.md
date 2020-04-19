---
title: コンパイラの警告 (レベル 1) C4561
ms.date: 11/04/2016
f1_keywords:
- C4561
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
ms.openlocfilehash: b0fd27142f0404a53fa2fee87fb2309e2f54d2c2
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965974"
---
# <a name="compiler-warning-level-1-c4561"></a>コンパイラの警告 (レベル 1) C4561

' __fastcall ' は '/clr ' オプションと互換性がありません: '\__stdcall ' に変換しています

[__Fastcall](../../cpp/fastcall.md)関数呼び出し規約を[/clr](../../build/reference/clr-common-language-runtime-compilation.md)コンパイラオプションと共に使用することはできません。 コンパイラは `__fastcall`の呼び出しを無視します。 この警告を解決するには、 **__fastcall**への呼び出しを削除するか、 **/clr**を指定せずにコンパイルします。

次の例では、C4561 が生成されます。

```cpp
// C4561.cpp
// compile with: /clr /W1 /c
// processor: x86
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve
```