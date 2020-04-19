---
title: コンパイラの警告 (レベル 1) C4326
ms.date: 08/27/2018
f1_keywords:
- C4326
helpviewer_keywords:
- C4326
ms.assetid: d44d2c4e-9456-42d3-b35b-4ba4b2d42ec7
ms.openlocfilehash: d14a1902db4dcf2224ce6a58db120a81ebb5620f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327354"
---
# <a name="compiler-warning-level-1-c4326"></a>コンパイラの警告 (レベル 1) C4326

> 型を返す '*関数*'は'*type1*' の代わりに '*type2*'

## <a name="remarks"></a>Remarks

返される型を以外の関数*type1*します。 たとえばを使用して[/Za](../../build/reference/za-ze-disable-language-extensions.md)、**メイン**を返しませんでした、 **int**。

## <a name="example"></a>例

次の例では、C4326 を生成し、その修正方法を示しています。

```cpp
// C4326.cpp
// compile with: /Za /W1
char main()
{
    // C4326, instead use int main()
}
```