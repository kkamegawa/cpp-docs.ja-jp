---
title: コンパイラの警告 (レベル 3) C4996
description: コンパイラの警告 C4996 が発生する理由と、その対処方法について説明します。
ms.date: 11/25/2019
f1_keywords:
- C4996
helpviewer_keywords:
- C4996
ms.assetid: 926c7cc2-921d-43ed-ae75-634f560dd317
ms.openlocfilehash: 98662dc0b5439c1f8857e4f2ad259793a4d03e41
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898778"
---
# <a name="compiler-warning-level-3-c4996"></a>コンパイラの警告 (レベル 3) C4996

コードでは、*非推奨*とマークされている関数、クラスメンバー、変数、または typedef を使用します。 シンボルは、 [__declspec (非推奨)](../../cpp/deprecated-cpp.md)修飾子を使用して非推奨になりました。または、c++ 14 [\[\[非推奨の\]\]](../../cpp/attributes.md)属性で使用されています。 実際の C4996 警告メッセージは、宣言の `deprecated` 修飾子または属性によって指定されます。

> [!IMPORTANT]
> この警告は、常に、シンボルを宣言するヘッダーファイルの作成者からの意図的なメッセージです。 結果を理解することなく、非推奨のシンボルを使用しないでください。

## <a name="remarks"></a>Remarks

Visual Studio ライブラリの多くの関数、メンバー関数、テンプレート関数、およびグローバル変数は*非推奨*とされます。 POSIX や Microsoft 固有の関数などの一部は、現在、優先名が異なるため非推奨とされます。 一部の C ランタイムライブラリ関数は安全ではなく、より安全なバリアントがあるため、非推奨とされます。 他のユーザーは廃止されているため、非推奨となりました。 廃止されたメッセージには、通常、非推奨の関数またはグローバル変数の代替候補が含まれています。

## <a name="turn-off-the-warning"></a>警告をオフにする

C4996 の問題を解決するには、通常、コードを変更することをお勧めします。 代わりに、推奨される関数とグローバル変数を使用します。 移植性のために既存の関数または変数を使用する必要がある場合は、警告をオフにすることができます。

特定のコード行に対して警告をオフにするには、[警告](../../preprocessor/warning.md)プラグマの `#pragma warning(suppress : 4996)`を使用します。

ファイル内の警告をオフにするには、警告プラグマの `#pragma warning(disable : 4996)`を使用します。

コマンドラインビルドで警告をグローバルにオフにするには、 [/wd4996](../../build/reference/compiler-option-warning-level.md)コマンドラインオプションを使用します。

Visual Studio IDE でプロジェクト全体の警告をオフにするには、次のようにします。

1. プロジェクトの **[プロパティページ]** ダイアログを開きます。 [プロパティページ] ダイアログの使用方法の詳細については、「[プロパティページ](../../build/reference/property-pages-visual-cpp.md)」を参照してください。

