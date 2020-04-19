---
title: コンパイラ エラー C2273
ms.date: 11/04/2016
f1_keywords:
- C2273
helpviewer_keywords:
- C2273
ms.assetid: 3c682c66-97bf-4a23-a22c-d9a26a92bf95
ms.openlocfilehash: 9cd46f7a8a0762fcae2bdec15b9b4be6384adb25
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758685"
---
# <a name="compiler-error-c2273"></a>コンパイラ エラー C2273

' type ': '-> ' 演算子の右辺が正しくありません。

型は `->` 演算子の右オペランドとして表示されます。

このエラーは、ユーザー定義型変換にアクセスしようとした場合に発生する可能性があります。 キーワードを使用して-> と `type`を `operator` します。

次の例では、C2273 が生成されます。

```cpp
// C2273.cpp
struct MyClass {
   operator int() {
      return 0;
   }
};
int main() {
   MyClass * ClassPtr = new MyClass;
   int i = ClassPtr->int();   // C2273
   int j = ClassPtr-> operator int();   // OK
}
```
