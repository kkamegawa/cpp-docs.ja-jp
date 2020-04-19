---
title: コンパイラの警告 (レベル 1) C4228
ms.date: 11/04/2016
f1_keywords:
- C4228
helpviewer_keywords:
- C4228
ms.assetid: 9301d660-d601-464e-83f5-7ed844a3c6dc
ms.openlocfilehash: 75bd34a4338db7a430c1951d5bc3bd61dbce4f64
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627274"
---
# <a name="compiler-warning-level-1-c4228"></a>コンパイラの警告 (レベル 1) C4228

非標準の拡張機能が使用されています: 宣言子リストのコンマの後の修飾子は無視されます

変数の宣言時に、 **const**や `volatile` のような修飾子をコンマの後に使用することは、Microsoft 拡張機能 ([/ze](../../build/reference/za-ze-disable-language-extensions.md)) です。

## <a name="example"></a>例

```cpp
// C4228.cpp
// compile with: /W1
int j, const i = 0;  // C4228
int k;
int const m = 0;  // ok
int main()
{
}
```