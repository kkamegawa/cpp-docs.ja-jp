---
title: コンパイラの警告 (レベル 1) C4353
ms.date: 11/04/2016
f1_keywords:
- C4353
helpviewer_keywords:
- C4353
ms.assetid: 6e79f186-ed82-4c95-9923-0ad5bb9c4db1
ms.openlocfilehash: f04bc78e1ff6183208f888d9072bfe90b3aca083
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966544"
---
# <a name="compiler-warning-level-1-c4353"></a>コンパイラの警告 (レベル 1) C4353

非標準の拡張機能が使用されています: 定数0が関数式です。 代わりに ' __noop ' 関数を使用してください

定数ゼロ (0) を関数式として使用することはできません。 詳細については、「 [__noop](../../intrinsics/noop.md)」を参照してください。

次の例では、C4353 が生成されます。

```cpp
// C4353.cpp
// compile with: /W1
void MyPrintf(void){};
#define X 0
#if X
   #define DBPRINT MyPrint
#else
   #define DBPRINT 0   // C4353 expected
#endif
int main(){
DBPRINT();
}
```