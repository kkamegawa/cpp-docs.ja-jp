---
title: コンパイラ エラー C3073
ms.date: 11/04/2016
f1_keywords:
- C3073
helpviewer_keywords:
- C3073
ms.assetid: b24b9b8b-f9fb-4c3c-a1a0-97fad2081bfc
ms.openlocfilehash: 0b53e704c14746579a32550726364c062a9ade6f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756748"
---
# <a name="compiler-error-c3073"></a>コンパイラ エラー C3073

' type ': ref クラスにユーザー定義のコピーコンストラクターがありません。

[/Clr (共通言語ランタイムのコンパイル)](../../build/reference/clr-common-language-runtime-compilation.md)コンパイルでは、コンパイラは参照型のコピーコンストラクターを生成しません。 任意の **/clr**コンパイルで、型のインスタンスがコピーされることが予想される場合は、参照型に対して独自のコピーコンストラクターを定義する必要があります。

詳細については、「 [ C++参照型のスタックセマンティクス](../../dotnet/cpp-stack-semantics-for-reference-types.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C3073 が生成されます。

```cpp
// C3073.cpp
// compile with: /clr
ref class R {
public:
   R(int) {}
};

ref class S {
public:
   S(int) {}
   S(const S %rhs) {}   // copy constructor
};

void f(R) {}
void f2(S) {}
void f3(R%){}

int main() {
   R r(1);
   f(r);   // C3073
   f3(r);   // OK

   S s(1);
   f2(s);   // OK
}
```
