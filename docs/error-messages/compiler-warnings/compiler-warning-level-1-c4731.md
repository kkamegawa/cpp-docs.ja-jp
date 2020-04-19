---
title: コンパイラの警告 (レベル 1) C4731
ms.date: 11/04/2016
f1_keywords:
- C4731
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
ms.openlocfilehash: b2591756dfaa8887affbe4e470f1c98738b6b680
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052427"
---
# <a name="compiler-warning-level-1-c4731"></a>コンパイラの警告 (レベル 1) C4731

' pointer ': インラインアセンブリコードによって変更されたフレームポインターレジスタ ' register '

フレームポインターレジスタが変更されました。 インラインアセンブリブロックまたはフレーム変数 (変更されたレジスタに応じてローカルまたはパラメーター) に登録を保存して復元する必要があります。または、コードが正しく機能しない可能性があります。

次の例では、C4731 が生成されます。

```cpp
// C4731.cpp
// compile with: /W1 /LD
// processor: x86
// C4731 expected
void bad(int p) {
   __asm
   {
      mov ebp, 1
   }

   if (p == 1)
   {
      // ...
   }
}
```

EBP はフレームポインターです (FPO は許可されていません)。変更されています。 `p` が後で参照されると、`EBP`に対して相対的に参照されます。 ただし、`EBP` はコードによって上書きされているため、プログラムが正常に動作せず、エラーが発生する可能性もあります。