---
title: 宣言と定義 (C++)
ms.date: 12/12/2019
ms.assetid: 678f1424-e12f-45e0-a957-8169e5fef6cb
ms.openlocfilehash: d52294b635e05f42a4c48620214a90cad609f575
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301549"
---
# <a name="declarations-and-definitions-c"></a>宣言と定義 (C++)

プログラムC++は、変数、関数、型、名前空間などのさまざまなエンティティで構成されます。 これらの各エンティティは、使用する前に*宣言*する必要があります。 宣言は、エンティティの一意の名前と、その型およびその他の特性に関する情報を指定します。 C++名前が宣言されているポイントは、コンパイラに表示される位置です。 コンパイル単位の後の時点で宣言されている関数またはクラスを参照することはできません。 変数は、使用されるポイントの前にできるだけ近いものとして宣言する必要があります。

次の例は、いくつかの宣言を示しています。

```cpp
#include <string>

void f(); // forward declaration

int main()
{
    const double pi = 3.14; //OK
    int i = f(2); //OK. f is forward-declared
    std::string str; // OK std::string is declared in <string> header
    C obj; // error! C not yet declared.
    j = 0; // error! No type specified.
    auto k = 0; // OK. type inferred as int by compiler.
}

int f(int i)
{
    return i + 42;
}

namespace N {
   class C{/*...*/};
}
```

5行目では、`main` 関数が宣言されています。 7行目では、`pi` という名前の**const**変数が宣言および*初期化*されます。 8行目では、整数 `i` が宣言され、関数 `f`によって生成される値で初期化されます。 `f` 名前は、3行目の*事前宣言*によってコンパイラから参照できます。 

9行目では、`C` 型の `obj` という名前の変数が宣言されています。 ただし、`C` はプログラムの後半まで宣言されておらず、前方宣言されていないため、この宣言ではエラーが発生します。 このエラーを解決するには、`main` する前に `C` の*定義*全体を移動するか、事前宣言を追加します。 この動作は、などC#の他の言語とは異なります。この場合、関数とクラスは、ソースファイル内の宣言の時点よりも前に使用できます。 

10行目では、`std::string` 型の `str` という名前の変数が宣言されています。 `std::string` 名前は、行1のソースファイルにマージされる `string`[ヘッダーファイル](header-files-cpp.md)に導入されるため、表示されます。 `std` は、`string` クラスが宣言されている名前空間です。

11行目では、`j` 名前が宣言されていないため、エラーが発生します。 宣言は、javaScript などの他の言語とは異なり、型を提供する必要があります。 12行目では、`auto` キーワードが使用されます。これは、初期化された値に基づいて `k` の型を推論するようにコンパイラに指示します。 この場合、コンパイラは型の `int` を選択します。  

## <a name="declaration-scope"></a>宣言のスコープ

宣言によって導入される名前は、宣言が行われる*スコープ*内で有効です。 前の例では、`main` 関数内で宣言されている変数は*ローカル変数*です。 `i` という名前の別の変数は、*グローバルスコープ*で main の外部に宣言することができ、完全に独立したエンティティになります。 ただし、このような名前の重複によって、プログラマの混乱やエラーが発生する可能性があるため、回避する必要があります。 21行目では、クラス `C` が名前空間 `N`のスコープ内で宣言されています。 名前空間を使用すると、*名前の競合*を回避できます。 ほとんどC++の標準ライブラリ名は `std` 名前空間内で宣言されます。 スコープ規則と宣言の相互作用の詳細については、「[スコープ](../cpp/scope-visual-cpp.md)」を参照してください。

## <a name="definitions"></a>定義

関数、クラス、列挙型、定数変数を含む一部のエンティティは、宣言されるだけでなく、定義する必要があります。 *定義*により、プログラムの中でエンティティが使用されている場合にコンピューターコードを生成するために必要なすべての情報がコンパイラに提供されます。 前の例では、行3に関数 `f` の宣言が含まれていますが、関数の*定義*は 15 ~ 18 行目で提供されています。 21行目では、クラス `C` が宣言および定義されています (定義されているように、クラスは何も実行しません)。 定数変数は、その変数が宣言されているのと同じステートメント内で、値が割り当てられている他の単語に定義されている必要があります。 `int` などの組み込み型の宣言は、自動的に定義されます。これは、コンパイラが割り当てられる領域の量を認識するためです。

次の例は、定義でもある宣言を示しています。

```cpp
// Declare and define int variables i and j.
int i;
int j = 10;

// Declare enumeration suits.
enum suits { Spades = 1, Clubs, Hearts, Diamonds };

// Declare class CheckBox.
class CheckBox : public Control
{
public:
    Boolean IsChecked();
    virtual int     ChangeState() = 0;
};
```

定義ではない宣言をいくつか次に示します。

```cpp
extern int i;
char *strchr( const char *Str, const char Target );
```

## <a name="typedefs-and-using-statements"></a>Typedef と using ステートメント

以前のバージョンのC++では、 [typedef](aliases-and-typedefs-cpp.md)キーワードを使用して、別の名前の*エイリアス*である新しい名前を宣言しています。 たとえば `std::string` 型は `std::basic_string<char>`の別の名前です。 プログラマは、実際の名前ではなく typedef 名を使用するのが明らかです。 現代C++では、 [using](aliases-and-typedefs-cpp.md)キーワードは typedef よりも優先されますが、考え方は同じです。新しい名前は、既に宣言および定義されているエンティティに対して宣言されています。

## <a name="static-class-members"></a>静的クラスメンバー

静的クラスのデータメンバーは、クラスのすべてのオブジェクトによって共有される個別の変数であるため、クラス定義の外部で定義および初期化する必要があります。 (詳細については、「[クラス](../cpp/classes-and-structs-cpp.md)」を参照してください)。

## <a name="extern-declarations"></a>extern 宣言

プログラムC++には、複数の[コンパイル単位](header-files-cpp.md)を含めることができます。 個別のコンパイル単位で定義されたエンティティを宣言するには、 [extern](extern-cpp.md)キーワードを使用します。 宣言内の情報はコンパイラに対して十分ですが、リンク手順でエンティティの定義が見つからない場合は、リンカーによってエラーが発生します。

## <a name="in-this-section"></a>このセクションの内容

[ストレージ クラス](storage-classes-cpp.md)<br/>
[const](const-cpp.md)<br/>
[constexpr](constexpr-cpp.md)<br/>
[extern](extern-cpp.md)<br/>
[初期化子](initializers.md)<br/>
[エイリアスと typedef](aliases-and-typedefs-cpp.md)<br/>
[宣言の使用](using-declaration.md)<br/>
[volatile](volatile-cpp.md)<br/>
[decltype](decltype-cpp.md)<br/>
[属性C++](attributes.md)<br/>

## <a name="see-also"></a>関連項目

[基本的な概念](../cpp/basic-concepts-cpp.md)<br/>
