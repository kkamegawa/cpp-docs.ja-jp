---
title: コンパイラ エラー C2976
ms.date: 11/04/2016
f1_keywords:
- C2976
helpviewer_keywords:
- C2976
ms.assetid: d9bf9836-325e-4f72-a7e3-a67cf19d32e7
ms.openlocfilehash: 76fd2363b6139bc1bc04aa4d4949a12522e31aa6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751795"
---
# <a name="compiler-error-c2976"></a>コンパイラ エラー C2976

' identifier ': 型引数が少なすぎます

ジェネリックまたはテンプレートに1つ以上の実際の引数がありません。 ジェネリックまたはテンプレート宣言を確認して、正しい数のパラメーターを調べてください。

このエラーは、標準ライブラリのコンポーネントでテンプレートC++引数が欠落していることが原因で発生する場合があります。

次の例では、C2976 が生成されます。

```cpp
// C2976.cpp
template <class T>
struct TC {
   T t;
};
int main() {
   TC<>* t;   // C2976
   TC<int>* t2;   // OK
}
```

C2976 は、ジェネリックを使用する場合にも発生する可能性があります。

```cpp
// C2976b.cpp
// compile with: /clr
generic <class T>
ref struct GC {
   T t;
};

int main() {
   GC<>^ g;   // C2976
   GC<int>^ g2;   // OK
}
```
