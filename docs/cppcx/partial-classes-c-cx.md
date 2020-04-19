---
title: 部分クラス (C++/CX)
ms.date: 12/30/2016
ms.assetid: 69d93575-636c-4564-8cca-6dfba0c7e328
ms.openlocfilehash: 703f12498e0f2c68448e2b3896d3d5f906aba779
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740473"
---
# <a name="partial-classes-ccx"></a>部分クラス (C++/CX)

部分クラスは、ユーザーがクラス定義の一部を変更するのと同時に、XAML デザイナーなどの自動コード生成ソフトウェアも同じクラスのコードを変更するようなシナリオをサポートする構造体です。 部分クラスを使用することにより、デザイナーがコードを上書きすることを防ぐことができます。 Visual Studio プロジェクトでは、生成されたファイルに `partial` 修飾子が自動的に適用されます。

## <a name="syntax"></a>構文

部分クラスを定義するには、通常のクラス定義のクラス キーの直前に `partial` キーワードを使用します。 `partial ref class` などのキーワードは、空白文字を含むコンテキスト キーワードです。 部分定義は、次の構造体でサポートされています。

- `class` または `struct`

- `ref class` または `ref struct`

- `value class` または `value struct`

- `enum` または `enum class`

- `ref interface`、 `interface class`、 `interface struct`、または `__interface`

- `union`

この例は、部分的な `ref class`を示しています。

[!code-cpp[cx_partial#01](../cppcx/codesnippet/CPP/partialclassexample/class1.h#01)]

## <a name="contents"></a>目次

部分クラス定義には、 `partial` キーワードを省略した場合に完全クラス定義に含めることができるすべてのものを含めることができます。 1 つの例外を除き、これには、基底クラス、データ メンバー、メンバー関数、列挙体、フレンド宣言、および属性など、任意の有効な構造体が含まれます。 また、静的データ メンバーのインライン定義が許可されています。

1 つの例外は、クラス アクセシビリティです。 たとえば、 `public partial class MyInvalidClass {/* ... */};` ステートメントはエラーです。 MyInvalidClass の部分クラス定義で使用されるいずれのアクセス指定子も、それ以降の MyInvalidClass の部分クラス定義または完全クラス定義の既定のアクセシビリティに影響しません。

次のコード片は、アクセシビリティを示しています。 最初の部分クラスでは、アクセシビリティがパブリックであるため、 `Method1` もパブリックです。 2 番目の部分クラスでは、既定のクラス アクセシビリティがプライベートであるため、 `Method2` もプライベートです。

[!code-cpp[cx_partial#02](../cppcx/codesnippet/CPP/partialclassexample/class1.h#02)]

## <a name="declaration"></a>宣言

*MyClass* などのクラスの部分定義は、MyClass の単なる宣言にすぎません。 つまり、 *MyClass*という名前のみ説明します。 *MyClass* は、クラス定義を必要とする方法では使用できません。たとえば、 *MyClass* のサイズがわかっている場合や *MyClass*の基底クラスまたはメンバーを使用する場合です。 *MyClass* は、コンパイラが部分定義ではない *MyClass*の定義を検出した場合のみ、定義されていると見なされます。

次の例は、部分クラスの宣言の動作を示しています。 宣言 #1 の後で、 *MyClass* があたかも事前宣言 `ref class MyClass;`として記述されているかのように、このクラスを使用することができます。 宣言 #2 は宣言 #1 と等価です。宣言 #3 は、クラスに対する事前宣言であるため有効です。 ただし、宣言 #4 は、

*MyClass* が完全に定義されていないため無効です。

宣言 #5 は `partial` キーワードを使用しません。また、この宣言は、 *MyClass*を完全に定義します。 その結果、宣言 #6 は有効です。

[!code-cpp[Cx_partial#03](../cppcx/codesnippet/CPP/partialclassexample/class1.h#03)]

## <a name="number-and-ordering"></a>数字と順序

1 つのクラスの完全定義には、0 個またはそれ以上の部分クラス定義を持たせることができます。

1 つのクラスに関する部分クラス定義のそれぞれは、構文上、そのクラスに関する 1 つの完全定義より前に記述する必要がありますが、そのクラスの事前宣言より前に記述する必要はありません。 クラスの完全定義がない場合、部分クラス宣言に指定できるのは事前宣言のみです。

`class` や `struct` などのすべてのクラス キーは一致する必要があります。 たとえば、 `partial class X {}; struct X {};`という名前のみ説明します。

次の例は、数字と順序を示しています。 最後の部分宣言は、クラスが既に定義されているため失敗します。

[!code-cpp[cx_partial#04](../cppcx/codesnippet/CPP/partialclassexample/class1.h#04)]

## <a name="full-definition"></a>完全定義

クラス X の完全定義の点で、動作は、X の定義にすべての基底クラスやメンバーなどが、部分クラスで検出および定義されている順序で宣言されている場合のようになります。 つまり、部分クラスの内容は、クラスの完全定義の点で記述されているかのように処理されます。また名前参照および他の言語規則は、部分クラスの内容がその場所に記述されているかのように、クラスの完全定義の点で適用されます。

次の 2 つのコード例には、同じ意味と効果があります。 最初の例は部分クラスを使用し、2 番目の例は部分クラスを使用しません。

[!code-cpp[cx_partial#05](../cppcx/codesnippet/CPP/partialclassexample/class1.h#05)]

[!code-cpp[cx_partial#06](../cppcx/codesnippet/CPP/partialclassexample/class1.h#06)]

## <a name="templates"></a>テンプレート

部分クラスをテンプレートとして指定することはできません。

## <a name="restrictions"></a>制約

部分クラスが、1 つの翻訳単位の範囲を越えることはできません。

`partial` キーワードは、 `ref class` キーワードまたは `value class` キーワードと組み合わせた場合のみサポートされます。

### <a name="examples"></a>使用例

次の例では、2 つのコード ファイルにまたがって `Address` クラスを定義しています。 デザイナーは `Address.details.h` を変更し、ユーザーは `Address.h`を変更します。 最初のファイルのクラス定義のみ、 `partial` キーワードを使用します。

[!code-cpp[cx_partial#07](../cppcx/codesnippet/CPP/partialclassexample/address.details.h#07)]

[!code-cpp[cx_partial#09](../cppcx/codesnippet/CPP/partialclassexample/address.h#09)]

## <a name="see-also"></a>関連項目

[型システム](../cppcx/type-system-c-cx.md)<br/>
[C++/CX 言語リファレンス](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[名前空間参照](../cppcx/namespaces-reference-c-cx.md)
