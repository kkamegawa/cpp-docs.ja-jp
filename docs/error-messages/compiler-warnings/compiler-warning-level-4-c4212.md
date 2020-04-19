---
title: コンパイラの警告 (レベル 4) C4212
ms.date: 11/04/2016
f1_keywords:
- C4212
helpviewer_keywords:
- C4212
ms.assetid: df781ea1-182d-4f9f-9a31-55b6ce80c711
ms.openlocfilehash: 99dd99eee3c305a53c5ea03235d23a2520768176
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541825"
---
# <a name="compiler-warning-level-4-c4212"></a>コンパイラの警告 (レベル 4) C4212

非標準の拡張機能が使用されています: 省略記号を使用する関数宣言

関数プロトタイプには、可変個の引数があります。 関数定義ではありません。

次の例では、C4212 が生成されます。

```c
// C4212.c
// compile with: /W4 /Ze /c
void f(int , ...);
void f(int i, int j) {}
```