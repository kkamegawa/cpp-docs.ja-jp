---
title: money_get クラス
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_get
- xlocmon/std::money_get::char_type
- xlocmon/std::money_get::iter_type
- xlocmon/std::money_get::string_type
- xlocmon/std::money_get::do_get
- xlocmon/std::money_get::get
helpviewer_keywords:
- std::money_get [C++]
- std::money_get [C++], char_type
- std::money_get [C++], iter_type
- std::money_get [C++], string_type
- std::money_get [C++], do_get
- std::money_get [C++], get
ms.assetid: 692d3374-3fe7-4b46-8aeb-f8d91ed66b2e
ms.openlocfilehash: d882edd5ce55b15d03512ca9a55a49bc3424ee7a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687668"
---
# <a name="money_get-class"></a>money_get クラス

クラステンプレートは、`CharType` 型のシーケンスから通貨値への変換を制御するためにロケールファセットとして使用できるオブジェクトを表します。

## <a name="syntax"></a>構文

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class money_get : public locale::facet;
```

### <a name="parameters"></a>パラメーター

*Chartype* \
ロケールの文字をエンコードするためにプログラム内で使用される型。

*InputIterator* \
get 関数が入力を読み取る反復子の型。

## <a name="remarks"></a>Remarks

すべてのロケールのファセットと同様、静的オブジェクト ID に最初に格納されている値は 0 です。 格納されている値に初めてアクセスしようとすると、**id** に一意の正の値が格納されます。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[money_get](#money_get)|通貨値を表すシーケンスから数値を抽出するために使用される `money_get` 型のオブジェクトのコンストラクター。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[char_type](#char_type)|ロケールによって使用される文字を表すために使用される型。|
|[iter_type](#iter_type)|入力反復子を表す型。|
|[string_type](#string_type)|`CharType` 型の文字を格納する文字列を表す型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[do_get](#do_get)|通貨値を表す文字シーケンスから数値を抽出するために呼び出される仮想関数。|
|[get](#get)|通貨値を表す文字シーケンスから数値を抽出します。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<locale>

**名前空間:** std

## <a name="char_type"></a>  money_get::char_type

ロケールによって使用される文字を表すために使用される型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター *CharType* のシノニムです。

## <a name="do_get"></a>  money_get::do_get

通貨値を表す文字シーケンスから数値を抽出するために呼び出される仮想関数。

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    long double& val) const virtual iter_type do_get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    string_type& val) const
```

### <a name="parameters"></a>パラメーター

*最初*の \
変換されるシーケンスの開始位置を示す入力反復子。

*最後*の \
変換されるシーケンスの終了位置を示す入力反復子。

*国際*\
シーケンスで期待される通貨記号の種類を示すブール値。国際通貨の場合は **true**、国内通貨の場合は **false**。

*Iosbase* \
書式設定フラグ。これが設定されている場合、通貨記号は省略可能です。それ以外の場合は必須です。

*状態*\
操作が成功したか失敗したかに基づいて、ストリームの状態に適したビットマスク要素を設定します。

*val* \
変換後のシーケンスを格納する文字列。

### <a name="return-value"></a>戻り値

通貨入力フィールドを超える先頭の要素を示す入力反復子。

### <a name="remarks"></a>Remarks

