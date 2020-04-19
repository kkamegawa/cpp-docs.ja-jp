---
title: コンパイラの警告 (レベル 1) C4546
ms.date: 11/04/2016
f1_keywords:
- C4546
helpviewer_keywords:
- C4546
ms.assetid: 071e1709-3841-46c1-8e71-96109cd22041
ms.openlocfilehash: 7c2e47b92050bb83b1f55836e633d9749bb5e309
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966419"
---
# <a name="compiler-warning-level-1-c4546"></a>コンパイラの警告 (レベル 1) C4546

コンマの前の関数呼び出しに引数一覧がありません。

コンパイラにより、正しくない形式のコンマ式が検出されました。

既定では、この警告はオフに設定されています。 詳細については、「 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)」を参照してください。

## <a name="example"></a>例

次の例では、C4546 が生成されます。

```cpp
// C4546.cpp
// compile with: /W1
#pragma warning (default : 4546)
void f(int i) {
   i++;
}

int main() {
   int i = 0, k = 0;

   if ( f, k )   // C4546
   // try the following line instead
   // if ( f(i), k )
      i++;
}
```