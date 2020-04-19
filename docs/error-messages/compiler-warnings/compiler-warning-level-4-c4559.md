---
title: コンパイラの警告 (レベル 4) C4559
ms.date: 08/27/2018
f1_keywords:
- C4559
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
ms.openlocfilehash: afb4fb493c7c3e34ca691720a30d74517b0ab5b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62220877"
---
# <a name="compiler-warning-level-4-c4559"></a>コンパイラの警告 (レベル 4) C4559

> '*関数*': 再定義; 関数が _ _declspec (*修飾子*)

## <a name="remarks"></a>Remarks

2 番目の定義または宣言を追加し、関数が再定義または再宣言、 **_ _declspec**修飾子 (*修飾子*)。 これは、情報提供の警告です。 この警告を解決するには、定義を 1 つを削除します。

## <a name="example"></a>例

次の例では、C4559 が生成されます。

```cpp
// C4559.cpp
// compile with: /W4 /LD
void f();
__declspec(noalias) void f();   // C4559
```