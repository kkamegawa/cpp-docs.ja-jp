---
title: コンパイラの警告 (レベル 4) C4565
ms.date: 08/27/2018
f1_keywords:
- C4565
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
ms.openlocfilehash: b655dcfb456d32e45833e89e5a48926ad70d1d9e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62220482"
---
# <a name="compiler-warning-level-4-c4565"></a>コンパイラの警告 (レベル 4) C4565

> '*関数*': 再定義; シンボルが以前に宣言されたを _ _declspec (*修飾子*)

## <a name="remarks"></a>Remarks

2 番目の定義または宣言の最初の定義または宣言とは異なり、ありませんでしたし、シンボルが再定義または再宣言、`__declspec`修飾子 (*修飾子*)。 これは、情報提供の警告です。 この警告を解決するには、定義を 1 つを削除します。

## <a name="example"></a>例

次の例では、C4565 が生成されます。

```cpp
// C4565.cpp
// compile with: /W4 /LD
__declspec(noalias) void f();
void f();   // C4565
```