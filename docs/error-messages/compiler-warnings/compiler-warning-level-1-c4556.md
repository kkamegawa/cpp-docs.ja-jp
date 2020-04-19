---
title: コンパイラの警告 (レベル 1) C4556
ms.date: 08/27/2018
f1_keywords:
- C4556
helpviewer_keywords:
- C4556
ms.assetid: e4c0e296-b747-4db1-9608-30b8b74feac2
ms.openlocfilehash: c31602766261a8d6d0c4f0bb0a880ee34ee1ed45
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397316"
---
# <a name="compiler-warning-level-1-c4556"></a>コンパイラの警告 (レベル 1) C4556

> 組み込みイミディ エイト引数の値 '*値*'が範囲外です'*lowerbound* - *upperbound*'

## <a name="remarks"></a>Remarks

組み込み関数では、ハードウェア命令と一致します。 ハードウェアの命令では、固定数の定数をエンコードするビットがあります。 場合*値*が範囲外には正常にエンコードされません。 コンパイラでは、余分なビットが切り捨てられます。

## <a name="example"></a>例

次の例では、C4556 が生成されます。

```cpp
// C4556.cpp
// compile with: /W1
// processor: x86 IPF
#include <xmmintrin.h>

void test()
{
   __m64 m;
   _m_pextrw(m, 5);   // C4556
}

int main()
{
}
```