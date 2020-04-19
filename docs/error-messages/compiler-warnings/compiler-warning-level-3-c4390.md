---
title: コンパイラの警告 (レベル 3) C4390
ms.date: 11/04/2016
f1_keywords:
- C4390
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
ms.openlocfilehash: 8402c6a2d0fcbb4704b833ac7ae2b070c7af3a48
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051592"
---
# <a name="compiler-warning-level-3-c4390"></a>コンパイラの警告 (レベル 3) C4390

'; ': 空の制御されたステートメントが見つかりました。これは目的ですか。

命令を含まない制御ステートメントの後にセミコロンが見つかりました。

マクロが原因で C4390 を取得した場合は、[警告](../../preprocessor/warning.md)プラグマを使用して、マクロを含むモジュールの C4390 を無効にする必要があります。

次の例では、C4390 が生成されます。

```cpp
// C4390.cpp
// compile with: /W3
int main() {
   int i = 0;
   if (i);   // C4390
      i++;
}
```