---
title: num_put クラス
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::num_put
- locale/std::num_put::char_type
- locale/std::num_put::iter_type
- locale/std::num_put::do_put
- locale/std::num_put::put
helpviewer_keywords:
- std::num_put [C++]
- std::num_put [C++], char_type
- std::num_put [C++], iter_type
- std::num_put [C++], do_put
- std::num_put [C++], put
ms.assetid: 36c5bffc-8283-4201-8ed4-78c4d81f8a17
ms.openlocfilehash: 49d76c5d553054934907cd2ddc0b7fd1f8b1e998
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687638"
---
# <a name="num_put-class"></a>num_put クラス

数値から `CharType` 型のシーケンスへの変換を制御するためにロケールファセットとして使用できるオブジェクトを表すクラステンプレート。

## <a name="syntax"></a>構文

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class num_put : public locale::facet;
```

### <a name="parameters"></a>パラメーター

*Chartype* \
ロケールの文字をエンコードするためにプログラム内で使用される型。

*OutputIterator* \
数値 put 関数が出力を書き込む反復子の型。

## <a name="remarks"></a>Remarks

すべてのロケールのファセットと同様、静的オブジェクト ID に最初に格納されている値は 0 です。 格納されている値に初めてアクセスしようとすると、**id** に一意の正の値が格納されます。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[num_put](#num_put)|`num_put` 型のオブジェクトのコンストラクター。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[char_type](#char_type)|ロケールによって使用される文字を表すために使用される型。|
|[iter_type](#iter_type)|出力反復子を表す型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[do_put](#do_put)|数値を、特定のロケールで書式設定された数値を表す `CharType` のシーケンスに変換するために呼び出される仮想関数。|
|[put](#put)|数値を、特定のロケールで書式設定された数値を表す `CharType` のシーケンスに変換します。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<locale>

**名前空間:** std

## <a name="char_type"></a>  num_put::char_type

ロケールによって使用される文字を表すために使用される型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター `CharType` のシノニムです。

## <a name="do_put"></a>  num_put::do_put

数値を、特定のロケールで書式設定された数値を表す `CharType` のシーケンスに変換するために呼び出される仮想関数。

```cpp
virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    bool val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    unsigned long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    double val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long double val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const void* val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const long long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const unsigned long long val) const;
```

### <a name="parameters"></a>パラメーター

*次*の \
挿入された文字列の先頭の要素を示す反復子。

*_Iosbase* \
出力に句読点を付けるために使用される numpunct ファセットを持つロケールおよび出力を書式設定するためのフラグを含むストリームを指定します。

@No__t_1 の*塗りつぶし (_c)*
スペースに使用される文字。

*val* \
出力する数値またはブール型。

### <a name="return-value"></a>戻り値

生成される最後の要素を 1 つ超える位置を示す出力反復子。

### <a name="remarks"></a>Remarks

最初の仮想プロテクトメンバー関数は、 *val*の値から整数の出力フィールドを生成するために、*次*に始まる連続した要素を生成します。 関数は、生成された出力フィールドを超える、次に要素を挿入する場所を指定する反復子を返します。

整数の出力フィールドは、ファイルに一連の**char**要素を生成するために、印刷関数によって使用されるのと同じ規則によって生成されます。 このような char 要素は、単純な一対一のマッピングによって `CharType` 型の同等の要素にマップされると想定されます。 ただし、print 関数はフィールドにスペースまたは数字0を埋め込みますが、代わりに `fill` を使用 `do_put` ます。 同等の出力変換仕様は次のように決定されます。

- **Iosbase. flags**の場合。 [フラグ](../standard-library/ios-base-class.md#flags) &  `ios_base::basefield`  ==  `ios_base::`[10 月](../standard-library/ios-functions.md#oct)の場合、変換仕様は `lo` です。

- **Iosbase. flags**  & **ios_base:: basefield**  ==  `ios_base::`[hex](../standard-library/ios-functions.md#hex)の場合、変換仕様は `lx` です。

- それ以外の場合、変換仕様は `ld` です。

**Iosbase. flags**の場合。 [width](../standard-library/ios-base-class.md#width)が0以外の場合、この値のフィールド幅が前に付加されます。 次に、関数は**iosbase. flags**を呼び出します。 **width**(0) フィールドの幅を0にリセットします。

埋め込みは、出力フィールドを指定するために必要な要素*N*の最小数が**iosbase. flags**より小さい場合にのみ発生します。 [幅](../standard-library/ios-base-class.md#width)。 このような埋め込みは、**塗りつぶし**の*N*  - **幅**のコピーのシーケンスで構成されます。 この場合、埋め込みは次のように発生します。

- **Iosbase. flags**の場合。 **フラグ** &  `ios_base::adjustfield`  == [左](../standard-library/ios-functions.md#left)`ios_base::`、フラグ **-** が前に付加されます。 (埋め込みは、生成されたテキストの後に発生します。)

- **iosbase.flags** & **ios_base::adjustfield** == `ios_base::`[internal](../standard-library/ios-functions.md#internal) の場合、**0** フラグが先頭に付加されます。 (数値出力フィールド場合、埋め込みは、出力関数が 0 で埋め込む状況でのみ発生します。)

- それ以外の場合、追加のフラグは先頭に付加されません。 (埋め込みは、生成されたシーケンスの前に発生します。)

最後に次のようになります。

- **Iosbase. flags**の場合。 `ios_base::`[showpos](../standard-library/ios-functions.md#showpos)  & **フラグ**が0以外の場合、変換指定の前にフラグ **+** が付加されます。

- **Iosbase. flags**の場合。 **ios_base::** [showbase](../standard-library/ios-functions.md#showbase)  & **フラグ**が0以外の場合、変換指定の前にフラグ **#** が付加されます。

整数の出力フィールドの形式は、 [use_facet](../standard-library/locale-functions.md#use_facet)  < [numpunct](../standard-library/numpunct-class.md) \< **Elem**> ( **iosbase. flags**) の呼び出しによって返される[ロケールファセット](../standard-library/locale-class.md#facet_class)によってさらに決定**されます**。 [getloc](../standard-library/ios-base-class.md#getloc))。 具体的には、次のように使用します。

- **fac.** 。 [グループ化](../standard-library/numpunct-class.md#grouping)によって、小数点の左側に桁をグループ化する方法が決まります。

- **fac.** 。 [thousands_sep](../standard-library/numpunct-class.md#thousands_sep)は、小数点の左側にある数字のグループを区切るシーケンスを決定します。

**Fac.** によって適用されるグループ化の制約がない場合。 **grouping** (最初の要素の値は CHAR_MAX)、次に**fac.** のインスタンスはありません。 `thousands_sep` は、出力フィールドに生成されます。 それ以外の場合、出力変換が発生した後に区切り記号が挿入されます。

2 番目のプロテクト仮想メンバー関数:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    unsigned long val) const;
```

