---
title: コンパイラ エラー C2146
ms.date: 11/04/2016
f1_keywords:
- C2146
helpviewer_keywords:
- C2146
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
ms.openlocfilehash: 8dc7b521243c4eafdc22fab851812b6c12b004cf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755916"
---
# <a name="compiler-error-c2146"></a>コンパイラ エラー C2146

構文エラー: 識別子 ' identifier ' の前に ' token ' がありません。

コンパイラは `token` を予期していましたが、代わりに `identifier` 見つかりました。  次の原因が考えられます。

1. スペルまたは大文字小文字のエラー。

1. 識別子の宣言に型指定子がありません。

このエラーは、タイポグラフィエラーが原因で発生する可能性があります。 通常、エラー [C2065](../../error-messages/compiler-errors-1/compiler-error-c2065.md)はこのエラーの前にあります。

## <a name="example"></a>使用例

次の例では、C2146 が生成されます。

```cpp
// C2146.cpp
class CDeclaredClass {};

class CMyClass {
   CUndeclared m_myClass;   // C2146
   CDeclaredClass m_myClass2;   // OK
};

int main() {
   int x;
   int t x;   // C2146 : missing semicolon before 'x'
}
```

## <a name="example"></a>使用例

このエラーは、Visual Studio .NET 2003 で実行されたコンパイラ準拠作業の結果として生成されることもあります。 `typename` キーワードがありません。

次のサンプルは、Visual Studio .NET 2002 ではコンパイルされますが、Visual Studio .NET 2003 では失敗します。

```cpp
// C2146b.cpp
// compile with: /c
template <typename T>
struct X {
   struct Y {
      int i;
   };
   Y memFunc();
};

template <typename T>
X<T>::Y func() { }   // C2146

// OK
template <typename T>
typename X<T>::Y func() { }
```

## <a name="example"></a>使用例

このエラーは、Visual Studio .NET 2003 で実行されたコンパイラ準拠作業の結果としても表示されます。明示的な特殊化では、プライマリテンプレートからテンプレートパラメーターが見つからなくなりました。

プライマリテンプレートからの `T` の使用は、明示的な特殊化では許可されていません。 Visual Studio .NET 2003 と Visual Studio .NET でコードを有効にするには、特殊化のテンプレートパラメーターのすべてのインスタンスを明示的に特殊化された型で置き換えます。

次のサンプルは、Visual Studio .NET ではコンパイルされますが、Visual Studio .NET 2003 では失敗します。

```cpp
// C2146_c.cpp
// compile with: /c
template <class T>
struct S;

template <>
struct S<int> {
   T m_t;   // C2146
   int m_t2;   // OK
};
```
