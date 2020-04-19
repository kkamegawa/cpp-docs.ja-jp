---
title: コンパイラエラー C2705
ms.date: 11/04/2016
f1_keywords:
- C2705
helpviewer_keywords:
- C2705
ms.assetid: 29249ea3-4ea7-4105-944b-bdb83e8d6852
ms.openlocfilehash: 1cd46db8e4cb237bebd9568409ecadf0ff84cdf8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758308"
---
# <a name="compiler-error-c2705"></a>コンパイラエラー C2705

' label ': ' exception handler block ' スコープへのジャンプが正しくありません。

実行は、`try`/`catch`、`__try`/`__except`、`__try`/`__finally` ブロック内のラベルにジャンプします。 詳細については、「[例外処理](../../cpp/exception-handling-in-visual-cpp.md)」を参照してください。

次の例では、C2705 が生成されます。

```cpp
// C2705.cpp
int main() {
goto trouble;
   __try {
      trouble: ;   // C2705
   }
   __finally {}

   // try the following line instead
   // trouble: ;
}
```
