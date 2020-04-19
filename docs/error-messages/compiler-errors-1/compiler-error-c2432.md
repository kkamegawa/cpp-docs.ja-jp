---
title: コンパイラ エラー C2432
ms.date: 11/04/2016
f1_keywords:
- C2432
helpviewer_keywords:
- C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
ms.openlocfilehash: d4234626bc246d6da87be68b03d44562dd5990ff
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744512"
---
# <a name="compiler-error-c2432"></a>コンパイラ エラー C2432

' identifier ' の16ビットデータへの無効な参照です

16ビットレジスタは、インデックスまたはベースレジスタとして使用されます。 コンパイラは、16ビットデータの参照をサポートしていません。 32ビットコードをコンパイルするときに、16ビットレジスタをインデックスまたは基本レジスタとして使用することはできません。

次の例では、C2432 が生成されます。

```cpp
// C2432.cpp
// processor: x86
int main() {
   _asm mov eax, DWORD PTR [bx]   // C2432
}
```
