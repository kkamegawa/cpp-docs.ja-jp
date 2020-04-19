---
title: コンパイラ エラー C2835
ms.date: 11/04/2016
f1_keywords:
- C2835
helpviewer_keywords:
- C2835
ms.assetid: 41c70630-983f-4da2-8342-513cf48b0519
ms.openlocfilehash: 17c0ecdb516b35cb0d00745a33704bae52350d57
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757866"
---
# <a name="compiler-error-c2835"></a>コンパイラ エラー C2835

ユーザー定義の変換 ' type ' に仮引数を指定することはできません

ユーザー定義型の変換は、仮パラメーターを受け取ることはできません。

次の例では、C2835 が生成されます。

```cpp
// C2835.cpp
class A {
public:
   char v_char;

   A() {
      v_char = 'A';
   };
   operator char(char a) {   // C2835
   // try the following line instead
   // operator char() {
      return v_char + 1;
   };
};

int main() {
   A a;
}
```
