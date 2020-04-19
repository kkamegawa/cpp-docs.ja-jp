---
title: コンパイラの警告 (レベル 1) C4286
ms.date: 11/04/2016
f1_keywords:
- C4286
helpviewer_keywords:
- C4286
ms.assetid: 93eadd6c-6f36-413b-ba91-c9aa2314685a
ms.openlocfilehash: ed2e6c10e35e53c6a67de9fecfce5da5ae429b93
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626664"
---
# <a name="compiler-warning-level-1-c4286"></a>コンパイラの警告 (レベル 1) C4286

' type1 ': 行番号の基底クラス (' type1 ') によってキャッチされました

指定された例外の種類は、前のハンドラーによって処理されます。 2番目の catch の型は、最初のの型から派生します。 基底クラスの例外は、派生クラスの例外をキャッチします。

## <a name="example"></a>例

```cpp
//C4286.cpp
// compile with: /W1
#include <eh.h>
class C {};
class D : public  C {};
int main()
{
    try
    {
        throw "ooops!";
    }
    catch( C ) {}
    catch( D ) {}  // warning C4286, D is derived from C
}
```