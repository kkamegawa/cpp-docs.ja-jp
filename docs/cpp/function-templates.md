---
title: 関数テンプレート
ms.date: 07/15/2019
helpviewer_keywords:
- function templates
- templates, function
- function templates, about function templates
ms.assetid: 59b56a4b-0689-4161-9c07-25021562e2a7
ms.openlocfilehash: d430ad7650ffa47f0d6334a827b416cfb05ae6c2
ms.sourcegitcommit: fd466f2e14ad001f52f3dbe54f46d77be10f2d7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67894358"
---
# <a name="function-templates"></a>関数テンプレート

クラス テンプレートは、インスタンス化の際にクラスに渡される型引数に基づいた、関連性のある複数クラスによるファミリを定義します。 関数テンプレートは、クラス テンプレートに似ていますが、定義されるのは関数ファミリです。 関数テンプレートを使用すると、同じコードに基づいているものの、異なる型またはクラスを対象にする関数のセットを指定できます。 次の関数テンプレートは、2 つの項目を入れ替えます。

```cpp
// function_templates1.cpp
template< class T > void MySwap( T& a, T& b ) {
   T c(a);
   a = b;
   b = c;
}
int main() {
}
```

このコードは、引数の値を入れ替える関数のファミリを定義します。 このテンプレートを入れ替える関数を生成できます**int**と**long**型、およびユーザー定義型です。 `MySwap` は、クラスのコピー コンストラクターと代入演算子が正しく定義されていれば、クラスの入れ替えも実行します。

さらに、関数テンプレートが入れ替えが防止、さまざまな種類のオブジェクトの型をコンパイラが認識するため、 *、* と*b*コンパイル時にパラメーター。

template 宣言されていない関数も、void ポインターを使用してこの関数を実行できますが、テンプレート バージョンはタイプ セーフです。 次の呼び出しがあるとします。

```cpp
int j = 10;
int k = 18;
CString Hello = "Hello, Windows!";
MySwap( j, k );          //OK
MySwap( j, Hello );      //error
```

コンパイラはパラメーターの型が異なる `MySwap` 関数を生成できないため、2 番目の `MySwap` 呼び出しでは、コンパイル時にエラーが発生します。 void ポインターが使用されている場合は、どちらの関数呼び出しも正しくコンパイルされますが、関数は実行時に正しく機能しません。

関数テンプレートのテンプレート引数を明示的に指定できます。 例えば:

```cpp
// function_templates2.cpp
template<class T> void f(T) {}
int main(int j) {
   f<char>(j);   // Generate the specialization f(char).
   // If not explicitly specified, f(int) would be deduced.
}
```

テンプレート引数を明示的に指定すると、通常の暗黙の型変換が実行されて、関数の引数が対応する関数テンプレート パラメーターの型に変換されます。 上記の例では、コンパイラの変換`j`入力**char**します。

## <a name="see-also"></a>関連項目

[[テンプレート]](../cpp/templates-cpp.md)<br/>
[関数テンプレートのインスタンス化](../cpp/function-template-instantiation.md)<br/>
[明示的なインスタンス化](../cpp/explicit-instantiation.md)<br/>
[関数テンプレートの明示的特殊化](../cpp/explicit-specialization-of-function-templates.md)