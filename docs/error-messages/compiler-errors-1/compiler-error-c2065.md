---
title: コンパイラエラー C2065
ms.date: 08/19/2019
f1_keywords:
- C2065
helpviewer_keywords:
- C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
ms.openlocfilehash: 40d1d0744588c4b7911e84f5e57a6b40372b48cf
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630134"
---
# <a name="compiler-error-c2065"></a>コンパイラエラー C2065

> '*identifier*': 宣言のない識別子です。

コンパイラは、識別子の宣言を見つけることができません。 このエラーには多くの原因が考えられます。 C2065 の最も一般的な原因として、識別子が宣言されていない、識別子のスペルが間違っている、識別子が宣言されているヘッダーがファイルに含まれていない、識別子`cout`にスコープ修飾子がない、などがあります。`std::cout`. のC++宣言の詳細については、「[宣言とC++定義」 ()](../../cpp/declarations-and-definitions-cpp.md)を参照してください。

ここでは、一般的な問題と解決方法について詳しく説明します。

## <a name="the-identifier-is-undeclared"></a>識別子が宣言されていません

識別子が変数または関数名の場合は、それを使用する前に宣言する必要があります。 関数宣言には、関数を使用する前に、そのパラメーターの型も含める必要があります。 変数がを使用して`auto`宣言されている場合、コンパイラは初期化子から型を推論できる必要があります。

識別子がクラスまたは構造体のメンバーである場合、または名前空間で宣言されている場合は、クラスまたは構造体の名前、または名前空間のスコープ外で使用される場合は名前空間の名前で修飾する必要があります。 `using`または、など`using namespace std;`のディレクティブによって名前空間をスコープ内に配置するか、メンバー名をのような`using` `using std::string;`宣言によってスコープ内に配置する必要があります。 それ以外の場合、非修飾名は現在のスコープ内で宣言されていない識別子と見なされます。

識別子がユーザー定義型 ( `class`や`struct`など) のタグである場合、タグの型は、使用する前に宣言する必要があります。 たとえば、コード内で`struct SomeStruct { /*...*/ };`変数`SomeStruct myStruct;`を宣言する前に、宣言が存在している必要があります。

識別子が型のエイリアスである場合、型は`using`宣言を使用して宣言するか`typedef` 、使用する前に宣言する必要があります。 たとえば、をの型の`using my_flags = std::ios_base::fmtflags;` `std::ios_base::fmtflags`別名として`my_flags`使用するには、事前にを宣言する必要があります。

## <a name="example-misspelled-identifier"></a>例: 識別子のスペルミス

このエラーが発生するのは一般的に、識別子名のスペルが間違っている場合、または識別子で大文字と小文字が正しく使用されていない場合です。 宣言内の名前は、使用する名前と完全に一致している必要があります。

```cpp
// C2065_spell.cpp
// compile with: cl /EHsc C2065_spell.cpp
#include <iostream>
using namespace std;
int main() {
    int someIdentifier = 42;
    cout << "Some Identifier: " << SomeIdentifier << endl;
    // C2065: 'SomeIdentifier': undeclared identifier
    // To fix, correct the spelling:
    // cout << "Some Identifier: " << someIdentifier << endl;
}
```

## <a name="example-use-an-unscoped-identifier"></a>例: 対象範囲外の識別子を使用する

このエラーは、識別子が適切にスコープ設定されていない場合に発生する可能性があります。 を使用`cout`するときに C2065 が表示される場合は、これが原因です。 標準C++ライブラリの関数と演算子が名前空間で完全に修飾されていない場合`std` 、または`using`ディレクティブを使用して名前空間を現在のスコープに設定していない場合、コンパイラはそれらを見つけることができません。 この問題を解決するには、識別子名を完全修飾するか、 `using`ディレクティブを使用して名前空間を指定する必要があります。

と`cout` `std`が名前空間で定義されているため、この例はコンパイルに失敗します。 `endl`

