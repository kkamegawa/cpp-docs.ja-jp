---
title: Platform::Collections::MapView クラス
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::MapView::MapView
- COLLECTION/Platform::Collections::MapView::First
- COLLECTION/Platform::Collections::MapView::HasKey
- COLLECTION/Platform::Collections::MapView::Lookup
- COLLECTION/Platform::Collections::MapView::Size
- COLLECTION/Platform::Collections::MapView::Split
helpviewer_keywords:
- MapView Class
ms.assetid: 9577dde7-f599-43c6-b1e4-7d653706fd62
ms.openlocfilehash: 1e38865f1d43edac4fc895052f1ea1b5a54a34ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161713"
---
# <a name="platformcollectionsmapview-class"></a>Platform::Collections::MapView クラス

キーと値のペアのコレクションである、 *マップ*への読み取り専用ビューを表します。

## <a name="syntax"></a>構文

```
template <
   typename K,
   typename V,
   typename C = ::std::less<K>>
ref class MapView sealed;
```

#### <a name="parameters"></a>パラメーター

*K*<br/>
キー/値ペア内のキーの型。

*V*<br/>
キー/値ペア内の値の型。

*C*<br/>
並べ替えキーとして 2 つの要素値を比較して MapView 内の相対順序を決定できる関数オブジェクトを提供する型。 既定では、 [std::less\<K >](../standard-library/less-struct.md)します。

### <a name="remarks"></a>Remarks

MapView の C++ の具象実装、 [Windows::Foundation::Collections::IMapView \<K, V >](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_)アプリケーション バイナリ インターフェイス (ABI) を越えて渡されるインターフェイス。 詳細については、「 [Collections (C++/CX) (コレクション (C++/CX))](../cppcx/collections-c-cx.md)」を参照してください。

### <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[MapView::MapView](#ctor)|MapView クラスの新しいインスタンスを初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[MapView::First](#first)|マップ ビュー内の最初の要素に初期化される反復子を返します。|
|[MapView::HasKey](#haskey)|現在の MapView に、指定されたキーが含まれているかどうかを判定します。|
|[MapView::Lookup](#lookup)|現在の MapView オブジェクト内の、指定されたキーの位置の要素を取得します。|
|[MapView::Size](#size)|現在の MapView オブジェクトの要素数を返します。|
|[MapView::Split](#split)|元の MapView オブジェクトを、2 つの MapView オブジェクトに分割します。|

## <a name="inheritance-hierarchy"></a>継承階層

`MapView`

### <a name="requirements"></a>必要条件

**ヘッダー:** collection.h

**名前空間:** Platform::Collections

## <a name="first"></a> Mapview::first メソッド

マップ ビュー内の最初の要素を指定する反復子を返します。

### <a name="syntax"></a>構文

```
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>戻り値

マップ ビュー内の最初の要素を指定する反復子。

### <a name="remarks"></a>Remarks

First() によって返される反復子を保持する便利な方法で宣言された変数に戻り値を割り当てるには、**自動**推論キーワードを入力します。 たとえば、`auto x = myMapView->First();` のようにします。

## <a name="haskey"></a>  Mapview::haskey メソッド

現在の MapView に、指定されたキーが含まれているかどうかを判定します。

### <a name="syntax"></a>構文

```

bool HasKey(K key);
```

### <a name="parameters"></a>パラメーター

*key*<br/>
MapView 要素の検索に使用するキー。 型*キー* typename が*K*します。

### <a name="return-value"></a>戻り値

**true**キーが見つかった。 それ以外の場合**false**します。

##  <a name="lookup"></a> Mapview::lookup メソッド

型 K の指定されたキーに関連付けられている型 V の値を取得します。

### <a name="syntax"></a>構文

```
V Lookup(K key);
```

### <a name="parameters"></a>パラメーター

*key*<br/>
MapView の要素の検索に使用するキー。 型`key`typename が*K*します。

### <a name="return-value"></a>戻り値

`key` とペアになる値。 戻り値の型は typename *V* します。

##  <a name="ctor"></a> Mapview::mapview コンス トラクター

MapView クラスの新しいインスタンスを初期化します。

### <a name="syntax"></a>構文

```cpp
explicit MapView(const C& comp = C());

explicit MapView(const ::std::map<K, V, C>& m);

explicit MapView(std::map<K, V, C>&& m);

template <typename InIt> MapView(
    InIt first,
    InIt last,
    const C& comp = C());

MapView(
    ::std::initializer_list<std::pair<const K, V>> il,
    const C& comp = C());
```

### <a name="parameters"></a>パラメーター

*InIt*<br/>
現在の MapView の型名。

*comp*<br/>
並べ替えキーとして 2 つの要素値を比較して MapView 内の相対順序を決定できる関数オブジェクト。

*m*<br/>
参照または[Lvalues と Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)を`map Class`現在の MapView を初期化するために使用されます。

*first*<br/>
現在の MapView を初期化するために使用される要素の範囲内の最初の要素の入力反復子。

*last*<br/>
現在の MapView を初期化するために使用される要素の範囲の後の最初の要素の入力反復子。

*il*<br/>
A [std::initializer_list < std::pair\<K, V >>](../standard-library/initializer-list-class.md)要素が MapView に挿入されます。

##  <a name="size"></a> Mapview::size メソッド

現在の MapView オブジェクトの要素数を返します。

### <a name="syntax"></a>構文

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>戻り値

現在の MapView 内の要素数。

##  <a name="split"></a> Mapview::split メソッド

現在の MapView を 2 つの MapView オブジェクトに分割します。 このメソッドは操作不可です。

### <a name="syntax"></a>構文

```
void Split(
   Windows::Foundation::Collections::IMapView<
                         K, V>^ * firstPartition,
   Windows::Foundation::Collections::IMapView<
                         K, V>^ * secondPartition);
```

### <a name="parameters"></a>パラメーター

*firstPartition*<br/>
元の MapView オブジェクトの最初の部分。

*secondPartition*<br/>
元の MapView オブジェクトの 2 番目の部分。

### <a name="remarks"></a>Remarks

このメソッドは操作可能ではありません。これは何も実行しません。

## <a name="see-also"></a>関連項目

[プラットフォーム Namespace](platform-namespace-c-cx.md)
