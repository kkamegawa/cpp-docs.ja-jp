---
title: fpos クラス
ms.date: 03/27/2019
f1_keywords:
- iosfwd/std::fpos
- iosfwd/std::fpos::seekpos
- iosfwd/std::fpos::state
- iosfwd/std::fpos::operator streamoff
helpviewer_keywords:
- std::fpos [C++]
- std::fpos [C++], seekpos
- std::fpos [C++], state
ms.assetid: ffd0827c-fa34-47f4-b10e-5cb707fcde47
ms.openlocfilehash: cdca7b961d9aedad841692160c8313f8a306dec2
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689667"
---
# <a name="fpos-class"></a>fpos クラス

クラステンプレートは、任意のストリーム内の任意のファイル位置インジケーターを復元するために必要なすべての情報を格納できるオブジェクトを表します。 fpos\<**St**> クラスのオブジェクトには、実質的に 2 個以上のメンバー オブジェクトが格納されます。

- [streamoff](../standard-library/ios-typedefs.md#streamoff) 型のバイト オフセット。

- @No__t_0 型のクラス basic_filebuf のオブジェクトによって使用される変換状態。通常は `mbstate_t` です。

[basic_filebuf](../standard-library/basic-filebuf-class.md) クラスのオブジェクトで使用するために、`fpos_t` 型の任意のファイル位置も格納できます。 ただし、ファイル サイズが制限された環境では、`streamoff` と `fpos_t` が区別されずに使用される場合があります。 状態依存のエンコードを使用したストリームがない環境では、実際に `mbstate_t` が使用されていない場合があります。 したがって、格納されるメンバー オブジェクトの数が異なる場合があります。

## <a name="syntax"></a>構文

```cpp
template <class Statetype>
class fpos
```

### <a name="parameters"></a>パラメーター

*Statetype* \
状態情報。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[fpos](#fpos)|ストリーム内の位置 (オフセット) に関する情報を格納するオブジェクトを作成します。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[seekpos](#seekpos)|C++ 標準ライブラリのみによって内部的に使用されます。 このメソッドをコードから呼び出さないでください。|
|[state](#state)|変換状態を設定または返します。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator!=](#op_neq)|ファイル位置インジケーターが等しくないかどうかをテストします。|
|[operator+](#op_add)|ファイル位置インジケーターをインクリメントします。|
|[operator+=](#op_add_eq)|ファイル位置インジケーターをインクリメントします。|
|[operator-](#operator-)|ファイル位置インジケーターをデクリメントします。|
|[operator-=](#operator-_eq)|ファイル位置インジケーターをデクリメントします。|
|[operator==](#op_eq_eq)|ファイル位置インジケーターが等しいかどうかをテストします。|
|[operator streamoff](#op_streamoff)|`fpos` 型のオブジェクトを `streamoff` 型のオブジェクトにキャストします。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<ios>

**名前空間:** std

## <a name="fpos"></a>  fpos::fpos

ストリーム内の位置 (オフセット) に関する情報を格納するオブジェクトを作成します。

```cpp
fpos(streamoff _Off = 0);

fpos(Statetype _State, fpos_t _Filepos);
```

### <a name="parameters"></a>パラメーター

*オフ \ (_r)*
ストリームへのオフセット。

*状態 \ (_c)*
`fpos` オブジェクトの開始状態。

*Filepos \ (_s)*
ストリームへのオフセット。

### <a name="remarks"></a>Remarks

1つ目のコンストラクターは、ファイルの先頭と初期の変換状態 (それが重要な場合) に相対的に、オフセットを*オフ*にします。 *Off*が-1 の場合、結果として得られるオブジェクトは無効なストリームの位置を表します。

2番目のコンストラクターは、0オフセットとオブジェクトの*状態*を格納します。

## <a name="op_neq"></a>  fpos::operator!=

ファイル位置インジケーターが等しくないかどうかをテストします。

```cpp
bool operator!=(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>パラメーター

*右*\
比較するファイル位置インジケーター。

### <a name="return-value"></a>戻り値

ファイル位置インジケーターが等しくない場合は **true**。それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

このメンバー関数は、 `!(*this == right)`を返します。

### <a name="example"></a>例

```cpp
// fpos_op_neq.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;

   fpos<int> pos1, pos2;
   ifstream file;
   char c;

   // Compare two fpos object
   if ( pos1 != pos2 )
      cout << "File position pos1 and pos2 are not equal" << endl;
   else
      cout << "File position pos1 and pos2 are equal" << endl;

   file.open( "fpos_op_neq.txt" );
   file.seekg( 0 );   // Goes to a zero-based position in the file
   pos1 = file.tellg( );
   file.get( c);
   cout << c << endl;

   // Increment pos1
   pos1 += 1;
   file.get( c );
   cout << c << endl;

   pos1 = file.tellg( ) - fpos<int>( 2);
   file.seekg( pos1 );
   file.get( c );
   cout << c << endl;

   // Increment pos1
   pos1 = pos1 + fpos<int>( 1 );
   file.get(c);
   cout << c << endl;

   pos1 -= fpos<int>( 2 );
   file.seekg( pos1 );
   file.get( c );
   cout << c << endl;

   file.close( );
}
```

## <a name="op_add"></a>  fpos::operator+

ファイル位置インジケーターをインクリメントします。

```cpp
fpos<Statetype> operator+(streamoff _Off) const;
```

### <a name="parameters"></a>パラメーター

*オフ \ (_r)*
ファイル位置インジケーターをインクリメントするオフセット。

### <a name="return-value"></a>戻り値

ファイル内の位置。

### <a name="remarks"></a>Remarks

このメンバー関数は、**fpos(\*this) +=** `_Off` を返します。

### <a name="example"></a>例

`operator+` の使用例については、[operator!=](#op_neq) を参照してください。

## <a name="op_add_eq"></a>  fpos::operator+=

ファイル位置インジケーターをインクリメントします。

```cpp
fpos<Statetype>& operator+=(streamoff _Off);
```

### <a name="parameters"></a>パラメーター

*オフ \ (_r)*
ファイル位置インジケーターをインクリメントするオフセット。

### <a name="return-value"></a>戻り値

ファイル内の位置。

### <a name="remarks"></a>Remarks

このメンバー関数は、格納されているオフセットメンバーオブジェクトに*を追加してから、* **\*this**を返します。 ファイル内の位置を特定する場合、結果は一般に状態依存エンコーディングを持たないバイナリ ストリームについてのみ有効です。

### <a name="example"></a>例

`operator+=` の使用例については、[operator!=](#op_neq) を参照してください。

## <a name="operator-"></a>  fpos::operator-

ファイル位置インジケーターをデクリメントします。

```cpp
streamoff operator-(const fpos<Statetype>& right) const;

fpos<Statetype> operator-(streamoff _Off) const;
```

### <a name="parameters"></a>パラメーター

*右*\
ファイルの位置。

*オフ \ (_r)*
ストリームのオフセット。

### <a name="return-value"></a>戻り値

最初のメンバー関数は `(streamoff)*this - (streamoff) right` を返します。 2 番目のメンバー関数は `fpos(*this) -= _Off` を返します。

### <a name="example"></a>例

`operator-` の使用例については、[operator!=](#op_neq) を参照してください。

## <a name="operator-_eq"></a>  fpos::operator-=

ファイル位置インジケーターをデクリメントします。

```cpp
fpos<Statetype>& operator-=(streamoff _Off);
```

### <a name="parameters"></a>パラメーター

*オフ \ (_r)*
ストリームのオフセット。

### <a name="return-value"></a>戻り値

このメンバー関数は、 `fpos(*this) -= _Off`を返します。

### <a name="remarks"></a>Remarks

ファイル内の位置を特定する場合、結果は一般に状態依存エンコーディングを持たないバイナリ ストリームについてのみ有効です。

### <a name="example"></a>例

`operator-=` の使用例については、[operator!=](#op_neq) を参照してください。

## <a name="op_eq_eq"></a>  fpos::operator==

ファイル位置インジケーターが等しいかどうかをテストします。

```cpp
bool operator==(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>パラメーター

*右*\
比較するファイル位置インジケーター。

### <a name="return-value"></a>戻り値

ファイル位置インジケーターが等しい場合は **true**。それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

このメンバー関数は、 `(streamoff)*this == (streamoff)right`を返します。

### <a name="example"></a>例

`operator+=` の使用例については、[operator!=](#op_neq) を参照してください。

## <a name="op_streamoff"></a>  fpos::operator streamoff

`fpos` 型のオブジェクトを `streamoff` 型のオブジェクトにキャストします。

```cpp
operator streamoff() const;
```

### <a name="remarks"></a>Remarks

このメンバー関数は、格納されたオフセット メンバー オブジェクト、および `fpos_t` メンバー オブジェクトの一部として格納された追加のオフセットを返します。

### <a name="example"></a>例

```cpp
// fpos_op_streampos.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   streamoff s;
   ofstream file( "rdbuf.txt");

   fpos<mbstate_t> f = file.tellp( );
   // Is equivalent to ..
   // streampos f = file.tellp( );
   s = f;
   cout << s << endl;
}
```

```Output
0
```

## <a name="seekpos"></a>  fpos::seekpos

このメソッドは、C++ 標準ライブラリのみによって内部的に使用されます。 このメソッドをコードから呼び出さないでください。

```cpp
fpos_t seekpos() const;
```

## <a name="state"></a>  fpos::state

変換状態を設定または返します。

```cpp
Statetype state() const;

void state(Statetype _State);
```

### <a name="parameters"></a>パラメーター

*状態 \ (_c)*
新しい変換状態。

### <a name="return-value"></a>戻り値

変換状態。

### <a name="remarks"></a>Remarks

1つ目のメンバー関数は、`St` メンバーオブジェクトに格納されている値を返します。 2番目のメンバー関数は、*状態*を `St` メンバーオブジェクトに格納します。

### <a name="example"></a>例

```cpp
// fpos_state.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main() {
   using namespace std;
   streamoff s;
   ifstream file( "fpos_state.txt" );

   fpos<mbstate_t> f = file.tellg( );
   char ch;
   while ( !file.eof( ) )
      file.get( ch );
   s = f;
   cout << f.state( ) << endl;
   f.state( 9 );
   cout << f.state( ) << endl;
}
```

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream プログラミング](../standard-library/iostream-programming.md)\
[iostreams の規則](../standard-library/iostreams-conventions.md)