```cpp
// C2065_scope.cpp
// compile with: cl /EHsc C2065_scope.cpp
#include <iostream>
// using namespace std;   // Uncomment this line to fix

int main() {
    cout << "Hello" << endl;   // C2065 'cout': undeclared identifier
                               // C2065 'endl': undeclared identifier
    // Or try the following line instead
    std::cout << "Hello" << std::endl;
}
```

型、型、または`class` `enum class`型`struct`の内部で宣言された識別子は、そのスコープの外部で使用する場合、外側のスコープの名前で修飾する必要があります。

## <a name="example-precompiled-header-isnt-first"></a>例: プリコンパイル済みヘッダーが最初ではない

このエラーは、プリコンパイル済みヘッダーファイルの #include の前に、#include、#define、#pragma などのプリプロセッサディレクティブを配置した場合に発生する可能性があります。 ソースファイルがプリコンパイル済みヘッダーファイルを使用する場合 (つまり、 **/yu**コンパイラオプションを使用してコンパイルされた場合)、プリコンパイル済みヘッダーファイルの前にあるすべてのプリプロセッサディレクティブは無視されます。

と\< `cout` が`endl` iostream > ヘッダーで定義されているため、この例はコンパイルに失敗します。これは、プリコンパイル済みヘッダーファイルの前に含まれているため無視されます。 この例をビルドするには、3つのファイルをすべて作成し、stdafx.h をコンパイルしてから、C2065_pch をコンパイルします。

```cpp
// pch.h (stdafx.h in Visual Studio 2017 and earlier)
#include <stdio.h>
```

```cpp
// pch.cpp (stdafx.cpp in Visual Studio 2017 and earlier)
// Compile by using: cl /EHsc /W4 /c /Ycstdafx.h stdafx.cpp
#include "pch.h"
```

```cpp
// C2065_pch.cpp
// compile with: cl /EHsc /W4 /Yustdafx.h C2065_pch.cpp
#include <iostream>
#include "stdafx.h"
using namespace std;

int main() {
    cout << "Hello" << endl;   // C2065 'cout': undeclared identifier
                               // C2065 'endl': undeclared identifier
}
```

この問題を解決するには、iostream \<> の #include をプリコンパイル済みヘッダーファイルに追加するか、プリコンパイル済みヘッダーファイルをソースファイルに含めた後に移動します。

## <a name="example-missing-header-file"></a>例: ヘッダーファイルがありません。

識別子を宣言するヘッダーファイルが含まれていません。 識別子の宣言が含まれているファイルが、それを使用するすべてのソースファイルに含まれていることを確認します。

```cpp
// C2065_header.cpp
// compile with: cl /EHsc C2065_header.cpp

//#include <stdio.h>
int main() {
    fpos_t file_position = 42; // C2065: 'fpos_t': undeclared identifier
    // To fix, uncomment the #include <stdio.h> line
    // to include the header where fpos_t is defined
}
```

また、initializer_list > ヘッダーを\<含めずに初期化子リストを使用した場合も考えられます。

```cpp
// C2065_initializer.cpp
// compile with: cl /EHsc C2065_initializer.cpp

// #include <initializer_list>
int main() {
    for (auto strList : {"hello", "world"})
        if (strList == "hello") // C2065: 'strList': undeclared identifier
            return 1;
    // To fix, uncomment the #include <initializer_list> line
}
```

、 `VC_EXTRALEAN` `WIN32_EXTRA_LEAN`、またはを定義した場合、Windows デスクトップアプリのソースファイルにこのエラーが表示されることがあります。 `WIN32_LEAN_AND_MEAN` これらのプリプロセッサマクロは、コンパイルを高速化するために\_、windows .h と afxv の一部のヘッダーファイルを除外します。 Windows .h と afxv_w32 を調べて、除外されている項目の最新の説明を確認します。

## <a name="example-missing-closing-quote"></a>例: 終わりの引用符がありません

このエラーは、文字列定数の後に終わりの引用符がない場合に発生する可能性があります。 これは、コンパイラを混同する簡単な方法です。 閉じた引用符がない場合は、報告されたエラーの場所の前に複数の行がある可能性があることに注意してください。

