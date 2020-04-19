---
title: コンパイラ エラー C2274
ms.date: 11/04/2016
f1_keywords:
- C2274
helpviewer_keywords:
- C2274
ms.assetid: 8e874903-f499-45ef-8291-f821eee4cc1c
ms.openlocfilehash: fd807dedb6c300860611d07212b8fc8952a90a65
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758672"
---
# <a name="compiler-error-c2274"></a>コンパイラ エラー C2274

' type ': '. ' 演算子の右側が正しくありません。

型は、メンバーアクセス (.) 演算子の右オペランドとして表示されます。

このエラーは、ユーザー定義型変換にアクセスしようとした場合に発生する可能性があります。 ピリオドと `type`の間に `operator` キーワードを使用します。

次の例では C2286 が生成されます。

```cpp
// C2274.cpp
struct MyClass {
   operator int() {
      return 0;
   }
};

int main() {
   MyClass ClassName;
   int i = ClassName.int();   // C2274
   int j = ClassName.operator int();   // OK
}
```
