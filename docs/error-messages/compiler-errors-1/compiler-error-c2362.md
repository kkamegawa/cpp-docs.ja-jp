---
title: コンパイラ エラー C2362
ms.date: 06/03/2019
f1_keywords:
- C2362
helpviewer_keywords:
- C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
ms.openlocfilehash: d48806982bbb6cdda4d29e47f6692e7e3601d6de
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503213"
---
# <a name="compiler-error-c2362"></a>コンパイラ エラー C2362

> 初期化 '*識別子*' の初期化が ' goto*ラベル*'

使用してコンパイルされるときに[/Za](../../build/reference/za-ze-disable-language-extensions.md)ラベルにジャンプ先から初期化される識別子をできないようにします。

宣言が入力されていないブロックで囲まれている場合、または変数は既に初期化されている場合、初期化子を含む宣言のみ移動できます。

次の例では、C2362 が生成されます。

```cpp
// C2362.cpp
// compile with: /Za
int main() {
   goto label1;
   int i = 1;      // C2362, initialization skipped
label1:;
}
```

考えられる解決方法:

```cpp
// C2362b.cpp
// compile with: /Za
int main() {
   goto label1;
   {
      int j = 1;   // OK, this block is never entered
   }
label1:;
}
```