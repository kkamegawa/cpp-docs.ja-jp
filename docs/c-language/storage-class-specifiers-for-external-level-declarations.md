---
title: 外部レベル宣言のストレージ クラス指定子
ms.date: 11/04/2016
helpviewer_keywords:
- external definitions
- linkage [C++], external
- external linkage, variable declarations
- declaring variables, external variables
- declarations [C++], external
- declarations [C++], specifiers
- external declarations
- static variables, external declarations
- variables, visibility
- external linkage, storage-class specifiers
- referencing declarations
- visibility, variables
- static storage class specifiers
ms.assetid: b76b623a-80ec-4d5d-859b-6cef422657ee
ms.openlocfilehash: 941994f668fa035b569f9ccae2c301ebf42bcda6
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152080"
---
# <a name="storage-class-specifiers-for-external-level-declarations"></a>外部レベル宣言のストレージ クラス指定子

外部変数はファイル スコープの変数です。 これらは、関数の外部で定義され、多くの関数に使用できる可能性があります。 関数は外部レベルでのみ定義できるため、入れ子にできません。 既定では、同じ名前の外部変数と関数へのすべての参照は、同じオブジェクトへの参照であり、"外部リンケージ" が含まれていることを意味します  (**static** キーワードを使用して、これをオーバーライドできます。 **static** の詳細については、このセクションで後述する情報をご覧ください)。

外部レベルの変数宣言は、変数の定義 ("宣言の定義") または別の場所で定義された変数の参照 ("宣言の参照") です。

変数も初期化する (暗黙的または明示的に) 外部変数宣言は、変数の定義宣言です。 外部レベルの定義は複数の形式にすることができます。

- **static** のストレージ クラス指定子で宣言する変数。 「[初期化](../c-language/initialization.md)」に説明されているように、定数式で **static** 変数を明示的に初期化できます。 初期化子を省略すると、変数は既定で 0 に初期化されます。 たとえば、次の 2 つのステートメントはどちらも変数 `k` の定義と見なされます。

    ```
    static int k = 16;
    static int k;
    ```

- 外部レベルで明示的に初期化する変数。 たとえば、`int j = 3;` は変数 `j` の定義です。

外部レベル (つまり、全関数の外側) の変数宣言では、**static** または `extern` ストレージ クラス指定子を使用するか、ストレージ クラス指定子を完全に省略できます。 外部レベルで **auto** と **register** *storage-class-specifier* 終端要素を使用することはできません。

外部レベルで変数を定義すると、その変数は翻訳単位の残りの部分全体にわたって参照できます。 変数は、同じソース ファイルでの宣言に先立って表示されません。 また、以下で説明するように、参照宣言が表示されるようにしない限り、プログラムの他のソース ファイルに表示されません。

**static** に関する規則には以下が含まれます。

- **static** キーワードなしですべてのブロックの外側で宣言された変数は、プログラム全体を通して常に値を保持します。 特定の翻訳単位へのアクセスを制限するには、**static** キーワードを使用する必要があります。 これによって、"内部リンケージ" が設定されます。 プログラム全体でグローバルにするには、明示的なストレージ クラスを省略するか、キーワード `extern` を使用します (次の一覧の規則を参照してください)。 これによって、"外部リンケージ" が設定されます。 内部リンケージおよび外部リンケージは「[Linkage (リンケージ)](../c-language/linkage.md)」でも説明します。

- プログラム内で 1 回だけ、外部レベルで変数を定義できます。 同じ名前と、別の翻訳単位の **static** ストレージ クラスの指定子を持つ別の変数を定義できます。 各 **static** 定義は独自の翻訳単位内だけで参照できるため、競合は発生しません。 これによって、1 つの翻訳単位内の関数間では共有され、他の翻訳単位からは参照されない識別子名を、簡単に隠すことができます。

- **static** ストレージ クラス指定子は、関数にも適用できます。 関数 **static** を宣言する場合、その名前は宣言されているファイルの外部には表示されません。

`extern` を使用するための規則は次のとおりです。

- `extern` ストレージ クラス指定子は、他の場所で定義された変数への参照を宣言します。 `extern` 宣言を使用して、別のソース ファイルでの定義を表示するか、同じソース ファイルで変数の定義前にその変数を表示することができます。 外部レベルで変数への参照を宣言すると、その変数は、宣言した参照が発生する翻訳単位の残りの部分全体で参照できます。

- `extern` 参照を有効にするには、参照する変数は 1 回だけ外部レベルで定義する必要があります。 この定義 (`extern` ストレージ クラスを含まない) は、プログラムを構成する任意の翻訳単位内で行うことができます。

## <a name="example"></a>例

次の例では外部宣言を示します。

```
/******************************************************************
                      SOURCE FILE ONE
*******************************************************************/
#include <stdio.h>

extern int i;                // Reference to i, defined below
void next( void );           // Function prototype

int main()
{
    i++;
    printf_s( "%d\n", i );   // i equals 4
    next();
}

int i = 3;                  // Definition of i

void next( void )
{
    i++;
    printf_s( "%d\n", i );  // i equals 5
    other();
}

/******************************************************************
                      SOURCE FILE TWO
*******************************************************************/
#include <stdio.h>

extern int i;              // Reference to i in
                           // first source file
void other( void )
{
    i++;
    printf_s( "%d\n", i ); // i equals 6
}
```

この例の 2 つのソース ファイルには、`i` の 3 つの外部宣言の合計が含まれます。 1 つの宣言だけが "定義宣言" となります。 この宣言

```
int i = 3;
```

によって、グローバル変数 `i` が定義され、初期値 3 で初期化されます。 `i` を使用している最初のソース ファイルの最上部にある `extern` の "参照" 宣言は、ファイルの定義宣言の前にグローバル変数を参照できるようにします。 また、2 番目のソース ファイルの `i` の参照宣言は、そのソース ファイルで変数を表示します。 変数の定義インスタンスが翻訳単位で提供されていない場合、コンパイラは次があるものと見なします。

```
extern int x;
```

参照宣言と定義参照

```
int x = 0;
```

プログラムの別の翻訳単位に表示されます。

3 つの関数 `main`、`next`、および `other` はすべて、同じタスクを実行します。これらは `i` を増やし、それを出力します。 値 4、5、および 6 が出力されます。

変数 `i` が初期化されていない場合は、自動的に 0 に設定されます。 この場合、値 1、2、および 3 が出力されています。 変数の初期化については、「[初期化](../c-language/initialization.md)」をご覧ください。

## <a name="see-also"></a>関連項目

[C ストレージ クラス](../c-language/c-storage-classes.md)
