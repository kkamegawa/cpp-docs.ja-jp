---
title: コンパイラエラー C2061
ms.date: 11/04/2016
f1_keywords:
- C2061
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
ms.openlocfilehash: dc64852523b6b56bc506260576e3c79164628340
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735932"
---
# <a name="compiler-error-c2061"></a>コンパイラエラー C2061

構文エラー: 識別子 ' identifier '

コンパイラは、予期されていなかった識別子を検出しました。 使用する前に `identifier` が宣言されていることを確認してください。

初期化子は、かっこで囲むことができます。 この問題を回避するには、宣言子をかっこで囲むか、`typedef`にします。

このエラーは、コンパイラがクラステンプレート引数として式を検出した場合にも発生する可能性があります。型であることをコンパイラに通知するには、 [typename](../../cpp/typename.md)を使用します。

次の例では、C2061 が生成されます。

```cpp
// C2061.cpp
// compile with: /c
template < A a >   // C2061
// try the following line instead
// template < typename b >
class c{};
```

C2061 は、インスタンス名を[typeid](../../extensions/typeid-cpp-component-extensions.md)に渡すと発生する可能性があります。

```cpp
// C2061b.cpp
// compile with: /clr
ref struct G {
   int i;
};

int main() {
   G ^ pG = gcnew G;
   System::Type ^ pType = typeid<pG>;   // C2061
   System::Type ^ pType2 = typeid<G>;   // OK
}
```