この関数の動作は 1 番目と同じですが、`ld` の変換仕様を `lu` に置き換えている点が異なります。

3 番目のプロテクト仮想メンバー関数：

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    double val) const;
```

この関数の動作は 1 番目と同じですが、**val** の値から浮動小数点出力フィールドを生成している点が異なります。 **fac.** 。 [decimal_point](../standard-library/numpunct-class.md#decimal_point)は、小数部の桁を区切るシーケンスを決定します。 同等の出力変換仕様は次のように決定されます。

- **Iosbase. flags**の場合。 **フラグ** &  `ios_base::floatfield`  ==  `ios_base::`[修正](../standard-library/ios-functions.md#fixed)されています。変換仕様は `lf` です。

- **Iosbase. flags**の場合。 **フラグ** & **ios_base:: floatfield**  ==  `ios_base::`[科学的](../standard-library/ios-functions.md#scientific)な場合、変換仕様は `le`。 **Iosbase. flags**の場合。 [大文字](../standard-library/ios-functions.md#uppercase)`ios_base::`  & **フラグ**は0以外の `e` `E` に置き換えられます。

- それ以外の場合、変換仕様は **lg** です。 **Iosbase. flags**の場合。 **ios_base::**  &  の**フラグ**が0以外の場合、`g` は `G` に置き換えられます。

**Iosbase. flags**の場合。 **フラグ** & **ios_base:: fixed**が0以外であるか、 **iosbase. flags**である場合。 [有効](../standard-library/ios-base-class.md#precision)桁数が0を超えています。値は**iosbase. flags**です。 変換指定の前に、**有効桁数**が付加されます。 埋め込みの動作は整数出力フィールドの場合と同様です。 埋め込み文字は **fill** です。 最後に次のようになります。

- **Iosbase. flags**の場合。 `ios_base::`[showpos](../standard-library/ios-functions.md#showpos)  & **フラグ**が0以外の場合、変換指定の前にフラグ **+** が付加されます。

- **Iosbase. flags**の場合。 `ios_base::`[showpoint](../standard-library/ios-functions.md#showpoint)  & **フラグ**が0以外の場合は、変換指定の前にフラグ **#** が付加されます。

4 番目のプロテクト仮想メンバー関数:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

は3番目と同じように動作しますが、変換指定の修飾子 `l` が `L` に置き換えられる点が異なります。

5 番目のプロテクト仮想メンバー関数:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    const void* val) const;
```

