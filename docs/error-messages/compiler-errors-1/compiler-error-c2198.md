---
title: コンパイラ エラー C2198
ms.date: 11/04/2016
f1_keywords:
- C2198
helpviewer_keywords:
- C2198
ms.assetid: 638a845c-9d7f-4115-a9aa-d72455605668
ms.openlocfilehash: cbe4f95037aabf3b4febc1a8fff5a324773a33b4
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301835"
---
# <a name="compiler-error-c2198"></a>コンパイラ エラー C2198

'function' : 呼び出しに対する引数が少なすぎます。

コンパイラで検出された関数を呼び出すためのパラメーターが少なすぎるか、または関数宣言が正しくありません。

次の例では C2198 が生成されます。

```c
// C2198.c
// compile with: /c
void func( int, int );
int main() {
   func( 1 );   // C2198 only one actual parameter
   func( 1, 1 );   // OK
}
```
