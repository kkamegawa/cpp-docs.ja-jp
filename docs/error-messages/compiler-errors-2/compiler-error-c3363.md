---
title: コンパイラ エラー C3363
ms.date: 11/04/2016
f1_keywords:
- C3363
helpviewer_keywords:
- C3363
ms.assetid: 41aa922f-608e-4f7a-ba66-451fc1161935
ms.openlocfilehash: 44b41dd706c7eb290c71d7312464d688cbcf08d3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757359"
---
# <a name="compiler-error-c3363"></a>コンパイラ エラー C3363

'type': 'typeid' のみを型に適用できます

[typeid](../../extensions/typeid-cpp-component-extensions.md) 演算子が正しく使用されていません。

## <a name="example"></a>使用例

次の例では C3363 が生成されます。

```cpp
// C3363.cpp
// compile with: /clr
int main() {
   System::typeid;   // C3363
}
```
