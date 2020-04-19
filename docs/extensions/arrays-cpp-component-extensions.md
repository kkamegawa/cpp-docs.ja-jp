---
title: 配列 (C++/CLI および C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- cli::array
- details::array
- lang::array
helpviewer_keywords:
- array keyword [C++]
- arrays [C++], multidimensional
- multidimensional arrays
- arrays [C++]
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
ms.openlocfilehash: e4173c16e13c08a54b36e42183e6e18b6ed4fdc2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516197"
---
# <a name="arrays-ccli-and-ccx"></a>配列 (C++/CLI および C++/CX)

C++/CX の `Platform::Array<T>` 型、または C++/CLI の **array** キーワードは、指定された型と初期値の配列を宣言します。

## <a name="all-platforms"></a>すべてのプラットフォーム

配列は、宣言内で終わり山かっこ (>) の後ろに、ハンドルへのオブジェクト (^) 修飾子を使用して宣言する必要があります。
配列の要素の数は型の一部ではありません。 1 つの配列変数で、異なるサイズの配列を参照できます。

標準 C++ とは異なり、添字演算はポインターの算術演算と同義ではなく、交換可能ではありません。

配列の詳細については、以下を参照してください。

- [方法: C++/CLI で配列を使用する](../dotnet/how-to-use-arrays-in-cpp-cli.md)

- [可変個引数リスト (...) (C++/CLI)](variable-argument-lists-dot-dot-dot-cpp-cli.md)

## <a name="windows-runtime"></a>Windows ランタイム

配列は、`Platform` 名前空間のメンバーです。 配列は、1 次元のみが可能です。

### <a name="syntax"></a>構文

構文の最初の例では、**ref new** 集計キーワードを使用して配列を割り当てます。 2 番目の例では、ローカル配列を宣言します。

```cpp
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier =
    ref new[Platform::]Array<initialization-type> [{initialization-list [,...]}]

[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier =
    {initialization-list [,...]}
```

*qualifiers*<br/>
(省略可能) 1 つ以上の次のストレージ クラス指定子: [mutable](../cpp/mutable-data-members-cpp.md)、[volatile](../cpp/volatile-cpp.md)、[const](../cpp/const-cpp.md)、[extern](../cpp/using-extern-to-specify-linkage.md)、[static](../cpp/static-members-cpp.md)。

*array-type*<br/>
配列変数の型。 有効な型は、Windows ランタイム クラスと基本型、ref クラスと構造体、値クラスと構造体、およびネイティブ ポインター (`type*`) です。

*rank*<br/>
(省略可能) 配列の次元の数。 1 にする必要があります。

*identifier*<br/>
配列変数の名前。

*initialization-type*<br/>
配列を初期化する値の型。 通常、*array-type* と *initialization-type* には同じ型を指定します。 ただし、*initialization-type* から *array-type* への変換がある場合は、異なる型を指定できます (たとえば *initialization-type* が *array-type* から派生する場合)。

*initialization-list*<br/>
(省略可能) 配列の要素を初期化する、中かっこ内のコンマ区切りの値の一覧。 たとえば、*rank-size-list* が `(3)` の場合 (3 つの要素の 1 次元配列を宣言しています)、*initialization-list* には `{1,2,3}` を指定できます。

### <a name="remarks"></a>解説

コンパイル時に、型が `__is_ref_array(type)` の参照カウント配列かどうかを検出できます。 詳細については、「[型の特徴のコンパイラ サポート](compiler-support-for-type-traits-cpp-component-extensions.md)」を参照してください。

### <a name="requirements"></a>要件

コンパイラ オプション: `/ZW`

### <a name="examples"></a>使用例

次の例では、100 個の要素がある 1 次元配列を作成します。

```cpp
// cwr_array.cpp
// compile with: /ZW
using namespace Platform;
ref class MyClass {};
int main() {
   // one-dimensional array
   Array<MyClass^>^ My1DArray = ref new Array<MyClass^>(100);
   My1DArray[99] = ref new MyClass();
}
```

## <a name="common-language-runtime"></a>共通言語ランタイム

### <a name="syntax"></a>構文

構文の最初の例では、**gcnew** キーワードを使用して配列を割り当てます。 2 番目の例では、ローカル配列を宣言します。

```cpp
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier =
    gcnew [cli::]array<initialization-type[,rank]>(rank-size-list[,...]) [{initialization-list [,...]}]

[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier =
    {initialization-list [,...]}
```

*qualifiers*<br/>
(省略可能) 次のストレージ クラス指定子 (1 つ以上): [mutable](../cpp/mutable-data-members-cpp.md)、[volatile](../cpp/volatile-cpp.md)、[const](../cpp/const-cpp.md)、[extern](../cpp/using-extern-to-specify-linkage.md)、[static](../cpp/static-members-cpp.md)。

*array-type*<br/>
配列変数の型。 有効な型は、Windows ランタイム クラスと基本型、ref クラスと構造体、値クラスと構造体、ネイティブ ポインター (`type*`)、およびネイティブ POD (Plain Old Data) 型です。

*rank*<br/>
(省略可能) 配列の次元の数。 既定値は 1 です。最大値は 32 です。 配列の各次元そのものが配列です。

*identifier*<br/>
配列変数の名前。

*initialization-type*<br/>
配列を初期化する値の型。 通常、*array-type* と *initialization-type* には同じ型を指定します。 ただし、*initialization-type* から *array-type* への変換がある場合は、異なる型を指定できます (たとえば *initialization-type* が *array-type* から派生する場合)。

*rank-size-list*<br/>
配列の各次元のサイズのコンマ区切りの一覧。 または、*initialization-list* パラメーターが指定された場合は、コンパイラが各次元のサイズを推測できるため、*rank-size-list* は省略できます。

*initialization-list*<br/>
(省略可能) 配列の要素を初期化する、中かっこ内のコンマ区切りの値の一覧。 または、多次元配列の要素を初期化する、入れ子になった *initialization-list* 項目のコンマ区切りの一覧。

たとえば、*rank-size-list* が `(3)` の場合 (3 つの要素の 1 次元配列を宣言しています)、*initialization-list* には `{1,2,3}` を指定できます。 *rank-size-list* が `(3,2,4)` の場合 (最初の次元に 3 つの要素、2 番目の次元に 2 つの要素、3 番目の要素に 4 つの要素を宣言しています)、*initialization-list* には `{{1,2,3},{0,0},{-5,10,-21,99}}`. を指定できます。

### <a name="remarks"></a>解説

**配列**は、[プラットフォーム、既定、および cli 名前空間](platform-default-and-cli-namespaces-cpp-component-extensions.md) にあります。

標準 C++ 同様、配列のインデックスはゼロから始まり、配列には角かっこ ([]) を使用して添え字を指定します。 標準 C++ とは異なり、多次元配列のインデックスは、各次元に対する一連の角括弧 ([]) ではなく、各次元に対するインデックスの一覧で指定されます。 たとえば、*identifier*[*index1*][*index2*] ではなく、*identifier*[*index1*, *index2*] になります。

すべてのマネージ配列は `System::Array` から継承します。 配列変数に `System::Array` の任意のメソッドまたはプロパティを直接適用できます。

要素の型がポインターである配列をマネージ クラスに割り当てると、要素が 0 に初期化されます。

要素の型が `V`, 型の値である配列を割り当てると、配列の各要素に `V` 用の既定のコンストラクタが適用されます。 詳細については、「[C++ ネイティブ型と等価な .NET Framework ネイティブ型 (C++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)」を参照してください。

コンパイル時に、型が `__is_ref_array(type)` の共通言語ランタイム (CLR) 配列かどうかを検出できます。 詳細については、「[型の特徴のコンパイラ サポート](compiler-support-for-type-traits-cpp-component-extensions.md)」を参照してください。

### <a name="requirements"></a>要件

コンパイラ オプション: `/clr`

### <a name="examples"></a>使用例

次の例では、100 個の要素を持つ 1 次元配列と、最初の次元に 3 つの要素、2 番目の次元に 5 つの要素、および 3 番目の次元に 6 つの要素を持つ 3 次元配列を作成します。

```cpp
// clr_array.cpp
// compile with: /clr
ref class MyClass {};
int main() {
   // one-dimensional array
   array<MyClass ^> ^ My1DArray = gcnew array<MyClass ^>(100);
   My1DArray[99] = gcnew MyClass();

   // three-dimensional array
   array<MyClass ^, 3> ^ My3DArray = gcnew array<MyClass ^, 3>(3, 5, 6);
   My3DArray[0,0,0] = gcnew MyClass();
}
```

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)