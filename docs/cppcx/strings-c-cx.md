---
title: 文字列 (C++/CX)
ms.date: 01/22/2017
ms.assetid: 5b34e1df-7c2b-4269-aba8-b767d36c49d9
ms.openlocfilehash: 8f7cbdd02cb1d38231c476ba939009a95533a046
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403244"
---
# <a name="strings-ccx"></a>文字列 (C++/CX)

C++ Windows ランタイム内のテキストが表される/cli によって CX、 [platform::string Class](../cppcx/platform-string-class.md)します。 使用して、 `Platform::String Class` Windows ランタイム クラス、メソッドに文字列を前後へ渡すとき、またはアプリケーション バイナリ インターフェイス (ABI) の境界を越えて他の Windows ランタイム コンポーネントと対話します。 `Platform::String Class` は、いくつかの一般的な文字列操作のメソッドを提供しますが、すべての機能を備えた文字列クラスとしては設計されていません。 C++ モジュールでは、重要なテキスト処理のために [wstring](../standard-library/basic-string-class.md) などの標準 C++ 文字列型を使用し、パブリック インターフェイスとの間でやり取りする前に、最終結果を [Platform::String^](../cppcx/platform-string-class.md) に変換します。 `wstring` または `wchar_t*` と `Platform::String`の間で変換することは簡単かつ効率的です。

**高速渡し**

場合によっては、コンパイラは基になる文字列データをコピーせずに `Platform::String` を安全に構築したり、 `String` を関数に渡したりできることを確認できます。 このような操作は *高速渡し* と呼ばれ、透過的に行われます。

## <a name="string-construction"></a>文字列の構築

`String` オブジェクトの値は、変更できない (読み取り専用) `char16` (16 ビット Unicode) 文字のシーケンスです。 `String` オブジェクトは変更できないため、 `String` 変数に新しい文字列リテラルを代入すると、元の `String` オブジェクトが新しい `String` オブジェクトで置き換えられます。 連結操作には、元の `String` オブジェクトの破棄と新しいオブジェクトの作成が含まれます。

**リテラル**

*リテラル文字* は単一引用符で囲まれた 1 文字で、 *リテラル文字列* は二重引用符で囲まれた文字のシーケンスです。 リテラルを使用して String^ 変数を初期化する場合、コンパイラはリテラルが `char16` 文字で構成されていると仮定します。 つまり、リテラルの前に文字列修飾子 'L' を挿入したり、 **_T()** または **TEXT()** マクロでリテラルを囲んだりする必要はありません。 C++ の Unicode サポートの詳細については、「 [Unicode Programming Summary](../text/unicode-programming-summary.md)」を参照してください。

次の例に、 `String` オブジェクトを構築するさまざまな方法を示します。

[!code-cpp[cx_strings#01](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#01)]

## <a name="string-handling-operations"></a>文字列処理の操作

`String` クラスは、文字列連結、文字列比較、その他の基本的な文字列操作のメソッドを提供します。 より広範囲の文字列操作を実行するには、 `String::Data()` メンバー関数を使用して、 `String^` として `const wchar_t*`オブジェクトの値を取得します。 そして、その値を使用して、豊富な文字列処理を提供する `std::wstring`を初期化します。

[!code-cpp[cx_strings#03](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#03)]

## <a name="string-conversions"></a>文字列変換

`Platform::String` には、 `char16` 文字または `NULL` 文字だけを含めることができます。 8 ビット文字を使用するアプリケーションがある場合、使用、 [string::data](../cppcx/platform-string-class.md#data)としてテキストを抽出する、`const wchar_t*`します。 そして、適切な Windows 関数または標準ライブラリ関数を使用してデータを操作し、データを `wchar_t*` または [wstring](../standard-library/basic-string-class.md)に戻します。これらを使用して、新しい `Platform::String`で表されます。

次のコードに、 `String^` 変数と `wstring` 変数の間で変換する方法を示します。 この例で使用される文字列操作の詳細については、「 [basic_string::replace](../standard-library/basic-string-class.md#replace)」を参照してください。

[!code-cpp[cx_strings#04](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#04)]

## <a name="string-length-and-embedded-null-values"></a>文字列の長さと埋め込み NULL 値

[String::length](../cppcx/platform-string-class.md#length)バイト数ではなく、文字列の文字の数を返します。 スタック セマンティクスを使用して文字列を構築すると、終端の NULL 文字は明示的に指定しない限りカウントされません。

`Platform::String` には埋め込み NULL 値を含めることができますが、連結演算の結果として NULL 値が含まれるときだけです。 埋め込み NULL は文字列リテラルではサポートされないため、 `Platform::String`を初期化するためにそのように埋め込まれた NULL は使用できません。 `Platform::String` 内の埋め込み NULL 値は、文字列が `TextBlock::Text` プロパティに割り当てられたときなど、文字列が表示されるときには無視されます。 埋め込み NULL は、文字列値が `Data` プロパティによって返されるときに削除されます。

## <a name="stringreference"></a>StringReference

場合によっては、コード (a) は、std::wstring または wchar_t 文字列または L""リテラル文字列、文字列を受け取るもう 1 つのメソッドに渡します ^ 入力パラメーターとして。 元の文字列バッファー自体が有効な状態にとどまり、関数が制御を返す前に変更されていない場合、 `wchar_t*` 文字列またはリテラル文字列を [Platform::StringReference](../cppcx/platform-stringreference-class.md)に変換し、 `Platform::String^`の代わりにそれを渡すことができます。 `StringReference` には、 `Platform::String^`に対するユーザー定義の変換があるため、この操作が許可されます。 `StringReference` を使用して、文字列データの余分なコピーを回避することもできます。 多数の文字列を渡すループの中や、非常に大きな文字列を渡す場合は、 `StringReference`を使用すると、パフォーマンスの大幅な向上を実現できる可能性があります。 ただし、 `StringReference` は基本的に元の文字列バッファーをそのまま利用するので、メモリの破損を防止するために十分注意する必要があります。 メソッドが制御を返すときに、元の文字列がスコープ内にあることが保証されている場合以外は、非同期メソッドに `StringReference` を渡さないでください。 2 番目の代入演算が発生した場合、StringReference によって初期化される String^ で、文字列データの割り当てとコピーが強制的に実行されます。 この場合、 `StringReference`が持つパフォーマンスの利点が失われます。

`StringReference` は ref クラスではなく、標準 C++ のクラス型であるため、定義した ref クラスのパブリック インターフェイス内で使用できないことに注意してください。

StringReference を使用する方法を次のコード例に示します。

```
void GetDecodedStrings(std::vector<std::wstring> strings)
{
    using namespace Windows::Security::Cryptography;
    using namespace Windows::Storage::Streams;

    for (auto&& s : strings)
    {
        // Method signature is IBuffer^ CryptographicBuffer::DecodeFromBase64String (Platform::String^)
        // Call using StringReference:
        IBuffer^ buffer = CryptographicBuffer::DecodeFromBase64String(StringReference(s.c_str()));

        //...do something with buffer
    }
}
```
