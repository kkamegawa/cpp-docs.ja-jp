---
title: "money_get クラス | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocmon/std::money_get
- money_get
- std.money_get
- std::money_get
dev_langs:
- C++
helpviewer_keywords:
- money_get class
ms.assetid: 692d3374-3fe7-4b46-8aeb-f8d91ed66b2e
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: f9e122dbeb68fb4ed33d9e652af21c1b9474e3a5
ms.lasthandoff: 02/24/2017

---
# <a name="moneyget-class"></a>money_get クラス
このテンプレート クラスは、`CharType` 型のシーケンスから通貨値への変換を制御するためにロケール ファセットとして使用できるオブジェクトを表します。  
  
## <a name="syntax"></a>構文  
  
```
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>  
class money_get : public locale::facet;
```  
  
#### <a name="parameters"></a>パラメーター  
 `CharType`  
 ロケールの文字をエンコードするためにプログラム内で使用される型。  
  
 `InputIterator`  
 get 関数が入力を読み取る反復子の型。  
  
## <a name="remarks"></a>コメント  
 すべてのロケールのファセットと同様、静的オブジェクト ID に最初に格納されている値は&0; です。 格納されている値に初めてアクセスしようとすると、**id** に一意の正の値が格納されます。  
  
### <a name="constructors"></a>コンストラクター  
  
