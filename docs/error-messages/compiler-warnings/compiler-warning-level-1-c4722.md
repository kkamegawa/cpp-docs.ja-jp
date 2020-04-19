---
title: コンパイラの警告 (レベル 1) C4722
ms.date: 11/04/2016
f1_keywords:
- C4722
helpviewer_keywords:
- C4722
ms.assetid: d8660710-f67b-4f59-a5fd-59259475529e
ms.openlocfilehash: 85921d67b764a28f9251f0c8b6e3fc807edd0f5b
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052450"
---
# <a name="compiler-warning-level-1-c4722"></a>コンパイラの警告 (レベル 1) C4722

'function': デストラクターに値が戻りません。メモリ リークの可能性があります

制御フローは、デストラクターで終了します。 スレッドまたはプログラム全体が終了し、割り当てられたリソースが解放されていない可能性があります。  さらに、例外の処理中にスタック アンワインドのためにデストラクターを呼び出す場合、実行可能ファイルの動作は未定義です。

解決するには、デストラクターが制御を戻さない原因となった関数呼び出しを削除します。

## <a name="example"></a>例

次の例では C4722 が生成されます。

```cpp
// C4722.cpp
// compile with: /O1 /W1 /c
#include <stdlib.h>
class C {
public:
   C();
   ~C() { exit(1); };   // C4722
};

extern void func (C*);

void Test(){
   C x;
   func(&x);
   // control will not leave Test because destructor will exit
}
```