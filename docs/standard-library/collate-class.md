---
title: collate クラス
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate
- locale/std::collate::char_type
- locale/std::collate::string_type
- locale/std::collate::compare
- locale/std::collate::do_compare
- locale/std::collate::do_hash
- locale/std::collate::do_transform
- locale/std::collate::hash
- locale/std::collate::transform
helpviewer_keywords:
- std::collate [C++]
- std::collate [C++], char_type
- std::collate [C++], string_type
- std::collate [C++], compare
- std::collate [C++], do_compare
- std::collate [C++], do_hash
- std::collate [C++], do_transform
- std::collate [C++], hash
- std::collate [C++], transform
ms.assetid: 92168798-9628-4a2e-be6e-fa62dcd4d6a6
ms.openlocfilehash: 88b04ad4f14faf4d152c0ce2b9c3477928263c52
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689819"
---
# <a name="collate-class"></a>collate クラス

文字列内の文字の順序付けとグループ化、文字列内の文字の比較、および文字列のハッシュ処理を制御するためにロケールファセットとして使用できるオブジェクトを表すクラステンプレート。

## <a name="syntax"></a>構文

```cpp
template <class CharType>
class collate : public locale::facet;
```

### <a name="parameters"></a>パラメーター

*Chartype* \
文字をエンコードするためにプログラム内で使用される型。

## <a name="remarks"></a>Remarks

