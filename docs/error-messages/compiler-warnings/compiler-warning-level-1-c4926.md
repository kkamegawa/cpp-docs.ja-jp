---
title: コンパイラの警告 (レベル 1) C4926
ms.date: 11/04/2016
f1_keywords:
- C4926
helpviewer_keywords:
- C4926
ms.assetid: 5717fce0-146f-4ef2-bde0-e9a01c0922d1
ms.openlocfilehash: a68e251209cb9664552b4324de108f2cf7ce3f37
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74050212"
---
# <a name="compiler-warning-level-1-c4926"></a>コンパイラの警告 (レベル 1) C4926

'identifier': シンボルは既に定義されています。属性は無視されます。

事前宣言が見つかりましたが、同じ名前の属性付きコンストラクトが既に存在します。 事前宣言の属性は無視されます。

次の例では C4926 警告が生成されます。

```cpp
// C4926.cpp
// compile with: /W1
[module(name="MyLib")];

[coclass]
struct a {
};

[coclass]
struct a;   // C4926

int main() {
}
```