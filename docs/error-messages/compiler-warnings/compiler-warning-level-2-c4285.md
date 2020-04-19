---
title: コンパイラの警告 (レベル 2) C4285
ms.date: 11/04/2016
f1_keywords:
- C4285
helpviewer_keywords:
- C4285
ms.assetid: fa14de1f-fc19-4eec-8bea-81003636e12f
ms.openlocfilehash: 326b73dcf4665c442926e68995bace60300b6ebf
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052100"
---
# <a name="compiler-warning-level-2-c4285"></a>コンパイラの警告 (レベル 2) C4285

挿入辞表記を使用して適用された場合、' identifier:: operator-> ' の戻り値の型は再帰的です

指定された**operator-> ()** 関数は、定義されている型、またはそれが定義されている型への参照を返すことができません。

次の例では、C4285 が生成されます。

```cpp
// C4285.cpp
// compile with: /W2
class C
{
public:
    C operator->();   // C4285
   // C& operator->();  C4285, also
};

int main()
{
}
```