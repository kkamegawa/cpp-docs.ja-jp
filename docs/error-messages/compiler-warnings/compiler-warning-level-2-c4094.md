---
title: コンパイラの警告 (レベル 2) C4094
ms.date: 11/04/2016
f1_keywords:
- C4094
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
ms.openlocfilehash: c293522e5d60d0edb4cc2da289e0ece71f89329f
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052200"
---
# <a name="compiler-warning-level-2-c4094"></a>コンパイラの警告 (レベル 2) C4094

タグなしの ' token ' はシンボルを宣言しませんでした

コンパイラは、タグなしの構造体、共用体、またはクラスを使用して空の宣言を検出しました。 宣言は無視されます。

## <a name="example"></a>例

```cpp
// C4094.cpp
// compile with: /W2
struct
{
};   // C4094

int main()
{
}
```

この条件により、ANSI 互換 ([/za](../../build/reference/za-ze-disable-language-extensions.md)) でエラーが生成されます。