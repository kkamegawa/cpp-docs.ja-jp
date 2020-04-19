---
title: コンパイラ エラー C2166
ms.date: 11/04/2016
f1_keywords:
- C2166
helpviewer_keywords:
- C2166
ms.assetid: 12789c3a-cc76-48bb-ae2e-64283e0964ed
ms.openlocfilehash: 73b3c29c5e4bdd22a50330a8a90aad37a9d45cbf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758412"
---
# <a name="compiler-error-c2166"></a>コンパイラ エラー C2166

左辺値は const オブジェクトに指定されています。

コードが、 `const`宣言した項目を変更しようとしています。

次の例では C2166 が生成されます。

```cpp
// C2166.cpp
int f();
int main() {
   ( (const int&) 1 ) = 5;   // C2166
}
```
