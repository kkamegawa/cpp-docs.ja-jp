---
title: コンパイラ エラー C2511
ms.date: 11/04/2016
f1_keywords:
- C2511
helpviewer_keywords:
- C2511
ms.assetid: df999efe-fe2b-418b-bb55-4af6a0592631
ms.openlocfilehash: ff78cb50b274fe40d513739264bd7e9894bbed9d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746566"
---
# <a name="compiler-error-c2511"></a>コンパイラ エラー C2511

' identifier ': オーバーロードされたメンバー関数が ' class ' に見つかりませんでした

指定されたパラメーターを使用して関数のバージョンが宣言されていません。  次の原因が考えられます。

1. 関数に渡されたパラメーターが正しくありません。

1. 間違った順序で渡されたパラメーター。

1. パラメーター名のスペルが正しくありません。

次の例では、C2511 が生成されます。

```cpp
// C2511.cpp
// compile with: /c
class C {
   int c_2;
   int Func(char *, char *);
};

int C::Func(char *, char *, int i) {   // C2511
// try the following line instead
// int C::Func(char *, char *) {
   return 0;
}
```
