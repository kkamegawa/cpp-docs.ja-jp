---
title: コンパイラ エラー C2498
ms.date: 11/04/2016
f1_keywords:
- C2498
helpviewer_keywords:
- C2498
ms.assetid: 0839f12c-aaa4-4a02-bb33-7f072715dd14
ms.openlocfilehash: 2b6f6469a221c914e0eef9e190c79a2b2706e651
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756995"
---
# <a name="compiler-error-c2498"></a>コンパイラ エラー C2498

' function ': ' novtable ' は、クラス宣言または定義にのみ適用できます

このエラーは、関数で `__declspec(novtable)` を使用することによって発生することがあります。

## <a name="example"></a>使用例

次の例では、C2498 が生成されます。

```cpp
// C2498.cpp
// compile with: /c
void __declspec(novtable) f() {}   // C2498
class __declspec(novtable) A {};   // OK
```
