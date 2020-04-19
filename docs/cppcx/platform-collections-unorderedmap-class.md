---
title: Platform::Collections::UnorderedMap クラス
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
ms.openlocfilehash: 7790b363ef3f30b0ad0602568190ab443a2c1401
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161733"
---
# <a name="platformcollectionsunorderedmap-class"></a>Platform::Collections::UnorderedMap クラス

キー/値ペアのコレクションである順序なしの *マップ*を表します。

## <a name="syntax"></a>構文

```cpp
template <
   typename K,
   typename V,
   typename C = std::equal_to<K>
>
ref class Map sealed;
```

#### <a name="parameters"></a>パラメーター

*K*<br/>
キー/値ペア内のキーの型。

*V*<br/>
キー/値ペア内の値の型。

*C*<br/>
並べ替えキーとして 2 つの要素値を比較してマップ内の相対順序を決定できる関数オブジェクトを提供する型。 既定では、 [std::equal_to\<K >](../standard-library/equal-to-struct.md)します。

### <a name="remarks"></a>Remarks

使用できる型は次のとおりです。

- 整数

- インターフェイス クラス ^

- パブリック ref クラス ^

- value struct

- パブリック列挙型クラス

**UnorderedMap**のラッパーでは基本的に[std::unordered_map](../standard-library/unordered-map-class.md) Windows ランタイム型の格納をサポートします。 具象実装、 [Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_)と[IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) Windows ランタイム インターフェイスのパブリックの間で渡される型。 パブリックの戻り値またはパラメーターで `Platform::Collections::UnorderedMap` 型を使用しようとすると、コンパイラ エラー C3986 が発生します。 エラーを修正するには、パラメーターや戻り値の型を [Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_)に変更します。

詳細については、次を参照してください。[コレクション](../cppcx/collections-c-cx.md)します。

