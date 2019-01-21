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
ms.openlocfilehash: 2ede0ccd85f116f300939c819ae8209435da72b7
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327331"
---
# <a name="numput-class"></a>num_put クラス

数値から `CharType` 型のシーケンスへの変換を制御するためにロケール ファセットとして使用できるオブジェクトを表すテンプレート クラス。

## <a name="syntax"></a>構文

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class num_put : public locale::facet;
```

### <a name="parameters"></a>パラメーター

*CharType*<br/>
ロケールの文字をエンコードするためにプログラム内で使用される型。

*OutputIterator*<br/>
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

## <a name="requirements"></a>必要条件

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

*next*<br/>
挿入された文字列の先頭の要素を示す反復子。

*されている _Iosbase*<br/>
出力に句読点を付けるために使用される numpunct ファセットを持つロケールおよび出力を書式設定するためのフラグを含むストリームを指定します。

*_Fill*<br/>
スペースに使用される文字。

*val*<br/>
出力する数値またはブール型。

### <a name="return-value"></a>戻り値

生成される最後の要素を 1 つ超える位置を示す出力反復子。

### <a name="remarks"></a>Remarks

最初のプロテクト仮想メンバー関数から始まる連続した要素を生成する*次*の値から整数出力フィールドを生成するために*val*します。 関数は、生成された出力フィールドを超える、次に要素を挿入する場所を指定する反復子を返します。

整数出力フィールドは、一連を生成するため、印刷の関数によって使用される同じ規則によって生成される**char**要素をファイル。 このような各 char 要素は型の同等の要素にマップすると見なされます`CharType`単純な一対一のマッピングでします。 印刷機能はフィールドを埋めるスペースや数字の 0 のいずれか、場所`do_put`代わりに使用`fill`します。 同等の出力変換仕様は次のように決定されます。

- 場合**iosbase**します。 [フラグ](../standard-library/ios-base-class.md#flags) & `ios_base::basefield` == `ios_base::`[oct](../standard-library/ios-functions.md#oct)、変換仕様は`lo`します。

- 場合**iosbase.flags** & **ios_base::basefield** == `ios_base::`[16 進](../standard-library/ios-functions.md#hex)、変換仕様は`lx`します。

- それ以外の場合、変換仕様は `ld` です。

場合**iosbase**します。 [幅](../standard-library/ios-base-class.md#width)が 0 以外の場合、この値のフィールドの幅が付きます。 関数を呼び出して**iosbase**します。 **幅**フィールドの幅をゼロにリセットするには、(0)。

埋め込みは、場合にのみが発生します。 要素の最小数*N*出力フィールドを指定するために必要な未満**iosbase**します。 [幅](../standard-library/ios-base-class.md#width)します。 このような埋め込みのシーケンスから成る*N* - **幅**のコピー**塗りつぶし**します。 この場合、埋め込みは次のように発生します。

- 場合**iosbase**します。 **フラグ** & `ios_base::adjustfield` == `ios_base::`[左](../standard-library/ios-functions.md#left)、フラグ**-** が付加されます。 (埋め込みは、生成されたテキストの後に発生します。)

- **iosbase.flags** & **ios_base::adjustfield** == `ios_base::`[internal](../standard-library/ios-functions.md#internal) の場合、**0** フラグが先頭に付加されます。 (数値出力フィールド場合、埋め込みは、出力関数が 0 で埋め込む状況でのみ発生します。)

- それ以外の場合、追加のフラグは先頭に付加されません。 (埋め込みは、生成されたシーケンスの前に発生します。)

最後に次のようになります。

- 場合**iosbase**します。 **フラグ** & `ios_base::`[showpos](../standard-library/ios-functions.md#showpos) 0 以外の場合、フラグ **+** 前は、変換仕様に追加されます。

- 場合**iosbase**します。 **フラグ** & **ios_base::**[showbase](../standard-library/ios-functions.md#showbase) 0 以外の場合、フラグ **#** 前は、変換仕様に追加されます。

整数の形式の出力フィールドがさらに続く、[ロケール ファセット](../standard-library/locale-class.md#facet_class)**fac**呼び出しによって返される[use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md) \< **Elem**> ( **iosbase**します。 [getloc](../standard-library/ios-base-class.md#getloc))。 具体的には、次のように使用します。

- **fac**します。 [グループ化](../standard-library/numpunct-class.md#grouping)小数点の左側の数字をグループ化する方法を決定します。

- **fac**します。 [thousands_sep](../standard-library/numpunct-class.md#thousands_sep)小数点の左側にある数字のグループを区切るシーケンスを決定します

場合によってはグループ化の制約は強制されません**fac**します。 **グループ化**(その最初の要素が値 CHAR_MAX) のインスタンスがし**fac**しません。 `thousands_sep` 出力フィールドで生成されます。 それ以外の場合、出力変換が発生した後に区切り記号が挿入されます。

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

この関数の動作は 1 番目と同じですが、**val** の値から浮動小数点出力フィールドを生成している点が異なります。 **fac**します。 [decimal_point](../standard-library/numpunct-class.md#decimal_point)を小数桁の整数の桁を区切るシーケンスを決定します。 同等の出力変換仕様は次のように決定されます。

- 場合**iosbase**します。 **フラグ** & `ios_base::floatfield` == `ios_base::`[固定](../standard-library/ios-functions.md#fixed)、変換仕様は`lf`します。

- 場合**iosbase**します。 **flags** & **ios_base::floatfield** == `ios_base::`[scientific](../standard-library/ios-functions.md#scientific), the conversion specification is `le`. 場合**iosbase**します。 **フラグ** & `ios_base::`[大文字](../standard-library/ios-functions.md#uppercase)0 以外の場合、`e`は置き換え`E`します。

- それ以外の場合、変換仕様は **lg** です。 場合**iosbase**します。 **フラグ** & **ios_base::uppercase** 0 以外の場合、`g`は置き換え`G`します。

場合**iosbase**します。 **フラグ** & **ios_base::fixed**が 0 でない場合、または**iosbase**します。 [有効桁数](../standard-library/ios-base-class.md#precision)が 0 の場合、値を持つ有効桁数よりも大きい**iosbase**します。 **有効桁数**前は、変換仕様に追加されます。 埋め込みの動作は整数出力フィールドの場合と同様です。 埋め込み文字は **fill** です。 最後に次のようになります。

- 場合**iosbase**します。 **フラグ** & `ios_base::`[showpos](../standard-library/ios-functions.md#showpos) 0 以外の場合、フラグ **+** 前は、変換仕様に追加されます。

- 場合**iosbase**します。 **フラグ** & `ios_base::`[showpoint](../standard-library/ios-functions.md#showpoint) 0 以外の場合、フラグ **#** 前は、変換仕様に追加されます。

4 番目のプロテクト仮想メンバー関数:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

3 番目の点を除いては、同じ動作修飾子`l`、変換仕様は置き換え`L`します。

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

ブール値出力フィールドを生成する点を除いて、1 番目と同じ動作*val*します。

ブール値出力フィールドは、次の 2 つの形式のいずれかになります。 場合`iosbase.flags & ios_base::` [boolalpha](../standard-library/ios-functions.md#boolalpha)は**false**、メンバー関数を返します`do_put(_Next, _Iosbase, _Fill, (long)val)`、通常 0 の生成されたシーケンスが作成されます (の**false**)または 1 (の**true**)。 それ以外の場合、生成されたシーケンスがいずれかが*fac*.[falsename](../standard-library/numpunct-class.md#falsename) (の**false**)、または*fac*.[truename](../standard-library/numpunct-class.md#truename) (の**true**)。

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

*_Refs*<br/>
オブジェクトのメモリ管理の種類を指定するために使用する整数値。

### <a name="remarks"></a>Remarks

使用可能な値を *_Refs*パラメーターとその重要性は。

- 0: オブジェクトの有効期間はそれが含まれるロケールによって管理されます。

- 1: オブジェクトの有効期間を手動で管理する必要があります。

- \> 1: これらの値が定義されていません。

デストラクターが保護されているため、利用できる直接的な例はありません。

コンストラクターは、**locale::**[facet](../standard-library/locale-class.md#facet_class)(_ *Refs*) を使用して、その基本オブジェクトを初期化します。

## <a name="put"></a>  num_put::put

一連の数値に変換`CharType`数を表す書式設定された、特定のロケール。

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

*dest*<br/>
挿入された文字列の先頭の要素を示す反復子。

*されている _Iosbase*<br/>
出力に句読点を付けるために使用される numpunct ファセットを持つロケールおよび出力を書式設定するためのフラグを含むストリームを指定します。

*_Fill*<br/>
スペースに使用される文字。

*val*<br/>
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

[\<locale>](../standard-library/locale.md)<br/>
[facet クラス](../standard-library/locale-class.md#facet_class)<br/>
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
