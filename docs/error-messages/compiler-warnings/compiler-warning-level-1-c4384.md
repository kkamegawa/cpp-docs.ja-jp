---
title: コンパイラの警告 (レベル 1) C4384
ms.date: 11/04/2016
f1_keywords:
- C4384
helpviewer_keywords:
- C4384
ms.assetid: fafa8eb2-cbfc-4edb-8b0f-511ff5d37ac0
ms.openlocfilehash: 467f15522503d16d3b023661ee339c986f74ddec
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73964884"
---
# <a name="compiler-warning-level-1-c4384"></a>コンパイラの警告 (レベル 1) C4384

\#プラグマ ' make_public ' はグローバルスコープでのみ使用する必要があります

[Make_public](../../preprocessor/make-public.md)プラグマが正しく適用されませんでした。

## <a name="example"></a>例

次の例では、C4384 が生成されます。

```cpp
// C4384.cpp
// compile with: /c /W1
namespace n {
   #pragma make_public(N::C)   // C4384
   namespace N {
      class C {};
   }
}
```