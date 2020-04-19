---
title: コンパイラ エラー C3279
ms.date: 11/04/2016
f1_keywords:
- C3279
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
ms.openlocfilehash: 3025dbf7c6bf4701218c2d9a956cae26d7180848
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757606"
---
# <a name="compiler-error-c3279"></a>コンパイラ エラー C3279

cli 名前空間で宣言されたクラス テンプレートの明示的なインスタンス生成と同様に、部分的または明示的な特殊化は許可されていません

`cli` 名前空間は、Microsoft によって定義され、擬似テンプレートが含まれています。 Microsoft C++コンパイラでは、この名前空間のクラステンプレートのユーザー定義、部分的な特殊化、および明示的なインスタンス化は許可されていません。

次の例では C3279 が生成されます。

```cpp
// C3279.cpp
// compile with: /clr
namespace cli {
   template <> ref class array<int> {};   // C3279
   template <typename T> ref class array<T, 2> {};   // C3279
}
```