すべてのロケールのファセットと同様、静的オブジェクト ID に最初に格納されている値は 0 です。 格納されている値に初めてアクセスしようとすると、`id` に一意の正の値が格納されます。 一部の言語では、複数の文字が 1 文字のように処理され、また別の言語では、個々の文字が 2 文字であるかのように処理されます。 照合クラスが提供する照合サービスは、これらの状況で文字を並べ替える方法を示します。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[collate](#collate)|文字列の並べ替え規則を処理するためにロケールのファセットとして機能する `collate` クラスのオブジェクトのコンストラクター。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[char_type](#char_type)|`CharType` 型の文字を表す型。|
|[string_type](#string_type)|`basic_string` 型の文字を格納する `CharType` 型の文字列を表す型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[compare](#compare)|等値または非等値のファセット固有の規則に従って、2 文字シーケンスを比較します。|
|[do_compare](#do_compare)|等値または非等値のファセット固有の規則に従って、2 文字シーケンスを比較するために呼び出される仮想関数。|
|[do_hash](#do_hash)|ファセット固有の規則に従ってシーケンスのハッシュ値を決定するために呼び出される仮想関数。|
|[do_transform](#do_transform)|ロケールの文字シーケンスを、同じロケールから同様に変換された他の文字シーケンスとの辞書式の比較で使用できる文字列に変換するために呼び出される仮想関数。|
|[hash](#hash)|ファセット固有の規則に従ってシーケンスのハッシュ値を決定します。|
|[transform](#transform)|ロケールの文字シーケンスを、同じロケールから同様に変換された他の文字シーケンスとの辞書式の比較で使用できる文字列に変換します。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<locale>

**名前空間:** std

## <a name="char_type"></a>  collate::char_type

`CharType` 型の文字を表す型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター `CharType` のシノニムです。

## <a name="collate"></a>  collate::collate

文字列の並べ替え規則を処理するためにロケール ファセットとして機能する collate クラスのオブジェクトのコンストラクター。

```cpp
public:
    explicit collate(
    size_t _Refs = 0);

protected:
    collate(
const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>パラメーター

*Refs \ (_c)*
オブジェクトのメモリ管理のタイプを指定するために使用する整数値。

*@No__t_1*
ロケールの名前。

### <a name="remarks"></a>Remarks

*Refs*パラメーターに指定できる値とその意味は、次のとおりです。

- 0: オブジェクトの有効期間はそれが含まれるロケールによって管理されます。

- 1: オブジェクトの有効期間を手動で管理する必要があります。

- \> 1: これらの値は定義されていません。

コンストラクターは、 **locale::** [facet](../standard-library/locale-class.md#facet_class)(`_Refs`) を使用して、その基本オブジェクトを初期化します。

## <a name="compare"></a>  collate::compare

等値または非等値のファセット固有の規則に従って、2 文字シーケンスを比較します。

```cpp
int compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>パラメーター

*first1* \
比較する最初のシーケンスの最初の要素へのポインター。

*last1* \
比較する最初のシーケンスの最後の要素へのポインター。

*first2* \
比較する 2 番目のシーケンスの最初の要素へのポインター。

*last2* \
比較する 2 番目のシーケンスの最後の要素へのポインター。

### <a name="return-value"></a>戻り値

このメンバー関数は、以下の値を返します。

- 最初のシーケンスが 2 番目のシーケンスより小さい場合は、-1。

- 2 番目のシーケンスが最初のシーケンスより小さい場合は、+1。

- シーケンスが等しい場合は 0。

### <a name="remarks"></a>Remarks

シーケンスの最も早い等しくないペアにより小さい要素がある場合、または等しくないペアは存在しないが、最初のシーケンスの方が短い場合は、最初のシーケンスが小さいと見なされます。

このメンバー関数は、[do_compare](#do_compare)( `first1`, `last1`, `first2`, `last2`) を返します。

### <a name="example"></a>例

```cpp
// collate_compare.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main() {
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s, it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare ( s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << result1 << endl;

   locale loc2 ( "C" );
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << result2 << endl;
}
```

## <a name="do_compare"></a>  collate::do_compare

等値または非等値のファセット固有の規則に従って、2 文字シーケンスを比較するために呼び出される仮想関数。

```cpp
virtual int do_compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>パラメーター

*first1* \
比較する最初のシーケンスの最初の要素へのポインター。

*last1* \
比較する最初のシーケンスの最後の要素へのポインター。

*first2* \
比較する 2 番目のシーケンスの最初の要素へのポインター。

*last2* \
比較する 2 番目のシーケンスの最後の要素へのポインター。

### <a name="return-value"></a>戻り値

このメンバー関数は、以下の値を返します。

- 最初のシーケンスが 2 番目のシーケンスより小さい場合は、-1。

- 2 番目のシーケンスが最初のシーケンスより小さい場合は、+1。

- シーケンスが等しい場合は 0。

### <a name="remarks"></a>Remarks

プロテクト仮想メンバー関数は、[* first1, Last1) * のシーケンスを、 *[first2, last2*) のシーケンスと比較します。 @No__t_1 型の対応する要素のペアの間に `operator<` を適用して値を比較します。 シーケンスの最も早い等しくないペアにより小さい要素がある場合、または等しくないペアは存在しないが、最初のシーケンスの方が短い場合は、最初のシーケンスが小さいと見なされます。

### <a name="example"></a>例

[collate::compare](#compare) の例 (`do_compare` を呼び出す) を参照してください。

## <a name="do_hash"></a>  collate::do_hash

ファセット固有の規則に従ってシーケンスのハッシュ値を決定するために呼び出される仮想関数。

```cpp
virtual long do_hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>パラメーター

*最初*の \
値を決定するシーケンスの最初の文字へのポインター。

*最後*の \
値を決定するシーケンスの最後の文字へのポインター。

### <a name="return-value"></a>戻り値

シーケンスの **long** 型のハッシュ値。

### <a name="remarks"></a>Remarks

ハッシュ値は、リストの配列で擬似ランダムにシーケンスを分散させる場合などに役立ちます。

### <a name="example"></a>例

[hash](#hash) の例 (`do_hash` を呼び出す) を参照してください。

## <a name="do_transform"></a>  collate::do_transform

ロケールの文字シーケンスを、同じロケールから同様に変換された他の文字シーケンスとの辞書式の比較で使用できる文字列に変換するために呼び出される仮想関数。

```cpp
virtual string_type do_transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>パラメーター

*最初*の \
変換対象となるシーケンスの最初の文字へのポインター。

*最後*の \
変換対象となるシーケンスの最後の文字へのポインター。

### <a name="return-value"></a>戻り値

変換された文字シーケンスである文字列。

### <a name="remarks"></a>Remarks

protected 仮想メンバー関数は、被制御シーケンスがシーケンス [ `first`, `last`) のコピーである [string_type](#string_type) クラスのオブジェクトを返します。 collate\< **CharType**> から派生したクラスで [do_compare](#do_compare) をオーバーライドする場合は、それに合わせて `do_transform` もオーバーライドする必要があります。 `collate::compare` に渡した場合、変換された 2 つの文字列の結果は、派生クラスで比較するために未変換文字列を渡した場合と同じものが生成される必要があります。

### <a name="example"></a>例

[transform](#transform) の例 (`do_transform` を呼び出す) を参照してください。

## <a name="hash"></a>  collate::hash

ファセット固有の規則に従ってシーケンスのハッシュ値を決定します。

```cpp
long hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>パラメーター

*最初*の \
値を決定するシーケンスの最初の文字へのポインター。

*最後*の \
値を決定するシーケンスの最後の文字へのポインター。

### <a name="return-value"></a>戻り値

シーケンスの **long** 型のハッシュ値。

### <a name="remarks"></a>Remarks

このメンバー関数は、[do_hash](#do_hash)( `first`, `last`) を返します。

ハッシュ値は、リストの配列で擬似ランダムにシーケンスを分散させる場合などに役立ちます。

### <a name="example"></a>例

```cpp
// collate_hash.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("\x00dfzz abc."); // \x00df is the German sharp-s (looks like beta), it comes before z in the alphabet
   _TCHAR * s2 = _T("zzz abc."); // \x00df is the German sharp-s (looks like beta), it comes before z in the alphabet

   long r1 = use_facet< collate<_TCHAR> > ( loc ).
      hash (s1, &s1[_tcslen( s1 )-1 ]);
   long r2 =  use_facet< collate<_TCHAR> > ( loc ).
      hash (s2, &s2[_tcslen( s2 )-1 ] );
   cout << r1 << " " << r2 << endl;
}
```

```Output
541187293 551279837
```

## <a name="string_type"></a>  collate::string_type

`basic_string` 型の文字を格納する `CharType` 型の文字列を表す型。

```cpp
typedef basic_string<CharType> string_type;
```

### <a name="remarks"></a>Remarks

この型は、ソースシーケンスのコピーを格納できるオブジェクトを持つクラステンプレート[basic_string](../standard-library/basic-string-class.md)の特殊化を表します。

### <a name="example"></a>例

`string_type` の宣言および使用方法の例については、「[collate::transform](#transform)」を参照してください。

## <a name="transform"></a>  collate::transform

ロケールの文字シーケンスを、同じロケールから同様に変換された他の文字シーケンスとの辞書式の比較で使用できる文字列に変換します。

```cpp
string_type transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>パラメーター

*最初*の \
変換対象となるシーケンスの最初の文字へのポインター。

*最後*の \
変換対象となるシーケンスの最後の文字へのポインター。

### <a name="return-value"></a>戻り値

変換された文字シーケンスを含む文字列。

### <a name="remarks"></a>Remarks

このメンバー関数は、 [do_transform](#do_transform)(`first`、`last`) を返します。

### <a name="example"></a>例

```cpp
// collate_transform.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   _TCHAR* s1 = _T("\x00dfzz abc.");
   // \x00df is the German sharp-s (looks like beta),
   // it comes before z in the alphabet
   _TCHAR* s2 = _T("zzz abc.");

   collate<_TCHAR>::string_type r1;   // OK for typedef
   r1 = use_facet< collate<_TCHAR> > ( loc ).
      transform (s1, &s1[_tcslen( s1 )-1 ]);

   cout << r1 << endl;

   basic_string<_TCHAR> r2 = use_facet< collate<_TCHAR> > ( loc ).
      transform (s2, &s2[_tcslen( s2 )-1 ]);

   cout << r2 << endl;

   int result1 = use_facet<collate<_TCHAR> > ( loc ).compare
      (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );

   cout << _tcscmp(r1.c_str( ),r2.c_str( )) << result1
      << _tcscmp(s1,s2) <<endl;
}
```

```Output

-1-11
```

## <a name="see-also"></a>関連項目

[\<locale>](../standard-library/locale.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
