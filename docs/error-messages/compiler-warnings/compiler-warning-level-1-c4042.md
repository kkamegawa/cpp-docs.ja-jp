---
title: コンパイラの警告 (レベル 1) C4042
ms.date: 11/04/2016
f1_keywords:
- C4042
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
ms.openlocfilehash: db7f0425c3752c20ca8c5d4b6c95845ff64475c5
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627033"
---
# <a name="compiler-warning-level-1-c4042"></a>コンパイラの警告 (レベル 1) C4042

' identifier ': 無効なストレージクラスがあります

このコンテキストでは、指定されたストレージクラスをこの識別子と共に使用することはできません。 コンパイラは、代わりに既定のストレージクラスを使用します。

- *識別子*が関数の場合は `extern`。

- **auto**(*識別子*が仮パラメーターまたはローカル変数の場合)。

- ストレージクラスがありません。*識別子*がグローバル変数です。

この警告は、パラメーター宣言で**register**以外のストレージクラスを指定することによって発生することがあります。

次の例では、C4042 が生成されます。

```cpp
// C4042.cpp
// compile with: /W1 /LD
int func2( __declspec( thread ) int tls_i )    // C4042
// try the following line instead
// int func2( int tls_i )
{
   return tls_i;
}
```