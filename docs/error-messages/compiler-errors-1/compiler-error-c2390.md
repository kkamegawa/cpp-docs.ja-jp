---
title: コンパイラ エラー C2390
ms.date: 11/04/2016
f1_keywords:
- C2390
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
ms.openlocfilehash: 515e2e151d27dd2eb84fc1dc71b9197b36b14cbb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745045"
---
# <a name="compiler-error-c2390"></a>コンパイラ エラー C2390

' identifier ': ストレージクラス ' 指定子 ' が正しくありません。

ストレージクラスは、グローバルスコープ識別子に対して有効ではありません。 既定のストレージクラスは、無効なクラスの代わりに使用されます。

考えられる解決策は次のとおりです。

- 識別子が関数の場合は、`extern` ストレージで宣言します。

- 識別子が仮パラメーターまたはローカル変数の場合は、auto storage を使用して宣言します。

- 識別子がグローバル変数の場合は、ストレージクラス (auto storage) を使用せずに宣言します。

## <a name="example"></a>使用例

- 次の例では、C2390 が生成されます。

```cpp
// C2390.cpp
register int i;   // C2390

int main() {
   register int j;   // OK
}
```
