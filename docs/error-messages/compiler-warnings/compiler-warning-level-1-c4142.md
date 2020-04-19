---
title: コンパイラの警告 (レベル 1) C4142
ms.date: 11/04/2016
f1_keywords:
- C4142
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
ms.openlocfilehash: 97b13ad65335df435d071c106f577aefca7e072d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73625005"
---
# <a name="compiler-warning-level-1-c4142"></a>コンパイラの警告 (レベル 1) C4142

型の問題のない再定義

型は、生成されたコードに影響を与えない方法で再定義されます。

次のような原因をチェックして問題を解決するには:

- 派生クラスのメンバー関数は、基底クラスの対応するメンバー関数とは異なる戻り値の型を持っています。

- `typedef` コマンドで定義された型が、別の構文を使用して再定義されています。

次の例では、C4142 が生成されます。

```c
// C4142.c
// compile with: /W1
float X2;
X2 = 2.0 + 1.0;   // C4142

int main() {
   float X2;
   X2 = 2.0 + 1.0;   // OK
}
```