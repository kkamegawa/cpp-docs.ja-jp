---
title: nothrow (C++)
ms.date: 01/03/2018
f1_keywords:
- nothrow_cpp
helpviewer_keywords:
- __declspec keyword [C++], nothrow
- nothrow __declspec keyword
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
ms.openlocfilehash: 88041b374cc48ac31c8990aa7f867ba25b33e1d7
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345881"
---
# <a name="nothrow-c"></a>nothrow (C++)

**Microsoft 固有の仕様**

A **_ _declspec**関数の宣言で使用できる拡張属性。

## <a name="syntax"></a>構文

> *return-type* __declspec(nothrow) [*call-convention*] *function-name* ([*argument-list*])

## <a name="remarks"></a>Remarks

すべての新しいコードを使用していることをお勧めします。、 [noexcept](noexcept-cpp.md)演算子なく`__declspec(nothrow)`します。

この属性は、宣言された関数、および、その呼び出す関数が例外をスローしないことをコンパイラに伝えます。 ただし、このディレクティブは適用されません。 しないと、つまり、 [std::terminate](../standard-library/exception-functions.md#terminate)呼び出されるとは異なり`noexcept`、または **/std:c++17**モード (Visual Studio 2017 バージョン 15.5 以降)、`throw()`します。

同期例外処理モデル (現在は既定のモデル) の場合、コンパイラはこのような関数で特定のアンワインド可能オブジェクトの有効期間を追跡する機構を削除して、コード サイズを大幅に小さくできます。 次のプリプロセッサ ディレクティブを指定するには、次の 3 つの関数の宣言が同じ **/std:c++14**モード。

```cpp
#define WINAPI __declspec(nothrow) __stdcall

void WINAPI f1();
void __declspec(nothrow) __stdcall f2();
void __stdcall f3() throw();
```

**/std:c++17**モード、`throw()`を使用すると、他と等価でない`__declspec(nothrow)`原因になるので`std::terminate`関数から例外がスローされた場合に呼び出されます。

`void __stdcall f3() throw();`宣言は、C++ 標準で定義されている構文を使用します。 C++ 17 で、`throw()`キーワードは非推奨とされました。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__declspec](../cpp/declspec.md)<br/>
[noexcept](noexcept-cpp.md)<br/>
[キーワード](../cpp/keywords-cpp.md)