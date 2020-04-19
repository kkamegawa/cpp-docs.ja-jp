---
title: コンパイラの警告 (レベル 1) C4028
ms.date: 11/04/2016
f1_keywords:
- C4028
helpviewer_keywords:
- C4028
ms.assetid: c3e8b70b-e870-416c-a285-bba5f71dbfc6
ms.openlocfilehash: 19bfd2659ee9017d3a304dee2d647da091515876
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623852"
---
# <a name="compiler-warning-level-1-c4028"></a>コンパイラの警告 (レベル 1) C4028

仮パラメーター ' number ' が宣言と異なります。

仮パラメーターの型が、宣言内の対応するパラメーターと一致しません。 元の宣言の型が使用されます。

この警告は、C ソースコードに対してのみ有効です。

## <a name="example"></a>例

次の例では、C4028 が生成されます。

```c
// C4028.c
// compile with: /W1 /Za
void f(int , ...);
void f(int i, int j) {}   // C4028

void g(int , int);
void g(int i, int j) {}   // OK

int main() {}
```