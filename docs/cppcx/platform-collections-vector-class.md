---
title: Platform::Collections::Vector クラス
ms.date: 12/04/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::Vector::Vector
- COLLECTION/Platform::Collections::Vector::Append
- COLLECTION/Platform::Collections::Vector::Clear
- COLLECTION/Platform::Collections::Vector::First
- COLLECTION/Platform::Collections::Vector::GetAt
- COLLECTION/Platform::Collections::Vector::GetMany
- COLLECTION/Platform::Collections::Vector::GetView
- COLLECTION/Platform::Collections::Vector::IndexOf
- COLLECTION/Platform::Collections::Vector::InsertAt
- COLLECTION/Platform::Collections::Vector::ReplaceAll
- COLLECTION/Platform::Collections::Vector::RemoveAt
- COLLECTION/Platform::Collections::Vector::RemoveAtEnd
- COLLECTION/Platform::Collections::Vector::SetAt
- COLLECTION/Platform::Collections::Vector::Size
- COLLECTION/Platform::Collections::Vector::VectorChanged
helpviewer_keywords:
- Vector Class (C++/Cx)
ms.assetid: aee8c076-9700-47c3-99b6-799fd3edb0ca
ms.openlocfilehash: b7774c2cdab7b9abcb3ebac1453779055eacf897
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857893"
---
# <a name="platformcollectionsvector-class"></a>Platform::Collections::Vector クラス

インデックスによって個別にアクセスできるオブジェクトのシーケンシャル コレクションを表します。 XAML[データバインディング](/windows/uwp/data-binding/data-binding-in-depth)を支援するために、 [Windows:: Foundation:: Collections:: IObservableVector](/uwp/api/Windows.Foundation.Collections.IObservableVector_T_)を実装します。

## <a name="syntax"></a>構文

```
template <typename T, typename E>
   ref class Vector sealed;
```

### <a name="parameters"></a>パラメーター

*T*<br/>
Vector オブジェクトに含まれている要素の型。

*E*<br/>
*T*型の値と等しいかどうかをテストするための二項述語を指定します。既定値は `std::equal_to<T>`です。

### <a name="remarks"></a>Remarks

使用できる型は次のとおりです。

1. 整数

1. インターフェイスクラス ^

1. パブリック ref クラス ^

1. 値構造体

1. パブリック列挙型クラス

**Vector**クラスは、 C++ [Windows:: Foundation:: Collections:: ivector](/uwp/api/Windows.Foundation.Collections.IVector_T_)インターフェイスの具象実装です。

パブリックの戻り値またはパラメーターで**Vector**型を使用しようとすると、コンパイラエラー C3986 が発生します。 このエラーを修正するには、パラメーターまたは戻り値の型を [Windows::Foundation::Collections::IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_)に変更します。 詳細については、「 [Collections (C++/CX) (コレクション (C++/CX))](../cppcx/collections-c-cx.md)」を参照してください。