### <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[UnorderedMap::UnorderedMap](#ctor)|マップ クラスの新しいインスタンスを初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[UnorderedMap::Clear](#clear)|現在のマップ オブジェクトから、すべてのキー/値ペアを削除します。|
|[UnorderedMap::First](#first)|マップ内の最初の要素を指定する反復子を返します。|
|[UnorderedMap::GetView](#getview)|現在のマップの読み取り専用ビューである Platform::Collections::UnorderedMapView クラスを返します。|
|[UnorderedMap::HasKey](#haskey)|指定したキーが現在のマップに格納されているかどうかを判定します。|
|[UnorderedMap::Insert](#insert)|指定したキー/値ペアを現在のマップ オブジェクトに追加します。|
|[UnorderedMap::Lookup](#lookup)|現在のマップ オブジェクト内の指定されたキーの位置の要素を取得します。|
|[UnorderedMap::Remove](#remove)|指定したキー/値ペアを現在のマップ オブジェクトから削除します。|
|[UnorderedMap::Size](#size)|現在のマップ オブジェクト内の要素数を返します。|

### <a name="events"></a>イベント

|||
|-|-|
|名前|説明|
|[Map::mapchanged](#mapchanged)イベント|マップが変更されたときに発生します。|

## <a name="inheritance-hierarchy"></a>継承階層

`UnorderedMap`

### <a name="requirements"></a>必要条件

**ヘッダー:** collection.h

**名前空間:** Platform::Collections

## <a name="clear"></a>  Unorderedmap::clear メソッド

現在の UnorderedMap オブジェクトから、すべてのキー/値ペアを削除します。

### <a name="syntax"></a>構文

```cpp
virtual void Clear();
```

## <a name="first"></a>  Unorderedmap::first メソッド

最初に指定する反復子を返します[Windows::Foundation::Collections::IKeyValuePair\<K, V >](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_)順序なしのマップ内の要素。

### <a name="syntax"></a>構文

```cpp
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
   First();
```

### <a name="return-value"></a>戻り値

マップ内の最初の要素を指定する反復子。

### <a name="remarks"></a>Remarks

First() によって返される反復子を保持する便利な方法で宣言された変数に戻り値を割り当てるには、**自動**推論キーワードを入力します。 たとえば、`auto x = myUnorderedMap->First();` のようにします。

## <a name="getview"></a>  Unorderedmap::getview メソッド

現在の UnorderedMap の読み取り専用ビューを返しますつまり、 [Platform::Collections::UnorderedMapView クラス](../cppcx/platform-collections-unorderedmapview-class.md)[Windows::Foundation::Collections::IMapView::IMapView]/uwp/api/Windows.Foundation.Collections.IMapView_K_V_) インターフェイスを実装します。

### <a name="syntax"></a>構文

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>戻り値

`UnorderedMapView` オブジェクト。

## <a name="haskey"></a>  Unorderedmap::haskey メソッド

指定したキーが現在の UnorderedMap に格納されているかどうかを判定します。

### <a name="syntax"></a>構文

```cpp
bool HasKey(
   K key
);
```

### <a name="parameters"></a>パラメーター

*key*<br/>
UnorderedMap 要素の検索に使用するキー。 型*キー* typename が*K*します。

### <a name="return-value"></a>戻り値

**true**キーが見つかった。 それ以外の場合**false**します。

## <a name="insert"></a>  UnorderedMap::Insert Method

指定したキー/値ペアを現在の UnorderedMap オブジェクトに追加します。

### <a name="syntax"></a>構文

```cpp
virtual bool Insert(
   K key,
   V value
);
```

### <a name="parameters"></a>パラメーター

*key*<br/>
キー/値ペアのキー部分。 型*キー* typename が*K*します。

*value*<br/>
キー/値ペアの値部分。 型*値*typename が*V*します。

### <a name="return-value"></a>戻り値

**true**現在のマップ内の既存の要素のキーと一致するかどうか*キー*し、その要素の値の部分に設定されている*値*します。 **false**現在のマップ内の既存の要素が一致しない場合*キー*と*キー*と*値*パラメーターはキー/値ペアに加えに追加し、現在の UnorderedMap します。

## <a name="lookup"></a>  Unorderedmap::lookup メソッド

型 K の指定されたキーに関連付けられている型 V の値を取得します。

### <a name="syntax"></a>構文

```cpp
V Lookup(
   K key
);
```

### <a name="parameters"></a>パラメーター

*key*<br/>
UnorderedMap の要素の検索に使用するキー。 型*キー* typename が*K*します。

### <a name="return-value"></a>戻り値

値とペアになっている、*キー*します。 戻り値の型は typename *V* します。

## <a name="mapchanged"></a>  UnorderedMap::MapChanged

項目がマップに挿入されたときまたはマップから削除されたときに発生します。

### <a name="syntax"></a>構文

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>プロパティ値/戻り値

A [MapChangedEventHandler\<K, V >](/uwp/api/windows.foundation.collections.mapchangedeventhandler)発生した変更の種類と、イベントを発生させたオブジェクトに関する情報を格納します。 参照してください[IMapChangedEventArgs\<K >](/uwp/api/Windows.Foundation.Collections.IMapChangedEventArgs_K_)と[CollectionChange 列挙](/uwp/api/windows.foundation.collections.collectionchange)します。

## <a name="net-framework-equivalent"></a>同等の .NET Framework 関数

Windows ランタイム アプリの c# または Visual Basic プロジェクトの IMap\<K, V > として IDictionary\<K, V >。

## <a name="remove"></a>  Unorderedmap::remove メソッド

指定したキー/値ペアを UnorderedMap オブジェクトから削除します。

### <a name="syntax"></a>構文

```cpp
virtual void Remove(
   K key);
```

### <a name="parameters"></a>パラメーター

*key*<br/>
キー/値ペアのキー部分。 型*キー* typename が*K*します。

## <a name="size"></a>  Unorderedmap::size メソッド

数を返します[Windows::Foundation::Collections::IKeyValuePair\<K, V >](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) UnorderedMap の要素。

### <a name="syntax"></a>構文

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>戻り値

順序なしのマップの要素数。

## <a name="ctor"></a>  UnorderedMap::UnorderedMap コンストラクター

UnorderedMap クラスの新しいインスタンスを初期化します。

### <a name="syntax"></a>構文

```cpp
UnorderedMap();

explicit UnorderedMap(
    size_t n
    );

UnorderedMap(
    size_t n,
    const H& h
    );

UnorderedMap(
    size_t n,
    const H& h,
    const P& p
    );

explicit UnorderedMap(
    const std::unordered_map<K, V, H, P>& m
    );

explicit UnorderedMap(
    std::unordered_map<K, V, H, P>&& m
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n,
    const H& h
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n,
    const H& h,
    const P& p
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h,
    const P& p
    );
```

### <a name="parameters"></a>パラメーター

*InIt*<br/>
現在の UnorderedMap の型名。

*P*<br/>
2 つのキーを比較してそれらが等しいかどうかを判定できる関数オブジェクト。 このパラメーターの既定値[std::equal_to\<K >](../standard-library/equal-to-struct.md)します。

*H*<br/>
キーのハッシュ値を生成する関数オブジェクト。 このパラメーターの既定値[クラス 1 にハッシュ](../standard-library/hash-class.md)するキーの型のクラスをサポートします。

*m*<br/>
参照または[Lvalues と Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)を[std::unordered_map](../standard-library/unordered-map-class.md)現在の UnorderedMap を初期化するために使用されます。

*il*<br/>
A [std::initializer_list](../standard-library/initializer-list-class.md)の[std::pair](../standard-library/pair-structure.md)マップを初期化するために使用されるオブジェクト。

*first*<br/>
現在の UnorderedMap を初期化するために使用される要素の範囲内の最初の要素の入力反復子。

*last*<br/>
現在の UnorderedMap を初期化するために使用される要素の範囲の後の最初の要素の入力反復子。

## <a name="see-also"></a>関連項目

[プラットフォーム Namespace](platform-namespace-c-cx.md)<br/>
[Platform::Collections 名前空間](../cppcx/platform-collections-namespace.md)<br/>
[Platform::Collections::Map クラス](../cppcx/platform-collections-map-class.md)<br/>
[Platform::Collections::UnorderedMapView クラス](../cppcx/platform-collections-unorderedmapview-class.md)<br/>
[コレクション](../cppcx/collections-c-cx.md)<br/>
[C++ で Windows ランタイム コンポーネントを作成する](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