1 番目のプロテクト仮想メンバー関数は、シーケンス [ `first`, `last`) の先頭から始め、空でない完全な通貨入力フィールドを認識するまで、連続した要素との一致を試みます。 成功した場合は、このフィールドを1つ以上の10進数のシーケンスに変換します。また、必要に応じてマイナス記号 (`-`) を付けて、その結果を[string_type](#string_type)オブジェクト*val*に格納します。 そして、通貨入力フィールドを超える先頭の要素を指す反復子を返します。 それ以外の場合、関数は空のシーケンスを*val*に格納し、*状態*の `ios_base::failbit` を設定します。 そして、有効な通貨入力フィールドのプレフィックスを超える先頭の要素を指す反復子を返します。 いずれの場合も、戻り値が `last` と等しい場合、関数は `State` に `ios_base::eofbit` を設定します。

2番目のプロテクト仮想メンバー関数は、最初と同じように動作します。ただし、成功した場合は、必要に応じて符号付き数字シーケンスを**long double**型の値に変換し、その値を*val*に格納します。

通貨入力フィールドの形式は、有効な呼び出し[use_facet](../standard-library/locale-functions.md#use_facet)  < [Moneypunct](../standard-library/moneypunct-class.md) \< **chartype**、**国際**> > ( **iosbase. flags**) によって返される[ロケールファセット](../standard-library/locale-class.md#facet_class)**fac.** によって決定されます。 [getloc](../standard-library/ios-base-class.md#getloc))。

具体的には、次のように使用します。

- **fac.** 。 [neg_format](../standard-library/moneypunct-class.md#neg_format)は、フィールドのコンポーネントの出現順序を決定します。

- **fac.** 。 [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol)は、通貨記号を構成する要素のシーケンスを決定します。

- **fac.** 。 [positive_sign](../standard-library/moneypunct-class.md#positive_sign)は、正の記号を構成する要素のシーケンスを決定します。

- **fac.** 。 [negative_sign](../standard-library/moneypunct-class.md#negative_sign)は、負の符号を構成する要素のシーケンスを決定します。

- **fac.** 。 [グループ化](../standard-library/moneypunct-class.md#grouping)は、小数点の左側に桁をグループ化する方法を決定します。

- **fac.** 。 [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep)は、小数点の左側にある数字のグループを区切る要素を決定します。

- **fac.** 。 [decimal_point](../standard-library/moneypunct-class.md#decimal_point)は、小数点以下の桁数と整数の桁を区切る要素を決定します。

- **fac.** 。 [frac_digits](../standard-library/moneypunct-class.md#frac_digits)は、小数点の右側にある有効な小数部の桁数を決定します。 `frac_digits` によって要求される小数桁数を上回る桁数の値を解析する場合、`do_get` は最大で `frac_digits` 文字を処理した後、解析を停止します。

符号文字列 ( **fac.** の場合は。 `negative_sign` または**fac.** 。 `positive_sign`) に複数の要素があり、最初の要素のみが一致します。これは、 **money_base:: sign**と等しい要素が、形式パターン ( **fac.** ) に表示されます。 `neg_format`) 残りの要素は、通貨入力フィールドの末尾で一致します。 いずれの文字列も通貨入力フィールド内の先頭の要素が次の要素と一致していない場合、符号文字列は空と見なされ、符号は正になります。

**Iosbase. flags**の場合。 [showbase](../standard-library/ios-functions.md#showbase)  &  の[フラグ](../standard-library/ios-base-class.md#flags)は0以外で、文字列は**fac.** です。 **money_base:: symbol**と等しい要素が書式パターンに含まれる場合は、`curr_symbol` が一致する必要があります。 このようにしないと、書式パターンの末尾に **money_base::symbol** が出現する場合、および一致せずに残っている符号文字列の要素がない場合に、通貨記号は一致しません。 それ以外の場合は、必要に応じて通貨記号が一致します。

**Fac.** のインスタンスが存在しない場合。 `thousands_sep` は、通貨入力フィールドの値の部分 ( **money_base:: value**と等しい要素が書式パターンで表示されます) で発生します。グループ化の制約は適用されません。 それ以外の場合は、 **fac.** によって課せられるグループ化の制約です。 **グループ化**が適用されます。 結果の数字のシーケンスは、下位**fac.** を持つ整数を表すことに注意してください。 `frac_digits` 10 進数は小数点の右側と見なされます。

任意の余白は、書式パターンの末尾以外に出現する場合、**money_base::space** と等しい要素が書式パターンに出現しているときに一致します。 それ以外の場合、内部の余白は一致しません。 [Use_facet](../standard-library/locale-functions.md#use_facet)  < [Ctype](../standard-library/ctype-class.md) \< **chartype**> > ( **iosbase. flags**の場合、要素*ch*は空白と見なされます。 [getloc](../standard-library/ios-base-class.md#getloc))。 [is](../standard-library/ctype-class.md#is)( **ctype_base:: space**, *ch*) が**true**である。

### <a name="example"></a>例

[get](#get) の例 (`do_get` を呼び出す) を参照してください。

## <a name="get"></a>  money_get::get

通貨値を表す文字シーケンスから数値を抽出します。

```cpp
iter_type get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    long double& val) const;

iter_type get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    string_type& val) const;
```

### <a name="parameters"></a>パラメーター

*最初*の \
変換されるシーケンスの開始位置を示す入力反復子。

*最後*の \
変換されるシーケンスの終了位置を示す入力反復子。

*国際*\
シーケンスで期待される通貨記号の種類を示すブール値。国際通貨の場合は **true**、国内通貨の場合は **false**。

*Iosbase* \
書式設定フラグ。これが設定されている場合、通貨記号は省略可能です。それ以外の場合は必須です

*状態*\
操作が成功したかどうかに基づき、ストリームの状態に適したビットマスク要素を設定します。

*val* \
変換後のシーケンスを格納する文字列。

### <a name="return-value"></a>戻り値

通貨入力フィールドを超える先頭の要素を示す入力反復子。

### <a name="remarks"></a>Remarks

両方のメンバー関数は、 [do_get](#do_get) `(first, last, Intl, Iosbase, State, val)` を返します。

### <a name="example"></a>例

```cpp
// money_get_get.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;

int main( )
{
   locale loc( "german_germany" );

   basic_stringstream< char > psz;
   psz << use_facet<moneypunct<char, 1> >(loc).curr_symbol() << "-1.000,56";
   basic_stringstream< char > psz2;
   psz2 << "-100056" << use_facet<moneypunct<char, 1> >(loc).curr_symbol();

   ios_base::iostate st = 0;
   long double fVal;

   psz.flags( psz.flags( )|ios_base::showbase );
   // Which forced the READING the currency symbol
   psz.imbue(loc);
   use_facet < money_get < char > >( loc ).
      get( basic_istream<char>::_Iter( psz.rdbuf( ) ),
           basic_istream<char>::_Iter( 0 ), true, psz, st, fVal );

   if ( st & ios_base::failbit )
      cout << "money_get(" << psz.str( ) << ", intl = 1) FAILED"
           << endl;
   else
      cout << "money_get(" << psz.str( ) << ", intl = 1) = "
           << fVal/100.0 << endl;

   use_facet < money_get < char > >( loc ).
      get(basic_istream<char>::_Iter(psz2.rdbuf( )),
          basic_istream<char>::_Iter(0), false, psz2, st, fVal);

   if ( st & ios_base::failbit )
      cout << "money_get(" << psz2.str( ) << ", intl = 0) FAILED"
           << endl;
   else
      cout << "money_get(" << psz2.str( ) << ", intl = 0) = "
           << fVal/100.0 << endl;
};
```

## <a name="iter_type"></a>  money_get::iter_type

入力反復子を表す型。

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター **InputIterator** のシノニムです。

## <a name="money_get"></a>  money_get::money_get

通貨値を表すシーケンスから数値を抽出するために使用される `money_get` 型のオブジェクトのコンストラクター。

```cpp
explicit money_get(size_t _Refs = 0);
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

コンストラクターは、 **locale::** [facet](../standard-library/locale-class.md#facet_class)( *(Refs*) を使用して、その基本オブジェクトを初期化します。

## <a name="string_type"></a>  money_get::string_type

**CharType** 型の文字を格納する文字列を表す型。

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Remarks

この型は、クラステンプレート[basic_string](../standard-library/basic-string-class.md)の特殊化を表します。

## <a name="see-also"></a>関連項目

[\<locale>](../standard-library/locale.md)\
[facet クラス](../standard-library/locale-class.md#facet_class)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