1. **[構成プロパティ]**  > [ **CC++ /**  > **詳細設定**] ページを選択します。

1. `4996`を追加するには、[**特定の警告を無効**にする] プロパティを編集します。 **[OK]** を選択して変更を適用します。

また、プリプロセッサマクロを使用して、ライブラリで使用されている特定の特定のクラスの非推奨の警告を無効にすることもできます。 これらのマクロについて以下に説明します。

Visual Studio でプリプロセッサマクロを定義するには、次のようにします。

1. プロジェクトの **[プロパティページ]** ダイアログを開きます。 [プロパティページ] ダイアログの使用方法の詳細については、「[プロパティページ](../../build/reference/property-pages-visual-cpp.md)」を参照してください。

1. **構成プロパティ > CC++ /> プリプロセッサ** の順に展開します。

1. **[プリプロセッサの定義]** プロパティで、マクロ名を追加します。 **[OK]** を選んで保存し、プロジェクトをリビルドします。

特定のソースファイルでのみマクロを定義するには、ヘッダーファイルを含む行の前に、`#define EXAMPLE_MACRO_NAME` などの行を追加します。

次に、C4996 の警告とエラーの一般的な原因をいくつか示します。

## <a name="posix-function-names"></a>POSIX 関数名

**この項目の POSIX 名は非推奨とされます。代わりに、ISO C とC++準拠した名前を使用**します。*新しい名前*。 **詳細については、オンラインヘルプを参照してください。**

Microsoft は、一部の POSIX および Microsoft 固有のライブラリ関数を、予約済みおよびグローバル実装定義名に対する C99 および C++ 03 制約に準拠するように名前変更しました。 *関数自体ではなく、名前のみが非推奨とされ*ます。 ほとんどの場合、準拠する名前を作成するために、関数名に先頭のアンダースコアが追加されています。 コンパイラは、元の関数名に対して非推奨の警告を発行し、優先名を提案します。

この問題を解決するには、通常、推奨される関数名を代わりに使用するようにコードを変更することをお勧めします。 ただし、更新された名前は Microsoft 固有です。 移植性のために既存の関数名を使用する必要がある場合は、これらの警告をオフにすることができます。 これらの関数は、ライブラリ内の元の名前の下でも使用できます。

これらの関数の非推奨の警告をオフにするには、プリプロセッサマクロ **\_CRT\_NONSTDC\_no\_警告**を定義します。 このマクロは、コマンドラインでオプション `/D_CRT_NONSTDC_NO_WARNINGS`を含めることによって定義できます。

## <a name="unsafe-crt-library-functions"></a>Unsafe CRT ライブラリ関数

**この関数または変数は安全でない可能性があります。** 代わりに *、セーフバージョン*を使用することを検討してください **。廃止を無効にするには、\_CRT\_セキュリティで保護された\_\_警告を使用しないようにします。 詳細については、オンラインヘルプを参照してください。**

Microsoft では、よりC++安全なバージョンを使用できるため、一部の CRT 関数と標準ライブラリ関数およびグローバル変数は非推奨となりました。 非推奨の関数のほとんどでは、バッファーへの読み取りまたは書き込みアクセスがチェックされません。 誤用によって、セキュリティ上の深刻な問題が発生する可能性があります。 コンパイラは、これらの関数は使用されなくなったとの警告を発し、優先関数を提案します。

この問題を解決するには、代わりに関数または変数の*安全なバージョン*を使用することをお勧めします。 場合によっては、移植性や下位互換性の理由ではできないことがあります。 コード内でバッファーの上書きまたは過度な読み取りが発生しないことを慎重に確認してください。 その後、警告をオフにすることができます。

CRT でこれらの関数の非推奨の警告をオフにするには **\_crt\_セキュリティで保護された\_\_警告**を定義します。

非推奨のグローバル変数に関する警告をオフにするには **\_CRT\_セキュリティで保護された\_\_警告\_GLOBALS**を定義します。

これらの非推奨の関数とグローバルの詳細については、「 [CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」および「[安全なライブラリ: C++標準ライブラリ](../../standard-library/safe-libraries-cpp-standard-library.md)」を参照してください。

## <a name="unsafe-standard-library-functions"></a>安全でない標準ライブラリ関数

__' std::__ *function_name* __::\_Unchecked\_の反復子::\___ は、安全でない可能性のあるパラメーターを使用した std::*function_name*の呼び出しを避け**ます。この呼び出しは、渡された値が正しいことを確認するために呼び出し元に依存します。この警告を無効にするには、-D\_SCL\_セキュリティで保護された\_\_警告は使用しません。C++ Visual ' チェックされた反復子の使用方法に関するドキュメントを参照してください**

この警告は、一部C++の標準ライブラリのテンプレート関数ではパラメーターが正しいかどうかのチェックが行われないため、デバッグビルドに表示されます。 多くの場合、コンテナーの境界を確認するために関数で使用できる情報が不足していることが原因です。 または、反復子が関数で不適切に使用されている可能性があります。 この警告は、これらの関数を識別するのに役立ちます。これは、プログラムに重大なセキュリティホールがある可能性があるためです。 詳細については、「チェックを行う[反復子](../../standard-library/checked-iterators.md)」を参照してください。

たとえば、この警告は、プレーン配列ではなく `std::copy`に要素ポインターを渡すと、デバッグモードで表示されます。 この問題を解決するには、適切に宣言された配列を使用して、ライブラリが配列の範囲を確認し、境界のチェックを実行できるようにします。

```cpp
// C4996_copyarray.cpp
// compile with: cl /c /W4 /D_DEBUG C4996_copyarray.cpp
#include <algorithm>

void example(char const * const src) {
    char dest[1234];
    char * pdest3 = dest + 3;
    std::copy(src, src + 42, pdest3); // C4996
    std::copy(src, src + 42, dest);   // OK, copy can tell that dest is 1234 elements
}
```

C++ 14 では、いくつかの標準ライブラリアルゴリズムが "デュアル範囲" バージョンに更新されました。 2つの範囲のバージョンを使用する場合、2番目の範囲は必要な範囲チェックを行います。

```cpp
// C4996_containers.cpp
// compile with: cl /c /W4 /D_DEBUG C4996_containers.cpp
#include <algorithm>

bool example(
    char const * const left,
    const size_t leftSize,
    char const * const right,
    const size_t rightSize)
{
    bool result = false;
    result = std::equal(left, left + leftSize, right); // C4996
    // To fix, try this form instead:
    // result = std::equal(left, left + leftSize, right, right + rightSize); // OK
    return result;
}
```

この例では、標準ライブラリを使用して反復子の使用法を確認する方法をいくつか示します。また、チェックをオフにした場合には危険な場合があります。

```cpp
// C4996_standard.cpp
// compile with: cl /EHsc /W4 /MDd C4996_standard.cpp
#include <algorithm>
#include <array>
#include <iostream>
#include <iterator>
#include <numeric>
#include <string>
#include <vector>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    vector<int> v(16);
    iota(v.begin(), v.end(), 0);
    print("v: ", v);

    // OK: vector::iterator is checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    vector<int> v2(16);
    transform(v.begin(), v.end(), v2.begin(), [](int n) { return n * 2; });
    print("v2: ", v2);

    // OK: back_insert_iterator is marked as checked in debug mode
    // (i.e. an overrun is impossible)
    vector<int> v3;
    transform(v.begin(), v.end(), back_inserter(v3), [](int n) { return n * 3; });
    print("v3: ", v3);

    // OK: array::iterator is checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    array<int, 16> a4;
    transform(v.begin(), v.end(), a4.begin(), [](int n) { return n * 4; });
    print("a4: ", a4);

    // OK: Raw arrays are checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    // NOTE: This applies only when raw arrays are
    // given to C++ Standard Library algorithms!
    int a5[16];
    transform(v.begin(), v.end(), a5, [](int n) { return n * 5; });
    print("a5: ", a5);

    // WARNING C4996: Pointers cannot be checked in debug mode
    // (i.e. an overrun triggers undefined behavior)
    int a6[16];
    int * p6 = a6;
    transform(v.begin(), v.end(), p6, [](int n) { return n * 6; });
    print("a6: ", a6);

    // OK: stdext::checked_array_iterator is checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    int a7[16];
    int * p7 = a7;
    transform(v.begin(), v.end(),
        stdext::make_checked_array_iterator(p7, 16),
        [](int n) { return n * 7; });
    print("a7: ", a7);

    // WARNING SILENCED: stdext::unchecked_array_iterator
    // is marked as checked in debug mode, but it performs no checking,
    // so an overrun triggers undefined behavior
    int a8[16];
    int * p8 = a8;
    transform( v.begin(), v.end(),
        stdext::make_unchecked_array_iterator(p8),
        [](int n) { return n * 8; });
    print("a8: ", a8);
}
```

コードでバッファーオーバーランエラーが発生しないことを確認した場合は、この警告をオフにすることができます。 これらの関数の警告をオフにするには **\_SCL\_セキュリティで保護された\_\_警告**を定義します。

## <a name="checked-iterators-enabled"></a>チェックを行う反復子有効

また、`_ITERATOR_DEBUG_LEVEL` が1または2として定義されている場合に、チェックを行う反復子を使用しないと、C4996 も発生する可能性があります。 これは、デバッグモードのビルドでは既定で2に設定され、リテールビルドの場合は0に設定されます。 詳細については、「チェックを行う[反復子](../../standard-library/checked-iterators.md)」を参照してください。

```cpp
// C4996_checked.cpp
// compile with: /EHsc /W4 /MDd C4996_checked.cpp
#define _ITERATOR_DEBUG_LEVEL 2

#include <algorithm>
#include <iterator>

using namespace std;
using namespace stdext;

int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 10, 11, 12 };
    copy(a, a + 3, b + 1);   // C4996
    // try the following line instead:
    // copy(a, a + 3, checked_array_iterator<int *>(b, 3));   // OK
}
```

## <a name="unsafe-mfc-or-atl-code"></a>Unsafe MFC または ATL コード

C4996 は、セキュリティ上の理由から非推奨とされた MFC 関数または ATL 関数を使用した場合に発生する可能性があります。

この問題を解決するには、代わりに更新された関数を使用するようにコードを変更することを強くお勧めします。

これらの警告を抑制する方法の詳細については、「 [_AFX_SECURE_NO_WARNINGS](../../mfc/reference/diagnostic-services.md#afx_secure_no_warnings)」を参照してください。

## <a name="obsolete-crt-functions-and-variables"></a>廃止された CRT 関数と変数

**この関数または変数は、新しいライブラリまたはオペレーティングシステムの機能に置き換えられました。代わりに new_item の使用を検討**してください **。詳細については、オンラインヘルプを参照してください。**

一部のライブラリ関数およびグローバル変数は非推奨とされるため使用されていません。 これらの関数および変数は、将来のバージョンのライブラリでは削除される可能性があります。 コンパイラは、これらの項目は使用されなくなったとの警告を発行し、優先すべき代替項目を提案します。

この問題を解決するには、推奨される関数または変数を使用するようにコードを変更することをお勧めします。

これらの項目について非推奨の警告をオフにするには **\_CRT\_廃止\_\_警告**は定義しません。 詳しくは、非推奨の関数または変数のドキュメントをご覧ください。

## <a name="marshaling-errors-in-clr-code"></a>CLR コードのマーシャリングエラー

C4996 は、CLR マーシャリングライブラリを使用するときにも発生する可能性があります。 この場合、C4996 はエラーであり、警告ではありません。 このエラーは、 [marshal_as](../../dotnet/marshal-as.md)を使用して、 [marshal_context クラス](../../dotnet/marshal-context-class.md)を必要とする2つのデータ型の間で変換を行う場合に発生します。 また、マーシャリングライブラリが変換をサポートしていない場合にも、このエラーが発生することがあります。 マーシャリングライブラリの詳細については、「 [」 C++の「マーシャリングの概要](../../dotnet/overview-of-marshaling-in-cpp.md)」を参照してください。

この例では、マーシャリングライブラリが `System::String` から `const char *`に変換するコンテキストを必要とするため、C4996 が生成されます。

```cpp
// C4996_Marshal.cpp
// compile with: /clr
// C4996 expected
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   String^ message = gcnew String("Test String to Marshal");
   const char* result;
   result = marshal_as<const char*>( message );
   return 0;
}
```

## <a name="example-user-defined-deprecated-function"></a>例: ユーザー定義の非推奨の関数

特定の関数の使用が推奨されなくなったときに、独自のコードで非推奨の属性を使用して、呼び出し元に警告することができます。 この例では、C4996 は、非推奨の関数が宣言されている行と、関数が使用されている行の2つの場所で生成されます。

```cpp
// C4996.cpp
// compile with: /W3
// C4996 warning expected
#include <stdio.h>

// #pragma warning(disable : 4996)
void func1(void) {
   printf_s("\nIn func1");
}

[[deprecated]]
void func1(int) {
   printf_s("\nIn func2");
}

int main() {
   func1();
   func1(1);    // C4996
}
```
