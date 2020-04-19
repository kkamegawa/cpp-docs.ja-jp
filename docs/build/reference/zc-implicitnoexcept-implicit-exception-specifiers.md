---
title: /Zc:implicitNoexcept (暗黙の例外指定子)
ms.date: 03/06/2018
f1_keywords:
- /Zc:implicitNoexcept
helpviewer_keywords:
- /Zc:implicitNoexcept
- Zc:implicitNoexcept
- -Zc:implicitNoexcept
ms.assetid: 71807652-6f9d-436b-899e-f52daa6f500b
ms.openlocfilehash: ec2b8c8fb4c7730a78c4403606d6fa61c0ddc374
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315561"
---
# <a name="zcimplicitnoexcept-implicit-exception-specifiers"></a>/Zc:implicitNoexcept (暗黙の例外指定子)

ときに、 **/Zc:implicitNoexcept**オプションを指定すると、コンパイラは暗黙的な追加[noexcept](../../cpp/noexcept-cpp.md)コンパイラで定義された特殊なメンバー関数、ユーザー定義のデストラクターの例外指定子とデアロケーターします。 既定では、 **/Zc:implicitNoexcept** ISO C 11 標準に準拠するようになっています。 このオプションをオフにすると、ユーザー定義のデストラクターとデアロケーターおよびコンパイラ定義の特別なメンバー関数に対して暗黙的な `noexcept` が無効になります。

## <a name="syntax"></a>構文

> **/Zc:implicitNoexcept**[**-**]

## <a name="remarks"></a>Remarks

**/Zc:implicitNoexcept** ISO C 11 標準のセクション 15.4 に従うようにコンパイラに指示します。 暗黙的に追加し、`noexcept`例外指定子は、それぞれの特殊なメンバーが暗黙的に宣言または明示的に既定化関数を既定のコンス トラクター、コピー コンス トラクター、移動コンス トラクター、デストラクター、コピー代入演算子、または移動の代入演算子、および各ユーザー定義のデストラクターまたはデアロケーター関数。 ユーザー定義のデアロケーターには、暗黙的な `noexcept(true)` 例外指定子があります。 ユーザー定義のデストラクターでは、含まれているメンバー クラスまたは基底クラスに `noexcept(true)` ではないデストラクターがなければ、暗黙的な例外指定子は `noexcept(true)` です。 コンパイラにより生成された特別なメンバー関数では、この関数によって直接呼び出された任意の関数が実質的に `noexcept(false)` である場合、暗黙的な例外指定子は `noexcept(false)` です。 それ以外の場合、暗黙的な例外指定子は `noexcept(true)` です。

コンパイラは、明示的な `noexcept` や `throw` 指定子または `__declspec(nothrow)` 属性を使用して宣言された関数に対して暗黙的な例外指定子を生成しません。

既定では、 **/Zc:implicitNoexcept**を有効にします。 [/Permissive -](permissive-standards-conformance.md)オプションには影響しません **/Zc:implicitNoexcept**します。

指定することで、オプションが無効になっている場合 **/zc: implicitnoexcept-**、コンパイラによって暗黙的な例外指定子は生成されません。 この動作は Visual Studio 2013 の場合と同じであり、例外指定子がないデストラクターとデアロケーターでは `throw` ステートメントを使用することができません。 既定とタイミング **/Zc:implicitNoexcept**の場合は、指定が、`throw`暗黙的な関数での実行時にステートメントが検出された`noexcept(true)`指定子の直接の呼び出しと`std::terminate`と例外ハンドラーに対する通常のアンワインド動作は保証されません。 このような状況を識別できるように、コンパイラが生成されます[コンパイラの警告 (レベル 1) C4297](../../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md)します。 場合、`throw`は意図的なものをお勧めしますが、明示的なように関数宣言を変更する`noexcept(false)`指定子を使用してではなく **/zc: implicitnoexcept-** します。

この例では、ユーザー定義のデストラクターを明示的な例外指定子を持たないによる場合の動作方法、 **/Zc:implicitNoexcept**オプションを設定するか、または無効になっています。 動作を設定するを使用してコンパイル`cl /EHsc /W4 implicitNoexcept.cpp`します。 無効になっているときの動作を表示するを使用してコンパイル`cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp`します。

```cpp
// implicitNoexcept.cpp
// Compile by using: cl /EHsc /W4 implicitNoexcept.cpp
// Compile by using: cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp

#include <iostream>
#include <cstdlib>      // for std::exit, EXIT_FAILURE, EXIT_SUCCESS
#include <exception>    // for std::set_terminate

void my_terminate()
{
    std::cout << "Unexpected throw caused std::terminate" << std::endl;
    std::cout << "Exit returning EXIT_FAILURE" << std::endl;
    std::exit(EXIT_FAILURE);
}

struct A {
    // Explicit noexcept overrides implicit exception specification
    ~A() noexcept(false) {
        throw 1;
    }
};

struct B : public A {
    // Compiler-generated ~B() definition inherits noexcept(false)
    ~B() = default;
};

struct C {
    // By default, the compiler generates an implicit noexcept(true)
    // specifier for this user-defined destructor. To enable it to
    // throw an exception, use an explicit noexcept(false) specifier,
    // or compile by using /Zc:implicitNoexcept-
    ~C() {
        throw 1; // C4297, calls std::terminate() at run time
    }
};

struct D : public C {
    // This destructor gets the implicit specifier of its base.
    ~D() = default;
};

int main()
{
    std::set_terminate(my_terminate);

    try
    {
        {
            B b;
        }
    }
    catch (...)
    {
        // exception should reach here in all cases
        std::cout << "~B Exception caught" << std::endl;
    }
    try
    {
        {
            D d;
        }
    }
    catch (...)
    {
        // exception should not reach here if /Zc:implicitNoexcept
        std::cout << "~D Exception caught" << std::endl;
    }
    std::cout << "Exit returning EXIT_SUCCESS" << std::endl;
    return EXIT_SUCCESS;
}
```

既定の設定を使用して、コンパイル時に **/Zc:implicitNoexcept**サンプルには、この出力が生成されます。

```Output
~B Exception caught
Unexpected throw caused std::terminate
Exit returning EXIT_FAILURE
```

設定を使用してコンパイルすると **/zc: implicitnoexcept-** サンプルには、この出力が生成されます。

```Output
~B Exception caught
~D Exception caught
Exit returning EXIT_SUCCESS
```

Visual C++ の準拠に関する問題について詳しくは、「 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)」をご覧ください。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **C/C++** > **コマンドライン**プロパティ ページ。

1. 変更、**追加オプション**含めるプロパティを **/Zc:implicitNoexcept**または **/zc: implicitnoexcept-** 選び、 **OK**します。

## <a name="see-also"></a>関連項目

[/Zc (準拠)](zc-conformance.md)<br/>
[noexcept](../../cpp/noexcept-cpp.md)<br/>
[例外の仕様 (スロー)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[terminate](../../standard-library/exception-functions.md#terminate)<br/>