|||  
|-|-|  
|[money_get](#money_get__money_get)|通貨値を表すシーケンスから数値を抽出するために使用される `money_get` 型のオブジェクトのコンストラクター。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#money_get__char_type)|ロケールによって使用される文字を表すために使用される型。|  
|[iter_type](#money_get__iter_type)|入力反復子を表す型。|  
|[string_type](#money_get__string_type)|`CharType` 型の文字を格納する文字列を表す型。|  
  
### <a name="member-functions"></a>メンバー関数  
  
|||  
|-|-|  
|[do_get](#money_get__do_get)|通貨値を表す文字シーケンスから数値を抽出するために呼び出される仮想関数。|  
|[get](#money_get__get)|通貨値を表す文字シーケンスから数値を抽出します。|  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** \<locale>  
  
 **名前空間:** std  
  
##  <a name="a-namemoneygetchartypea--moneygetchartype"></a><a name="money_get__char_type"></a>  money_get::char_type  
 ロケールによって使用される文字を表すために使用される型。  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>コメント  
 この型は、テンプレート パラメーター **CharType** のシノニムです。  
  
##  <a name="a-namemoneygetdogeta--moneygetdoget"></a><a name="money_get__do_get"></a>  money_get::do_get  
 通貨値を表す文字シーケンスから数値を抽出するために呼び出される仮想関数。  
  
```
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
 `first`  
 変換されるシーケンスの開始位置を示す入力反復子。  
  
 `last`  
 変換されるシーケンスの終了位置を示す入力反復子。  
  
 `Intl`  
 シーケンスで期待される通貨記号の種類を示すブール値。国際通貨の場合は **true**、国内通貨の場合は **false**。  
  
 `Iosbase`  
 書式設定フラグ。これが設定されている場合、通貨記号は省略可能です。それ以外の場合は必須です。  
  
 `State`  
 操作が成功したか失敗したかに基づいて、ストリームの状態に適したビットマスク要素を設定します。  
  
 `val`  
 変換後のシーケンスを格納する文字列。  
  
### <a name="return-value"></a>戻り値  
 通貨入力フィールドを超える先頭の要素を示す入力反復子。  
  
### <a name="remarks"></a>コメント  
 1 番目のプロテクト仮想メンバー関数は、シーケンス [ `first`, `last`) の先頭から始め、空でない完全な通貨入力フィールドを認識するまで、連続した要素との一致を試みます。 成功した場合、このフィールドを&1; 桁以上の&10; 進数字のシーケンス (必要に応じて頭にマイナス記号 ( `–`) が付く) に変換して値を表し、その結果を [string_type](#money_get__string_type) オブジェクト `val` に格納します。 そして、通貨入力フィールドを超える先頭の要素を指す反復子を返します。 それ以外の場合、この関数は `val` に空のシーケンスを格納し、`State` に `ios_base::failbit` を設定します。 そして、有効な通貨入力フィールドのプレフィックスを超える先頭の要素を指す反復子を返します。 いずれの場合も、戻り値が `last` と等しい場合、関数は `State` に `ios_base::eofbit` を設定します。  
  
 2 番目のプロテクト仮想メンバー関数は&1; 番目と同様に動作します。ただし、成功した場合は、必要に応じて符号を付けた数字シーケンスを `long double` 型の値に変換し、その値を `val` に格納します。  
  
 通貨入力フィールドの形式はによって決まります、[ロケールのファセット](../standard-library/locale-class.md#facet_class)**要素**効果的な呼び出しで返される[use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md) \< **CharType**、 **intl**>> ( **iosbase**します。 [getloc](../standard-library/ios-base-class.md#ios_base__getloc))。  
  
 具体的には、次のように使用します。  
  
- **fac**. [neg_format](../standard-library/moneypunct-class.md#moneypunct__neg_format)フィールドのコンポーネントが出現する順序を決定します。  
  
- **fac**. [curr_symbol](../standard-library/moneypunct-class.md#moneypunct__curr_symbol)通貨記号を構成する要素のシーケンスを決定します。  
  
- **fac**. [positive_sign](../standard-library/moneypunct-class.md#moneypunct__positive_sign)正の符号を構成する要素のシーケンスを決定します。  
  
- **fac**. [negative_sign](../standard-library/moneypunct-class.md#moneypunct__negative_sign)負の符号を構成する要素のシーケンスを決定します。  
  
- **fac**. [グループ化](../standard-library/moneypunct-class.md#moneypunct__grouping)数字が小数点の左側にグループ化方法を決定します。  
  
- **fac**. [thousands_sep](../standard-library/moneypunct-class.md#moneypunct__thousands_sep)小数点の左側にある数字のグループを区切る要素を調べます。  
  
- **fac**. [decimal_point](../standard-library/moneypunct-class.md#moneypunct__decimal_point)を小数点以下桁数の整数部の桁数を区切る要素を調べます。  
  
- **fac**. [frac_digits](../standard-library/moneypunct-class.md#moneypunct__frac_digits)小数点の右側にある重要な部分数字の数を決定します。 `frac_digits` によって要求される小数桁数を上回る桁数の値を解析する場合、`do_get` は最大で `frac_digits` 文字を処理した後、解析を停止します。  
  
 場合、記号の文字列 (**要素**します。 `negative_sign`or **fac**. `positive_sign`) が&1; つ以上の要素である最初の要素のみが一致すると、要素と等しい**money_base::sign**フォーマット パターンが表示されます (**要素**します。 `neg_format`) 残りの要素は、通貨入力フィールドの末尾で一致します。 いずれの文字列も通貨入力フィールド内の先頭の要素が次の要素と一致していない場合、符号文字列は空と見なされ、符号は正になります。  
  
 場合**iosbase**します。 [フラグ](../standard-library/ios-base-class.md#ios_base__flags) & [showbase](../standard-library/ios-functions.md#showbase)&0; 以外の場合、文字列**要素**します。 `curr_symbol`場所に一致する必要があります、要素と等しい**money_base::symbol**フォーマット パターンが表示されます。 このようにしないと、書式パターンの末尾に **money_base::symbol** が出現する場合、および一致せずに残っている符号文字列の要素がない場合に、通貨記号は一致しません。 それ以外の場合は、必要に応じて通貨記号が一致します。  
  
 インスタンスがない場合**要素**します。 `thousands_sep`通貨入力フィールドの値の部分で発生する (場所と等しい要素**money_base::value**フォーマット パターンが表示されます)、グループ化の制約は適用されません。 によって、グループ化の制約が課されるそれ以外の場合、**要素**します。 **グループ化**が適用されます。 結果の数字のシーケンスを表します整数の下位**要素**します。 `frac_digits`小数点以下桁数、小数点の右側と見なされます。  
  
 任意の余白は、書式パターンの末尾以外に出現する場合、**money_base::space** と等しい要素が書式パターンに出現しているときに一致します。 それ以外の場合、内部の余白は一致しません。 要素*ch*場合に、空白文字と見なされますが[use_facet](../standard-library/locale-functions.md#use_facet) < [ctype](../standard-library/ctype-class.md) \< **CharType**> > ( **iosbase**します。 [getloc](../standard-library/ios-base-class.md#ios_base__getloc))。 [is](../standard-library/ctype-class.md#ctype__is)( **ctype_base::space**, *ch*) is **true**.  
  
### <a name="example"></a>例  
  [get](#money_get__get) の例 (`do_get` を呼び出す) を参照してください。  
  
##  <a name="a-namemoneygetgeta--moneygetget"></a><a name="money_get__get"></a>  money_get::get  
 通貨値を表す文字シーケンスから数値を抽出します。  
  
```
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
 `first`  
 変換されるシーケンスの開始位置を示す入力反復子。  
  
 `last`  
 変換されるシーケンスの終了位置を示す入力反復子。  
  
 `Intl`  
 シーケンスで期待される通貨記号の種類を示すブール値。国際通貨の場合は **true**、国内通貨の場合は **false**。  
  
 `Iosbase`  
 書式設定フラグ。これが設定されている場合、通貨記号は省略可能です。それ以外の場合は必須です  
  
 `State`  
 操作が成功したかどうかに基づき、ストリームの状態に適したビットマスク要素を設定します。  
  
 `val`  
 変換後のシーケンスを格納する文字列。  
  
### <a name="return-value"></a>戻り値  
 通貨入力フィールドを超える先頭の要素を示す入力反復子。  
  
### <a name="remarks"></a>コメント  
 どちらのメンバー関数も [do_get](#money_get__do_get)( `first``,` `last``,` `Intl`, `Iosbase`, `State`, `val`) を返します。  
  
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
  
##  <a name="a-namemoneygetitertypea--moneygetitertype"></a><a name="money_get__iter_type"></a>  money_get::iter_type  
 入力反復子を表す型。  
  
```
typedef InputIterator iter_type;
```  
  
### <a name="remarks"></a>コメント  
 この型は、テンプレート パラメーター **InputIterator** のシノニムです。  
  
##  <a name="a-namemoneygetmoneygeta--moneygetmoneyget"></a><a name="money_get__money_get"></a>  money_get::money_get  
 通貨値を表すシーケンスから数値を抽出するために使用される `money_get` 型のオブジェクトのコンストラクター。  
  
```
explicit money_get(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>パラメーター  
 `_Refs`  
 オブジェクトのメモリ管理のタイプを指定するために使用する整数値。  
  
### <a name="remarks"></a>コメント  
 `_Refs` パラメーターの可能な値とその重要性は次のとおりです。  
  
-   0: オブジェクトの有効期間はそれが含まれるロケールによって管理されます。  
  
-   1: オブジェクトの有効期間を手動で管理する必要があります。  
  
-   \> 0: これらの値は定義されていません。  
  
 デストラクターが保護されているため、利用できる直接的な例はありません。  
  
 コンストラクターは、**locale::**[facet](../standard-library/locale-class.md#facet_class)( **_***Refs*) を使用して、その基本オブジェクトを初期化します。  
  
##  <a name="a-namemoneygetstringtypea--moneygetstringtype"></a><a name="money_get__string_type"></a>  money_get::string_type  
 **CharType** 型の文字を格納する文字列を表す型。  
  
```
typedef basic_string<CharType, Traits, Allocator> string_type;
```  
  
### <a name="remarks"></a>コメント  
 この型は、特殊化したテンプレート クラス [basic_string](../standard-library/basic-string-class.md) を表します。  
  
## <a name="see-also"></a>関連項目  
 [\<locale>](../standard-library/locale.md)   
 [facet クラス](../standard-library/locale-class.md#facet_class)   
 [C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)



