---
title: '&lt;ostream&gt; 関数'
ms.date: 11/04/2016
f1_keywords:
- ostream/std::swap
- ostream/std::endl
- ostream/std::ends
- ostream/std::flush
ms.assetid: d6e56cc0-c8df-4dbe-be10-98e14c35ed3a
helpviewer_keywords:
- std::swap [C++]
- std::endl [C++]
- std::ends [C++]
- std::flush [C++]
ms.openlocfilehash: 8d93e46b0323058d93c6d0bd8c1ee566998aef61
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447192"
---
# <a name="ltostreamgt-functions"></a>&lt;ostream&gt; 関数

これらは、ostream &lt;&gt;で定義されているグローバルテンプレート関数です。 メンバー関数については、 [Basic_ostream クラス](basic-ostream-class.md)のドキュメントを参照してください。

||||
|-|-|-|
|[endl](#endl)|[ends](#ends)|[flush](#flush)|
|[swap](#swap)|

## <a name="endl"></a>endl

行を終了し、バッファーをフラッシュします。

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& endl(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>パラメーター

*Elem*\
要素型。

*Ostr*\
**Basic_ostream**型のオブジェクト。

*Tr*\
文字の特徴 (traits)。

### <a name="return-value"></a>戻り値

**Basic_ostream**型のオブジェクト。

### <a name="remarks"></a>Remarks

マニピュレーターは*Ostr*を呼び出します。[put](../standard-library/basic-ostream-class.md#put)(*Ostr*。[拡大](../standard-library/basic-ios-class.md#widen)(' \n ')) を呼び出し、 *Ostr*を呼び出します。[フラッシュ](../standard-library/basic-ostream-class.md#flush)。 *Ostr*が返されます。

### <a name="example"></a>例

```cpp
// ostream_endl.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "testing" << endl;
}
```

```Output
testing
```

## <a name="ends"></a>終点

文字列を終了します。

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& ends(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>パラメーター

*Elem*\
要素型。

*Ostr*\
`basic_ostream` 型のオブジェクト。

*Tr*\
文字の特徴 (traits)。

### <a name="return-value"></a>戻り値

`basic_ostream` 型のオブジェクト。

### <a name="remarks"></a>Remarks

マニピュレーターは*Ostr*を呼び出します。[put](../standard-library/basic-ostream-class.md#put)(*Elem*(' \ 0 '))。 *Ostr*が返されます。

### <a name="example"></a>例

```cpp
// ostream_ends.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "a";
   cout << "b" << ends;
   cout << "c" << endl;
}
```

```Output
ab c
```

## <a name="flush"></a>flush

バッファーをフラッシュします。

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& flush(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>パラメーター

*Elem*\
要素型。

*Ostr*\
`basic_ostream` 型のオブジェクト。

*Tr*\
文字の特徴 (traits)。

### <a name="return-value"></a>戻り値

`basic_ostream` 型のオブジェクト。

### <a name="remarks"></a>Remarks

マニピュレーターは*Ostr*を呼び出します。[フラッシュ](../standard-library/basic-ostream-class.md#flush)。 *Ostr*が返されます。

### <a name="example"></a>例

```cpp
// ostream_flush.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "testing" << flush;
}
```

```Output
testing
```

## <a name="swap"></a>swap

2 つの `basic_ostream` オブジェクトの値を交換します。

```cpp
template <class Elem, class Tr>
void swap(
   basic_ostream<Elem, Tr>& left,
   basic_ostream<Elem, Tr>& right);
```

### <a name="parameters"></a>パラメーター

*Elem*\
要素型。

*Tr*\
文字の特徴 (traits)。

*左側*\
`basic_ostream` オブジェクトへの左辺値参照。

*そうです*\
`basic_ostream` オブジェクトへの左辺値参照。

### <a name="remarks"></a>Remarks

テンプレート関数 `swap` は、`left.swap(right)` を実行します。

## <a name="see-also"></a>関連項目

[\<ostream>](../standard-library/ostream.md)