```cpp
// C2065_quote.cpp
// compile with: cl /EHsc C2065_quote.cpp
#include <iostream>

int main() {
    // Fix this issue by adding the closing quote to "Aaaa"
    char * first = "Aaaa, * last = "Zeee";
    std::cout << "Name: " << first
        << " " << last << std::endl; // C2065: 'last': undeclared identifier
}
```

## <a name="example-use-iterator-outside-for-loop-scope"></a>例: for ループスコープの外側で反復子を使用する

このエラーは、 `for`ループで反復子変数を宣言した後、 `for`ループのスコープ外でその反復子変数を使用しようとした場合に発生する可能性があります。 コンパイラは、既定で[/zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)コンパイラオプションを有効にします。 詳細については、「[デバッグ反復子のサポート](../../standard-library/debug-iterator-support.md)」を参照してください。

```cpp
// C2065_iter.cpp
// compile with: cl /EHsc C2065_iter.cpp
#include <iostream>
#include <string>

int main() {
    // char last = '!';
    std::string letters{ "ABCDEFGHIJKLMNOPQRSTUVWXYZ" };
    for (const char& c : letters) {
        if ('Q' == c) {
            std::cout << "Found Q!" << std::endl;
        }
        // last = c;
    }
    std::cout << "Last letter was " << c << std::endl; // C2065
    // Fix by using a variable declared in an outer scope.
    // Uncomment the lines that declare and use 'last' for an example.
    // std::cout << "Last letter was " << last << std::endl; // C2065
}
```

## <a name="example-preprocessor-removed-declaration"></a>例: 削除されたプリプロセッサ宣言

このエラーは、現在の構成用にコンパイルされていない、条件付きでコンパイルされたコード内にある関数または変数を参照している場合に発生する可能性があります。 これは、ビルド環境で現在サポートされていないヘッダーファイル内の関数を呼び出す場合にも発生することがあります。 特定のプリプロセッサマクロが定義されている場合にのみ、特定の変数または関数を使用できるようにするには、同じプリプロセッサマクロが定義されている場合にのみ、これらの関数を呼び出すコードをコンパイルできるようにします。 現在のビルド構成に必要なプリプロセッサマクロが定義されていない場合、関数の宣言はグレーで表示されるため、この問題は IDE で簡単に見つけることができます。

次に示すコードの例は、デバッグでビルドするときには機能しますが、リテールは使用できません。

```cpp
// C2065_defined.cpp
// Compile with: cl /EHsc /W4 /MT C2065_defined.cpp
#include <iostream>
#include <crtdbg.h>
#ifdef _DEBUG
    _CrtMemState oldstate;
#endif
int main() {
    _CrtMemDumpStatistics(&oldstate);
    std::cout << "Total count " << oldstate.lTotalCount; // C2065
    // Fix by guarding references the same way as the declaration:
    // #ifdef _DEBUG
    //    std::cout << "Total count " << oldstate.lTotalCount;
    // #endif
}
```

## <a name="example-ccli-type-deduction-failure"></a>例:C++/CLI 型推論の失敗

このエラーは、目的の型引数が使用されているパラメーターから推測できない場合に、ジェネリック関数を呼び出すと発生する可能性があります。 詳細については、「[ジェネリックC++関数 (/cli)](../../extensions/generic-functions-cpp-cli.md)」を参照してください。

```cpp
// C2065_b.cpp
// compile with: cl /clr C2065_b.cpp
generic <typename ItemType>
void G(int i) {}

int main() {
   // global generic function call
   G<T>(10);     // C2065
   G<int>(10);   // OK - fix with a specific type argument
}
```

## <a name="example-ccli-attribute-parameters"></a>例:C++/CLI 属性パラメーター

このエラーは、visual Studio 2005 で実行されたコンパイラ準拠作業の結果として生成されることもC++あります。これは、ビジュアル属性のパラメーターチェックです。

```cpp
// C2065_attributes.cpp
// compile with: cl /c /clr C2065_attributes.cpp
[module(DLL, name=MyLibrary)];   // C2065
// try the following line instead
// [module(dll, name="MyLibrary")];

[export]
struct MyStruct {
   int i;
};
```
