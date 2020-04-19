---
title: money_put クラス
ms.date: 11/01/2018
f1_keywords:
- xlocmon/std::money_put
- xlocmon/std::money_put::char_type
- xlocmon/std::money_put::iter_type
- xlocmon/std::money_put::string_type
- xlocmon/std::money_put::do_put
- xlocmon/std::money_put::put
helpviewer_keywords:
- std::money_put [C++]
- std::money_put [C++], char_type
- std::money_put [C++], iter_type
- std::money_put [C++], string_type
- std::money_put [C++], do_put
- std::money_put [C++], put
ms.assetid: f439fd56-c9b1-414c-95e1-66c918c6eee6
ms.openlocfilehash: aafa6f9498ee315c25e73833baf3c13d99d36743
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689310"
---
# <a name="money_put-class"></a>money_put クラス

クラステンプレートは、通貨値から `CharType` 型のシーケンスへの変換を制御するためにロケールファセットとして使用できるオブジェクトを表します。

## <a name="syntax"></a>構文

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class money_put : public locale::facet;
```

### <a name="parameters"></a>パラメーター

*Chartype* \
ロケールの文字をエンコードするためにプログラム内で使用される型。

*OutputIterator* \
通貨の put 関数が出力を書き込む反復子の型。

## <a name="remarks"></a>Remarks

すべてのロケールのファセットと同様、静的オブジェクト ID に最初に格納されている値は 0 です。 格納されている値に初めてアクセスしようとすると、**id** に一意の正の値が格納されます。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[money_put](#money_put)|`money_put` 型のオブジェクトのコンストラクター。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[char_type](#char_type)|ロケールによって使用される文字を表すために使用される型。|
|[iter_type](#iter_type)|出力反復子を表す型。|
|[string_type](#string_type)|`CharType` 型の文字を格納する文字列を表す型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[do_put](#do_put)|通貨値を表す文字シーケンスから数値または文字列を抽出するために呼び出される仮想関数。|
|[put](#put)|数値または文字列を通貨値を表す文字シーケンスに変換します。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<locale>

**名前空間:** std

## <a name="char_type"></a>  money_put::char_type

ロケールによって使用される文字を表すために使用される型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター **CharType** のシノニムです。

## <a name="do_put"></a>  money_put::do_put

通貨値を表す文字シーケンスから数値または文字列を抽出するために呼び出される仮想関数。

```cpp
virtual iter_type do_put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    const string_type& val) const;

virtual iter_type do_put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

### <a name="parameters"></a>パラメーター

*次*の \
挿入された文字列の先頭の要素を示す反復子。

*国際 \ (_s)*
シーケンスで期待される通貨記号の種類を示すブール値。国際通貨の場合は **true**、国内通貨の場合は **false**。

*_Iosbase* \
書式設定フラグ。これが設定されている場合、通貨記号は省略可能です。それ以外の場合は必須です

@No__t_1 の*塗りつぶし (_c)*
スペースに使用される文字。

*val* \
変換される文字列オブジェクト。

### <a name="return-value"></a>戻り値

生成される最後の要素を 1 つ超える位置を示す出力反復子。

### <a name="remarks"></a>Remarks