この関数の動作は 1 番目と同じですが、変換仕様が `p` と **、** 埋め込みを指定するために必要なすべての修飾子である点が異なります。

6 番目のプロテクト仮想メンバー関数:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    bool val) const;
```

は、最初と同じように動作しますが、 *val*からブール型の出力フィールドを生成する点が異なります。

ブール値出力フィールドは、次の 2 つの形式のいずれかになります。 [ブール](../standard-library/ios-functions.md#boolalpha)型 `iosbase.flags & ios_base::` が**false**の場合、メンバー関数は `do_put(_Next, _Iosbase, _Fill, (long)val)` を返します。通常は、0 ( **false**の場合) または 1 ( **true**の場合) のいずれかの生成されたシーケンスが生成されます。 それ以外の場合、生成されたシーケンスは*fac.* です。[falsename](../standard-library/numpunct-class.md#falsename) ( **false**の場合) または*fac.* 。[(](../standard-library/numpunct-class.md#truename) **true**の場合)。

7 番目のプロテクト仮想メンバー関数:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    long long val) const;
```

この関数の動作は 1 番目と同じですが、`ld` の変換仕様を `lld` に置き換えている点が異なります。

8 番目のプロテクト仮想メンバー関数:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    unsigned long long val) const;
```

この関数の動作は 1 番目と同じですが、`ld` の変換仕様を `llu` に置き換えている点が異なります。

### <a name="example"></a>例

[put](#put) の例 (`do_put` を呼び出す) を参照してください。

## <a name="iter_type"></a>  num_put::iter_type

出力反復子を表す型。

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター **OutputIterator** のシノニムです。

## <a name="num_put"></a>  num_put::num_put

`num_put` 型のオブジェクトのコンストラクター。

```cpp
explicit num_put(size_t _Refs = 0);
```

### <a name="parameters"></a>パラメーター

*Refs \ (_c)*
オブジェクトのメモリ管理のタイプを指定するために使用する整数値。

### <a name="remarks"></a>Remarks

*Refs*パラメーターに指定できる値とその意味は、次のとおりです。

- 0: オブジェクトの有効期間はそれが含まれるロケールによって管理されます。

- 1: オブジェクトの有効期間を手動で管理する必要があります。

- \> 1: これらの値は定義されていません。

デストラクターが保護されているため、利用できる直接的な例はありません。

コンストラクターは、**locale::** [facet](../standard-library/locale-class.md#facet_class)(_ *Refs*) を使用して、その基本オブジェクトを初期化します。

## <a name="put"></a>  num_put::put

数値を、特定のロケールで書式設定された数値を表す `CharType`s のシーケンスに変換します。

```cpp
iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    bool val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    unsigned long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    Long long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    Unsigned long long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    double val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long double val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const void* val) const;
```

### <a name="parameters"></a>パラメーター

*dest* \
挿入された文字列の先頭の要素を示す反復子。

*_Iosbase* \
出力に句読点を付けるために使用される numpunct ファセットを持つロケールおよび出力を書式設定するためのフラグを含むストリームを指定します。

@No__t_1 の*塗りつぶし (_c)*
スペースに使用される文字。

*val* \
出力する数値またはブール型。

### <a name="return-value"></a>戻り値

生成される最後の要素を 1 つ超える位置を示す出力反復子。

### <a name="remarks"></a>Remarks

すべてのメンバー関数が [do_put](#do_put)( `next`, `_Iosbase`, `_Fill`, `val`) を返します。

### <a name="example"></a>例

```cpp
// num_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );
   basic_stringstream<char> psz2;
   ios_base::iostate st = 0;
   long double fVal;
   cout << "The thousands separator is: "
        << use_facet < numpunct <char> >(loc).thousands_sep( )
        << endl;

   psz2.imbue( loc );
   use_facet < num_put < char > >
      ( loc ).put(basic_ostream<char>::_Iter(psz2.rdbuf( ) ),
                    psz2, ' ', fVal=1000.67);

   if ( st & ios_base::failbit )
      cout << "num_put( ) FAILED" << endl;
   else
      cout << "num_put( ) = " << psz2.rdbuf( )->str( ) << endl;
}
```

```Output
The thousands separator is: .
num_put( ) = 1.000,67
```

## <a name="see-also"></a>関連項目

[\<locale>](../standard-library/locale.md)\
[facet クラス](../standard-library/locale-class.md#facet_class)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
