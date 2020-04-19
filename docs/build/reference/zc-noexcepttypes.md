---
title: '/Zc: noexceptTypes (C++ 17 noexcept ルール)'
ms.date: 11/14/2017
f1_keywords:
- /Zc:noexceptTypes
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
ms.openlocfilehash: 35bea7c2c629c615c60a6136f289b6b11926c054
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624862"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc: noexceptTypes (C++ 17 noexcept ルール)

C++ 17 標準では、`noexcept`のエイリアス `throw()` し、`throw(<type list>)` と `throw(...)`を削除し、特定の型に `noexcept`を含めることができます。 この変更により、C++ 14 以前に準拠しているコードでソース互換性の問題がいくつか発生する可能性があります。 **/Zc: noexceptTypes**オプションは、c++ 17 標準に準拠することを指定します。 **/Zc: noexceptTypes-** c++ 17 モードでコードをコンパイルするときに、c++ 14 以前の動作を許可します。

## <a name="syntax"></a>構文

> **/Zc: noexceptTypes**[-]

## <a name="remarks"></a>Remarks

ときに、 **/zc: noexcepttypes**オプションを指定すると、コンパイラは、標準の C++17 に準拠しているし、処理[throw()](../../cpp/exception-specifications-throw-cpp.md)のエイリアスとして[noexcept](../../cpp/noexcept-cpp.md)を削除します`throw(<type list>)`。 **/Zc: noexcepttypes**場合オプションは使用のみ[/std:c++17](std-specify-language-standard-version.md)または[/std:latest](std-specify-language-standard-version.md)を有効にします。 **/Zc: noexceptTypes**は、ISO c++ 17 標準に準拠するように既定で有効になっています。 [/Permissive-](permissive-standards-conformance.md)オプションは、 **/zc: noexceptTypes**には影響しません。 指定することで、このオプションをオフに **/Zc:noexceptTypes-** の C++14 動作に戻す`noexcept`とき **/std:c++17**または **/std:latest**が指定されてです。

Visual Studio 2017 バージョン15.5 以降では、 C++コンパイラは c++ 17 モードでの宣言内で、または[/permissive-](permissive-standards-conformance.md)オプションを指定したときに、一致しない例外指定を診断します。

このサンプルでは、 **/zc: noexceptTypes**オプションが設定または無効になっている場合に、例外指定子を使用した宣言がどのように動作するかを示します。 設定時に動作を表示するには、`cl /EHsc /W4 noexceptTypes.cpp`を使用してコンパイルします。 無効になっているときの動作を表示するには、`cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp`を使用してコンパイルします。

```cpp
// noexceptTypes.cpp
// Compile by using: cl /EHsc /W4 noexceptTypes.cpp
// Compile by using: cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp

void f() throw();    // equivalent to void f() noexcept;
void f() { }         // warning C5043
void g() throw(...); // warning C5040

struct A
{
    virtual void f() throw();
};

struct B : A
{
    virtual void f() { } // error C2694
};
```

既定の設定である **/zc: noexceptTypes**を使用してコンパイルした場合、サンプルでは警告が生成されます。 コードを更新するには、代わりに次のコードを使用します。

```cpp
void f() noexcept;
void f() noexcept { }
void g() noexcept(false);

struct A
{
    virtual void f() noexcept;
};

struct B : A
{
    virtual void f() noexcept { }
};
```

Visual C++ の準拠に関する問題について詳しくは、「 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)」をご覧ください。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関する記事を参照してください。

1. **[構成プロパティ]**  >  **[C/C++]**  >  **[コマンド ライン]** プロパティ ページを選択します。

1. **/Zc: noexceptTypes**または **/zc: noexceptTypes**が含まれるように "**追加オプション**" プロパティを変更し、[ **OK]** をクリックします。

## <a name="see-also"></a>関連項目

[/Zc (準拠)](zc-conformance.md)\
[noexcept](../../cpp/noexcept-cpp.md)\
[例外の指定 (throw)](../../cpp/exception-specifications-throw-cpp.md)
