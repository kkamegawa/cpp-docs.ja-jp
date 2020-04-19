---
title: Platform::Collections::UnorderedMapView クラス
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMapView
ms.assetid: 545a3725-2efd-4cc1-b590-4a7cd2351f61
ms.openlocfilehash: ebda6f179c365aaa009eb45425a36058105def10
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161635"
---
# <a name="platformcollectionsunorderedmapview-class"></a>Platform::Collections::UnorderedMapView クラス

キーと値のペアのコレクションである、 *マップ*への読み取り専用ビューを表します。

## <a name="syntax"></a>構文

```cpp
template <
   typename K,
   typename V,
   typename C = ::std::equal_to<K>>
ref class UnorderedMapView sealed;
```

#### <a name="parameters"></a>パラメーター

*K*<br/>
キー/値ペア内のキーの型。

*V*<br/>
キー/値ペア内の値の型。

*C*<br/>
2 つのキー値を比較して等価性を確認できる関数オブジェクトを提供する型。 既定では、 [std::equal_to\<K >](../standard-library/equal-to-struct.md)

### <a name="remarks"></a>Remarks

UnorderedMapView の C++ の具象実装、 [Windows::Foundation::Collections::IMapView\<K, V >](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_)アプリケーション バイナリ インターフェイス (ABI) を越えて渡されるインターフェイス。 詳細については、「 [Collections (C++/CX) (コレクション (C++/CX))](../cppcx/collections-c-cx.md)」を参照してください。

### <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[UnorderedMapView::UnorderedMapView](#ctor)|UnorderedMapView クラスの新しいインスタンスを初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[UnorderedMapView::First](#first)|マップ ビュー内の最初の要素に初期化される反復子を返します。|
|[UnorderedMapView::HasKey](#haskey)|指定したキーが現在の UnorderedMapView に格納されているかどうかを判定します。|
|[UnorderedMapView::Lookup](#lookup)|現在の UnorderedMapView オブジェクト内の指定されたキーの位置の要素を取得します。|
|[UnorderedMapView::Size](#size)|現在の UnorderedMapView オブジェクトの要素数を返します。|
|[UnorderedMapView::Split](#split)|元の UnorderedMapView オブジェクトを 2 つの UnorderedMapView オブジェクトに分割します。|

## <a name="inheritance-hierarchy"></a>継承階層

`UnorderedMapView`

### <a name="requirements"></a>必要条件

**ヘッダー:** collection.h

**名前空間:** Platform::Collections

## <a name="first"></a>  UnorderedMapView::First メソッド

最初に指定する反復子を返します[Windows::Foundation::Collections::IKeyValuePair\<K, V >](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_)順序なしのマップ内の要素。

### <a name="syntax"></a>構文

```cpp
virtual Windows::Foundation::Collections::IIterator<
    Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
    First();
```

### <a name="return-value"></a>戻り値

マップ ビュー内の最初の要素を指定する反復子。

### <a name="remarks"></a>Remarks

First() によって返される反復子を保持する便利な方法で宣言された変数に戻り値を割り当てるには、**自動**推論キーワードを入力します。 たとえば、`auto x = myMapView->First();` のようにします。

## <a name="haskey"></a>  UnorderedMapView::HasKey メソッド

指定したキーが現在の UnorderedMap に格納されているかどうかを判定します。

### <a name="syntax"></a>構文

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>パラメーター

*key*<br/>
要素の検索に使用するキー。 型`key`typename が*K*します。

### <a name="return-value"></a>戻り値

**true**キーが見つかった。 それ以外の場合**false**します。

## <a name="lookup"></a>  UnorderedMapView::Lookup メソッド

型 K の指定されたキーに関連付けられている型 V の値を取得します。

### <a name="syntax"></a>構文

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>パラメーター

*key*<br/>
UnorderedMapView の要素の検索に使用するキー。 型`key`typename が*K*します。

### <a name="return-value"></a>戻り値

`key` とペアになる値。 戻り値の型は typename *V* します。

## <a name="size"></a>  UnorderedMapView::Size メソッド

数を返します[Windows::Foundation::Collections::IKeyValuePair\<K, V >](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) UnorderedMapView 内の要素。

### <a name="syntax"></a>構文

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>戻り値

Unordered MapView の要素数。

## <a name="split"></a>  UnorderedMapView::Split メソッド

現在の UnorderedMapView オブジェクトを 2 つの UnorderedMapView オブジェクトに分割します。 このメソッドは操作不可です。

### <a name="syntax"></a>構文

```cpp
void Split(
   Windows::Foundation::Collections::IMapView<
                         K,V>^ * firstPartition,
   Windows::Foundation::Collections::IMapView<
                         K,V>^ * secondPartition);
```

### <a name="parameters"></a>パラメーター

*firstPartition*<br/>
元の UnorderedMapView オブジェクトの最初の部分。

*secondPartition*<br/>
元の UnorderedMapView オブジェクトの 2 つ目の部分。

### <a name="remarks"></a>Remarks

このメソッドは操作可能ではありません。これは何も実行しません。

## <a name="ctor"></a>  UnorderedMapView::UnorderedMapView コンストラクター

UnorderedMapView クラスの新しいインスタンスを初期化します。

### <a name="syntax"></a>構文

```cpp
UnorderedMapView();
explicit UnorderedMapView(size_t n);
UnorderedMapView(size_t n, const H& h);
UnorderedMapView(size_t n, const H& h, const P& p);

explicit UnorderedMapView(
    const std::unordered_map<K, V, H, P>& m);
explicit UnorderedMapView(
    std::unordered_map<K, V, H, P>&& m);

template <typename InIt> UnorderedMapView(InIt first, InIt last );
template <typename InIt> UnorderedMapView(InIt first, InIt last, size_t n );

template <typename InIt> UnorderedMapView(
    InIt first,
    InIt last,
    size_t n,
    const H& h );

template <typename InIt> UnorderedMapView(
    InIt first,
    InIt last,
    size_t n,
    const H& h,
    const P& p );

UnorderedMapView(std::initializer_list<std::pair<const K, V>);

UnorderedMapView(std::initializer_list< std::pair<const K, V>> il, size_t n

UnorderedMapView(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h);

UnorderedMapView(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h,
    const P& p );
```

### <a name="parameters"></a>パラメーター

*n*<br/>
領域を事前に割り当てる要素の数。

*InIt*<br/>
UnorderedMapView の型名。

*H*<br/>
キーのハッシュ値にできる関数オブジェクト。 既定値は[std::hash\<K >](../standard-library/hash-class.md)の種類を`std::hash`をサポートしています。

*P*<br/>
2 つのキーを比較して等価性を確認できる関数オブジェクトを提供する型。 既定値は[std::equal_to\<K >](../standard-library/equal-to-struct.md)します。

*m*<br/>
参照または[Lvalues と Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)を[std::unordered_map](../standard-library/unordered-map-class.md) UnorderedMapView を初期化するために使用されます。

*first*<br/>
UnorderedMapView を初期化するために使用される要素の範囲内の最初の要素の入力反復子。

*last*<br/>
UnorderedMapView を初期化するために使用される要素の範囲の後の最初の要素の入力反復子。

## <a name="see-also"></a>関連項目

[Platform::Collections 名前空間](../cppcx/platform-collections-namespace.md)<br/>
[Windows::Foundation::IMapView](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_)
