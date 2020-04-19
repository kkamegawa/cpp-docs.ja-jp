---
title: time_put クラス
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_put
- locale/std::time_put::char_type
- locale/std::time_put::iter_type
- locale/std::time_put::do_put
- locale/std::time_put::put
helpviewer_keywords:
- std::time_put [C++]
- std::time_put [C++], char_type
- std::time_put [C++], iter_type
- std::time_put [C++], do_put
- std::time_put [C++], put
ms.assetid: df79493e-3331-48d2-97c3-ac3a745f0791
ms.openlocfilehash: 2c0ae501693a8abffc72a23be9c427f31bad65b6
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685417"
---
# <a name="time_put-class"></a>time_put クラス

クラステンプレートは、時刻値から `CharType` 型のシーケンスへの変換を制御するためにロケールファセットとして使用できるオブジェクトを表します。

## <a name="syntax"></a>構文

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class time_put : public locale::facet;
```

### <a name="parameters"></a>パラメーター

*Chartype* \
文字をエンコードするためにプログラム内で使用される型。

*OutputIterator* \
時刻の put 関数が出力を書き込む反復子の型。

## <a name="remarks"></a>Remarks

すべてのロケールのファセットと同様、静的オブジェクト ID に最初に格納されている値は 0 です。 格納されている値に初めてアクセスしようとすると、**id** に一意の正の値が格納されます。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[time_put](#time_put)|`time_put` 型のオブジェクトのコンストラクター。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[char_type](#char_type)|ロケールによって使用される文字を表すために使用される型。|
|[iter_type](#iter_type)|出力反復子を表す型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[do_put](#do_put)|時刻と日付の情報を `CharType` のシーケンスとして出力する仮想関数。|
|[put](#put)|時刻と日付の情報を `CharType` のシーケンスとして出力します。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<locale>

**名前空間:** std

## <a name="char_type"></a>  time_put::char_type

ロケールによって使用される文字を表すために使用される型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター `CharType` のシノニムです。

## <a name="do_put"></a>  time_put::do_put

時刻と日付の情報を `CharType` のシーケンスとして出力する仮想関数。

```cpp
virtual iter_type do_put(
    iter_type next,
    ios_base& _Iosbase,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;
```

### <a name="parameters"></a>パラメーター

*次*の \
時刻と日付を表す文字のシーケンスが挿入される出力反復子。

*_Iosbase* \
使用されません。

*ポイント \ (_d)*
出力される時刻と日付の情報。

*_Fmt* \
出力の形式。 有効な値については、「[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)」を参照してください。

*Mod \ (_t)*
形式の修飾子。 有効な値については、「[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)」を参照してください。

### <a name="return-value"></a>戻り値

最後に挿入された要素の後の最初の位置を指す反復子。

### <a name="remarks"></a>Remarks

仮想プロテクトメンバー関数は、`tm` 型のオブジェクト \* `_Pt` に格納されている時刻値から `next` から始まる連続する要素を生成します。 関数は、生成された出力を超える、次に要素を挿入する場所を指定する反復子を返します。

出力は、一連の**char**要素を配列に生成するため*に、最後の引数*である、`strftime` で使用されるものと同じ規則によって生成されます。 このような**char**要素は、単純な一対一のマッピングによって `CharType` 型の同等の要素にマップされると想定されます。 *Mod*が0の場合、有効な形式は "% F" です。 F は *_Fmt*に置き換えられます。 それ以外の場合、有効な形式は "% MF" で、M は*Mod*で置き換えられます。

### <a name="example"></a>例

[put](#put) の例 (`do_put` を呼び出す) を参照してください。

## <a name="iter_type"></a>  time_put::iter_type

出力反復子を表す型。

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター `OutputIterator` のシノニムです。

## <a name="put"></a>  time_put::put

時刻と日付の情報を `CharType` のシーケンスとして出力します。

```cpp
iter_type put(iter_type next,
    ios_base& _Iosbase,
    char_type _Fill,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;

iter_type put(iter_type next,
    ios_base& _Iosbase,
    char_type _Fill,
    const tm* _Pt,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>パラメーター

*次*の \
時刻と日付を表す文字のシーケンスが挿入される出力反復子。

*_Iosbase* \
使用されません。

@No__t_1 の*塗りつぶし (_c)*
スペーシングに使用 `CharType` 型の文字。

*ポイント \ (_d)*
出力される時刻と日付の情報。

*_Fmt* \
出力の形式。 有効な値については、「[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)」を参照してください。

*Mod \ (_t)*
形式の修飾子。 有効な値については、「[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)」を参照してください。

*最初*の \
出力の書式設定文字列の先頭。 有効な値については、「[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)」を参照してください。

*最後*の \
出力の書式設定文字列の末尾。 有効な値については、「[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)」を参照してください。

### <a name="return-value"></a>戻り値

最後に挿入された要素の後の最初の位置を指す反復子。

### <a name="remarks"></a>Remarks

1つ目のメンバー関数は、 [do_put](#do_put)(`next`、`_Iosbase`、`_Fill`、`_Pt`、`_Fmt`、`_Mod`) を返します。 2 番目のメンバー関数は、\* `next` ++ に、間隔 [ `first`, `last`) のパーセント (%) 以外のすべての要素をコピーします。 間隔 [`first`、`last`) の文字*C*の後にパーセントを指定する場合、関数は `next`  =  `do_put` (`next`、`_Iosbase`、`_Fill`、`_Pt`、 *C*、0) を評価し、 *c*をスキップします。ただし、 *C*が set EOQ # の修飾子文字であり、その後に [4, 5) 内の文字 3 が続く場合、関数は代わりに 6 7 8 (9 を評価し 0、1、2、3、 *C*) をスキップし、過去の 5 をスキップします。

### <a name="example"></a>例

```cpp
// time_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   t.tm_hour = 5;
   t.tm_min = 30;
   t.tm_sec = 40;
   t.tm_year = 00;
   t.tm_mday = 4;
   t.tm_mon = 6;

   pszPutI.imbue( loc );
   char *pattern = "x: %X %x";
   use_facet <time_put <char> >
   (loc).put(basic_ostream<char>::_Iter(pszPutI.rdbuf( )),
          pszPutI, ' ', &t, pattern, pattern+strlen(pattern));

      cout << "num_put( ) = " << pszPutI.rdbuf( )->str( ) << endl;

      char strftimebuf[255];
      strftime(&strftimebuf[0], 255, pattern, &t);
      cout << "strftime( ) = " << &strftimebuf[0] << endl;
}
```

```Output
num_put( ) = x: 05:30:40 07/04/00
strftime( ) = x: 05:30:40 07/04/00
```

## <a name="time_put"></a>  time_put::time_put

`time_put` 型のオブジェクトのコンストラクター。

```cpp
explicit time_put(size_t _Refs = 0);
```

### <a name="parameters"></a>パラメーター

*Refs \ (_c)*
オブジェクトのメモリ管理のタイプを指定するために使用する整数値。

### <a name="remarks"></a>Remarks

*Refs*パラメーターに指定できる値とその意味は、次のとおりです。

- 0: オブジェクトの有効期間はそれが含まれるロケールによって管理されます。

- 1: オブジェクトの有効期間を手動で管理する必要があります。

- \> 1: これらの値は定義されていません。

コンストラクターは、 [locale:: facet](../standard-library/locale-class.md#facet_class)( *(Refs*) を使用して、その基本オブジェクトを初期化します。

## <a name="see-also"></a>関連項目

[\<locale>](../standard-library/locale.md)\
[time_base クラス](../standard-library/time-base-class.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
