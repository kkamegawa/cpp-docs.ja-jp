---
title: コンパイラ エラー C2505
ms.date: 11/04/2016
f1_keywords:
- C2505
helpviewer_keywords:
- C2505
ms.assetid: b19f5c53-399d-425e-90db-fe3ca9b40858
ms.openlocfilehash: 94a6f180c93839646d771509145b2f65a00780fd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746865"
---
# <a name="compiler-error-c2505"></a>コンパイラ エラー C2505

' symbol ': ' __declspec (修飾子) ' は、グローバルオブジェクトまたは静的データメンバーの宣言または定義にのみ適用できます

グローバルスコープでのみ使用するように設計された `__declspec` 修飾子が関数で使用されました。

詳細については、「 [appdomain](../../cpp/appdomain.md) 」および「 [process](../../cpp/process.md)」を参照してください。

次の例では、C2505 が生成されます。

```cpp
// C2505.cpp
// compile with: /clr

// OK
__declspec(process) int ii;
__declspec(appdomain) int jj;

int main() {
   __declspec(process) int i;   // C2505
   __declspec(appdomain) int j;   // C2505
}
```
