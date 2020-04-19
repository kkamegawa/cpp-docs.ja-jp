---
title: コンパイラ エラー C3384
ms.date: 11/04/2016
f1_keywords:
- C3384
helpviewer_keywords:
- C3384
ms.assetid: c9f92c6a-62a9-4333-b2b1-bc55c7f288b6
ms.openlocfilehash: 059518462bd7a0463fd03fec6434acbbda7ee60a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756436"
---
# <a name="compiler-error-c3384"></a>コンパイラ エラー C3384

'type_parameter': 値の制約および ref 制約を同時に使用することはできません

ジェネリック型を `value class` と `ref class`の両方に制限することはできません。

詳細については、「[ジェネリック型パラメーターの制約 (C++/cli)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) 」を参照してください。

## <a name="example"></a>使用例

次の例では C3384 が生成されます。

```cpp
// C3384.cpp
// compile with: /c /clr
generic <typename T>
where T : ref class
where T : value class   // C3384
ref class List {};
```