最初の仮想プロテクトメンバー関数は、 [string_type](#string_type)オブジェクト*val*から通貨出力フィールドを生成するために、*次*に始まる連続した要素を生成します。 *Val*によって制御されるシーケンスは、1つ以上の10進数字で始まり、必要に応じて、その金額を表すマイナス記号 (-) を付ける必要があります。 関数は、生成された通貨出力フィールドを超える先頭の要素を指す反復子を返します。

2番目のプロテクト仮想メンバー関数は、最初のオーバーロードと同じように動作しますが、最初に*val*が10進数のシーケンスに変換され、必要に応じてマイナス記号 (-) の前にあるように変換されます。

通貨出力フィールドの形式は、(有効な) call [use_facet](../standard-library/locale-functions.md#use_facet)  < [Moneypunct](../standard-library/moneypunct-class.md) \< **chartype**、**国際**> > ( **iosbase. flags**) によって返される[ロケールファセット](../standard-library/locale-class.md#facet_class)fac. によって決定されます。 [getloc](../standard-library/ios-base-class.md#getloc))。

具体的には、次のように使用します。

- **fac.** 。 [pos_format](../standard-library/moneypunct-class.md#pos_format)は、負でない値に対してフィールドのコンポーネントが生成される順序を決定します。

- **fac.** 。 [neg_format](../standard-library/moneypunct-class.md#neg_format)は、フィールドのコンポーネントが負の値に対して生成される順序を決定します。

- **fac.** 。 [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol)は、通貨記号用に生成する要素のシーケンスを決定します。

- **fac.** 。 [positive_sign](../standard-library/moneypunct-class.md#positive_sign)は、正の符号に対して生成する要素のシーケンスを決定します。

- **fac.** 。 [negative_sign](../standard-library/moneypunct-class.md#negative_sign)は、負の符号に対して生成する要素のシーケンスを決定します。

- **fac.** 。 [グループ化](../standard-library/moneypunct-class.md#grouping)は、小数点の左側に桁をグループ化する方法を決定します。

- **fac.** 。 [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep)は、小数点の左側にある数字のグループを区切る要素を決定します。

- **fac.** 。 [decimal_point](../standard-library/moneypunct-class.md#decimal_point)は、小数点以下の桁数と整数の桁を区切る要素を決定します。

- **fac.** 。 [frac_digits](../standard-library/moneypunct-class.md#frac_digits)は、小数点の右側にある有効な小数部の桁数を決定します。

符号文字列 ( **fac.** の場合は。 `negative_sign` または**fac.** 。 `positive_sign`) に複数の要素があります。最初の要素だけが生成されます。 **money_base:: sign**と等しい要素が、形式パターン ( **fac.** ) に表示されます。 `neg_format` または**fac.** 。 `pos_format`) 残りの要素は、通貨出力フィールドの末尾に生成されます。

**Iosbase. flags**の場合。 [showbase](../standard-library/ios-functions.md#showbase)  &  の[フラグ](../standard-library/ios-base-class.md#flags)は0以外で、文字列は**fac.** です。 `curr_symbol` が生成されます。この要素は、 **money_base:: symbol**と等しい要素が書式パターンで表示されます。 それ以外の場合、通貨記号は生成されません。

**Fac.** によって適用されるグループ化の制約がない場合。 **grouping** (最初の要素の値は CHAR_MAX)、次に**fac.** のインスタンスはありません。 `thousands_sep` は、通貨出力フィールドの値の部分 ( **money_base:: value**と等しい要素が書式パターンで表示されます) に生成されます。 **Fac.** の場合。 `frac_digits` が0の場合、 **fac.** のインスタンスはありません。 10進数の後に `decimal_point` が生成されます。 それ以外の場合、結果として得られる通貨の出力フィールドには、下位の**fac.** が配置されます。 小数点以下の桁数を `frac_digits` します。

埋め込みは、 **iosbase. flags**の場合を除き、任意の数値出力フィールドに対して行われます。 **iosbase. flags** & **フラグ**。 [internal](../standard-library/ios-functions.md#internal)が0以外の場合、内部の埋め込みが生成されます。ここでは、 **money_base:: space**と等しい要素が、表示されている場合は、書式パターンで表示されます。 それ以外の場合、内部の埋め込みは生成されたシーケンスの前に発生します。 埋め込み文字は **fill** です。

関数は**iosbase. flags**を呼び出します。 **width**(0) フィールドの幅を0にリセットします。

### <a name="example"></a>例

[put](#put) の例 (仮想メンバー関数が **put** で呼び出される) を参照してください。

## <a name="iter_type"></a>  money_put::iter_type

出力反復子を表す型。

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター **OutputIterator** のシノニムです。

## <a name="money_put"></a>  money_put::money_put

`money_put` 型のオブジェクトのコンストラクター。

```cpp
explicit money_put(size_t _Refs = 0);
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

コンストラクターは、**locale::** [facet](../standard-library/locale-class.md#facet_class)( `_Refs`) を使用して、その基本オブジェクトを初期化します。

## <a name="put"></a>  money_put::put

数値または文字列を通貨値を表す文字シーケンスに変換します。

```cpp
iter_type put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    const string_type& val) const;

iter_type put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

### <a name="parameters"></a>パラメーター

*次*の \
挿入された文字列の先頭の要素を示す反復子。

*国際 \ (_s)*
シーケンスで期待される通貨記号の種類を示すブール値。国際通貨の場合は **true**、国内通貨の場合は **false**。

*_Iosbase* \
書式設定フラグ。これが設定されている場合、通貨記号は省略可能です。それ以外の場合は必須です

@No__t_1 の*塗りつぶし (_c)*
スペースに使用される文字。

*val* \
変換される文字列オブジェクト。

### <a name="return-value"></a>戻り値

生成される最後の要素を 1 つ超える位置を示す出力反復子。

### <a name="remarks"></a>Remarks

どちらのメンバー関数も [do_put](#do_put)( `next`, `_Intl`, `_Iosbase`, `_Fill`, `val`) を返します。

### <a name="example"></a>例

```cpp
// money_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

int main()
{
    std::locale loc( "german_germany" );
    std::basic_stringstream<char> psz;

    psz.imbue(loc);
    psz.flags(psz.flags() | std::ios_base::showbase); // force the printing of the currency symbol
    std::use_facet<std::money_put<char> >(loc).put(std::basic_ostream<char>::_Iter(psz.rdbuf()), true, psz, ' ', 100012);
    if (psz.fail())
        std::cout << "money_put() FAILED" << std::endl;
    else
        std::cout << "money_put() = \"" << psz.rdbuf()->str() << "\"" << std::endl;
}
```

```Output
money_put() = "EUR1.000,12"
```

## <a name="string_type"></a>  money_put::string_type

`CharType` 型の文字を格納する文字列を表す型。

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Remarks

この型は、ソースシーケンスから要素のシーケンスを格納できるオブジェクトを持つクラステンプレート[basic_string](../standard-library/basic-string-class.md)の特殊化を表します。

## <a name="see-also"></a>関連項目

[\<locale>](../standard-library/locale.md)\
[facet クラス](../standard-library/locale-class.md#facet_class)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