### <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|[名前]|説明|
|----------|-----------------|
|[Vector:: Vector](#ctor)|ベクター クラスの新しいインスタンスを初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|[名前]|説明|
|----------|-----------------|
|[Vector:: Append](#append)|指定された項目を、現在の Vector の最後の項目の後に挿入します。|
|[Vector:: Clear](#clear)|現在のベクター内のすべての要素を削除します。|
|[Vector:: First](#first)|Vector 内の最初の要素を指定する反復子を返します。|
|[Vector::GetAt](#getat)|指定されたインデックスで識別される現在のベクターの要素を取得します。|
|[Vector:: GetMany](#getmany)|指定されたインデックスを開始位置として、現在の Vector から項目のシーケンスを取得します。|
|[Vector:: GetView](#getview)|ベクターの読み取り専用ビュー、つまり [Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md)を返します。|
|[Vector:: IndexOf](#indexof)|現在のベクター内で指定された項目を検索し、見つかった場合は項目のインデックスを返します。|
|[Vector::InsertAt](#insertat)|現在のベクター内の指定したインデックスによって識別される要素の位置に、指定した項目を挿入します。|
|[Vector::ReplaceAll](#replaceall)|現在のベクターの要素を削除し、指定された配列の要素を挿入します。|
|[Vector::RemoveAt](#removeat)|現在のベクターから指定されたインデックスで識別される要素を削除します。|
|[Vector::RemoveAtEnd](#removeatend)|現在の Vector の末尾から要素を削除します。|
|[Vector:: SetAt](#setat)|現在の Vector で、指定されたインデックスによって識別される要素に、指定された値を割り当てます。|
|[Vector:: Size](#size)|現在のベクター オブジェクトの要素数を返します。|

### <a name="events"></a>Events

|||
|-|-|
|[名前]|説明|
|イベント[Windows:: Foundation:: Collection:: VectorChangedEventHandler\<t > ^ VectorChanged](/uwp/api/windows.foundation.collections.vectorchangedeventhandler)|Vector が変更されたときに発生します。|

## <a name="inheritance-hierarchy"></a>継承階層

`Vector`

### <a name="requirements"></a>要件

**ヘッダー:** collection.h

**名前空間:** Platform::Collections

## <a name="append"></a>Vector:: Append メソッド

指定された項目を、現在の Vector の最後の項目の後に挿入します。

### <a name="syntax"></a>構文

```cpp
virtual void Append(T item);
```

### <a name="parameters"></a>パラメーター

*index*<br/>
Vector に挿入する項目。 *項目*の型は、 *T*型名によって定義されます。

## <a name="clear"></a>Vector:: Clear メソッド

現在のベクター内のすべての要素を削除します。

### <a name="syntax"></a>構文

```cpp
virtual void Clear();
```

## <a name="first"></a>Vector:: First メソッド

Vector 内の最初の要素を指す反復子を返します。

### <a name="syntax"></a>構文

```cpp
virtual Windows::Foundation::Collections::IIterator <T>^ First();
```

### <a name="return-value"></a>戻り値

Vector 内の最初の要素を指す反復子。

### <a name="remarks"></a>Remarks

First () によって返される反復子を保持する便利な方法は、 **auto**型推論キーワードで宣言された変数に戻り値を代入することです。 たとえば、`auto x = myVector->First();` のようにします。 この反復子は、コレクションの長さを認識しています。

STL 関数に渡す反復子のペアが必要な場合は、free 関数の[windows:: foundation:: collections:: begin](../cppcx/begin-function.md)および[Windows:: Foundation:: collections:: end](../cppcx/end-function.md)を使用します。

## <a name="getat"></a>Vector:: GetAt メソッド

指定されたインデックスで識別される現在のベクターの要素を取得します。

### <a name="syntax"></a>構文

```cpp
virtual T GetAt(unsigned int index);
```

### <a name="parameters"></a>パラメーター

*index*<br/>
ベクター オブジェクト内の特定の要素を指定する、0 から始まる符号なし整数。

### <a name="return-value"></a>戻り値

*Index*パラメーターによって指定された要素。 要素の型は、 *T*型名によって定義されます。

## <a name="getmany"></a>Vector:: GetMany メソッド

指定されたインデックスを開始位置として、現在の Vector から項目のシーケンスを取得し、呼び出し元が割り当てた配列にコピーします。

### <a name="syntax"></a>構文

```cpp
virtual unsigned int GetMany(
    unsigned int startIndex,
    Platform::WriteOnlyArray<T>^ dest);
```

### <a name="parameters"></a>パラメーター

*startIndex*<br/>
取得する項目の 0 から始まるインデックス。

*dest*<br/>
*StartIndex*によって指定された要素から開始し、ベクターの最後の要素で終了する項目の、呼び出し元が割り当てた配列。

### <a name="return-value"></a>戻り値

取得した項目数。

### <a name="remarks"></a>Remarks

この関数は、直接クライアント コードで使用することを目的としたものではありません。 Platform:: Vector インスタンスから std:: vector インスタンスへの効率的な変換を可能にするために、 [To_vector 関数](../cppcx/to-vector-function.md)で内部的に使用されます。

## <a name="getview"></a>Vector:: GetView メソッド

Vector の読み取り専用ビュー、つまり IVectorView を返します。

### <a name="syntax"></a>構文

```cpp
Windows::Foundation::Collections::IVectorView<T>^ GetView();
```

### <a name="return-value"></a>戻り値

IVectorView オブジェクト。

## <a name="indexof"></a>Vector:: IndexOf メソッド

現在のベクター内で指定された項目を検索し、見つかった場合は項目のインデックスを返します。

### <a name="syntax"></a>構文

```cpp
virtual bool IndexOf(T value, unsigned int* index);
```

### <a name="parameters"></a>パラメーター

*value*<br/>
検索する項目。

*index*<br/>
パラメーター*値*が見つかった場合は、項目の0から始まるインデックス。それ以外の場合は0です。

*インデックス*パラメーターは、項目がベクターの最初の要素であるか、項目が見つからなかった場合は0になります。 戻り値が**true**の場合、項目が見つかり、それが最初の要素になります。それ以外の場合、項目は見つかりませんでした。

### <a name="return-value"></a>戻り値

指定した項目が見つかった場合は**true** 。それ以外の場合は**false**。

### <a name="remarks"></a>Remarks

IndexOf は、std::find_if を使用して項目を検索します。 このため、find_if が必要とする等価比較を有効にするために、カスタム要素の種類で == および != 演算子をオーバーロードする必要があります。

##  <a name="insertat"></a>Vector:: InsertAt メソッド

現在のベクター内の指定したインデックスによって識別される要素の位置に、指定した項目を挿入します。

### <a name="syntax"></a>構文

```cpp
virtual void InsertAt(unsigned int index, T item)
```

### <a name="parameters"></a>パラメーター

*index*<br/>
ベクター オブジェクト内の特定の要素を指定する、0 から始まる符号なし整数。

*item*<br/>
*Index*で指定された要素のベクターに挿入する項目。 *項目*の型は、 *T*型名によって定義されます。

## <a name="removeat"></a>Vector:: RemoveAt メソッド

現在のベクターから指定されたインデックスで識別される要素を削除します。

### <a name="syntax"></a>構文

```cpp
virtual void RemoveAt(unsigned int index);
```

### <a name="parameters"></a>パラメーター

*index*<br/>
ベクター オブジェクト内の特定の要素を指定する、0 から始まる符号なし整数。

## <a name="removeatend"></a>Vector:: RemoveAtEnd メソッド

現在の Vector の末尾から要素を削除します。

### <a name="syntax"></a>構文

```cpp
virtual void RemoveAtEnd();
```

## <a name="replaceall"></a>Vector:: ReplaceAll メソッド

現在のベクターの要素を削除し、指定された配列の要素を挿入します。

### <a name="syntax"></a>構文

```cpp
virtual void ReplaceAll(const ::Platform::Array<T>^ arr);
```

### <a name="parameters"></a>パラメーター

*arr*<br/>
*T*型名によって定義される型を持つオブジェクトの配列。

## <a name="setat"></a>Vector:: SetAt メソッド

現在の Vector で、指定されたインデックスによって識別される要素に、指定された値を割り当てます。

### <a name="syntax"></a>構文

```cpp
virtual void SetAt(unsigned int index, T item);
```

### <a name="parameters"></a>パラメーター

*index*<br/>
ベクター オブジェクト内の特定の要素を指定する、0 から始まる符号なし整数。

*item*<br/>
指定された要素に代入する値。 *項目*の型は、 *T*型名によって定義されます。

## <a name="size"></a>Vector:: Size メソッド

現在のベクター オブジェクトの要素数を返します。

### <a name="syntax"></a>構文

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>戻り値

現在の Vector 内の要素数。

## <a name="ctor"></a>Vector:: Vector コンストラクター

ベクター クラスの新しいインスタンスを初期化します。

### <a name="syntax"></a>構文

```cpp
Vector();

explicit Vector(unsigned int size);
Vector( unsigned int size, T value);
template <typename U> explicit Vector( const ::std::vector<U>& v);
template <typename U> explicit Vector( std::vector<U>&& v);

Vector( const T * ptr, unsigned int size);
template <size_t N> explicit Vector(const T(&arr)[N]);
template <size_t N> explicit Vector(const std::array<T, N>& a);
explicit Vector(const Array<T>^ arr);

template <typename InIt> Vector(InIt first, InIt last);
Vector(std::initializer_list<T> il);
```

### <a name="parameters"></a>パラメーター

*a*<br/>
ベクターを初期化するために使用される[std:: array](../standard-library/array-class-stl.md) 。

*arr*<br/>
ベクターを初期化するために使用される[Platform:: Array](../cppcx/platform-array-class.md) 。

*InIt*<br/>
現在のベクターを初期化するために使用されるオブジェクトのコレクションの型。

*il*<br/>
ベクターの初期化に使用される*T*型のオブジェクトの[std:: initializer_list](../standard-library/initializer-list-class.md) 。

*N*<br/>
現在のベクターを初期化するために使用されるオブジェクトのコレクションの要素数。

*size*<br/>
ベクターの要素数。

*value*<br/>
現在のベクターの各要素を初期化するために使用される値。

*v*<br/>
現在のベクターを初期化するために使用される[std:: vector](../standard-library/vector-class.md)の[左辺値と右辺値](../cpp/lvalues-and-rvalues-visual-cpp.md)。

*ptr*<br/>
現在のベクターを初期化するために使用される `std::vector` へのポインター。

*first*<br/>
現在のベクターを初期化するために使用されるオブジェクトのシーケンスの最初の要素。 *最初*のの型は、*完全転送*によって渡されます。 詳細については、「[右辺値参照宣言子: &&](../cpp/rvalue-reference-declarator-amp-amp.md)」を参照してください。

*last*<br/>
現在のベクターを初期化するために使用されるオブジェクトのシーケンスの最後の要素。 *最後*のの種類は、*完全転送*によって渡されます。 詳細については、「[右辺値参照宣言子: &&](../cpp/rvalue-reference-declarator-amp-amp.md)」を参照してください。

## <a name="see-also"></a>参照

[コレクション (C++/CX)](collections-c-cx.md)<br/>
[Platform 名前空間](platform-namespace-c-cx.md)<br/>
[C++ で Windows ランタイム コンポーネントを作成する](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
