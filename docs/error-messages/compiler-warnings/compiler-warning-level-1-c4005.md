---
title: コンパイラの警告 (レベル 1) C4005
ms.date: 11/04/2016
f1_keywords:
- C4005
helpviewer_keywords:
- C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
ms.openlocfilehash: 71b23ec719198d15a99b4fcfd50db8b151e03226
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627356"
---
# <a name="compiler-warning-level-1-c4005"></a>コンパイラの警告 (レベル 1) C4005

' identifier ': マクロの再定義

マクロ識別子は2回定義されます。 コンパイラは、2番目のマクロ定義を使用します。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>次のような原因をチェックして問題を解決するには

1. `#define` ディレクティブを使用して、コマンドラインとコードにマクロを定義します。

1. インクルードファイルからインポートされたマクロ。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>以下の可能性がある解決策を使って修正するには

1. 定義の1つを削除します。

1. 2番目の定義の前に[#undef](../../preprocessor/hash-undef-directive-c-cpp.md)ディレクティブを使用します。

次の例では、C4005 が生成されます。

```cpp
// C4005.cpp
// compile with: /W1 /EHsc
#include <iostream>
using namespace std;

#define TEST "test1"
#define TEST "test2"   // C4005 delete or rename to resolve the warning

int main() {
   cout << TEST << endl;
}
```