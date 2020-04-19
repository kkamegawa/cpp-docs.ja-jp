---
title: コンパイラの警告 (レベル 1) C4033
ms.date: 11/04/2016
f1_keywords:
- C4033
helpviewer_keywords:
- C4033
ms.assetid: 189a9ec3-ff6d-49dd-b9b2-530b28bbb7c9
ms.openlocfilehash: 740be5fa45d0cd332cc7ac6b62a983ce00d05a8f
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623740"
---
# <a name="compiler-warning-level-1-c4033"></a>コンパイラの警告 (レベル 1) C4033

'function': 値を返さなければいけません

この関数は値を返しません。 定義されていない値が返されます。

戻り値のない `return` を使用する関数は、型 `void`として宣言する必要があります。

このエラーは、C 言語コード用です。

次の例では C4033 が生成されます。

```c
// C4033.c
// compile with: /W1 /LD
int test_1(int x)   // C4033 expected
{
   if (x)
   {
      return;   // C4033
   }
}
```