---
title: コンパイラ エラー C3083
ms.date: 11/04/2016
f1_keywords:
- C3083
helpviewer_keywords:
- C3083
ms.assetid: 05ff791d-52bb-41eb-9511-3ef89d7f4710
ms.openlocfilehash: ee4a2bc683a757e079295c16d1022739eaa5726c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759712"
---
# <a name="compiler-error-c3083"></a>コンパイラ エラー C3083

' function ': ':: ' の左側のシンボルは型でなければなりません

関数が正しく呼び出されませんでした。

## <a name="example"></a>使用例

次の例では、C3083 が生成されます。

```cpp
// C3083.cpp
// compile with: /c
struct N {
   ~N();
};

struct N1 {
   ~N1();
};

N::N::~N() {}   // C3083
N1::~N1() {}   // OK
```
