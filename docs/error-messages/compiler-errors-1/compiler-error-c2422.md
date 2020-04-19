---
title: コンパイラ エラー C2422
ms.date: 11/04/2016
f1_keywords:
- C2422
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
ms.openlocfilehash: 39f779ee846cf4f328f9c7af59ae394d97d7a3ca
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744733"
---
# <a name="compiler-error-c2422"></a>コンパイラ エラー C2422

' オペランド ' に無効なセグメントオーバーライドがあります。

インラインアセンブラーコードで、オペランドに対してセグメントオーバーライド演算子 (コロン) が誤って使用されています。  以下の原因が考えられます。

- 演算子の前のレジスタがセグメントレジスタではありません。

- 演算子の前のレジスタは、オペランドの唯一のセグメントレジスタではありません。

- セグメントのオーバーライド演算子は、間接演算子 (角かっこ) 内に出現します。

- セグメントオーバーライド演算子の後の式は、イミディエイトオペランドまたはメモリオペランドではありません。

次の例では、C2422 が生成されます。

```cpp
// C2422.cpp
// processor: x86
int main() {
   _asm {
      mov AX, [BX:ES]   // C2422
      mov AX, ES   // OK
   }
}
```
