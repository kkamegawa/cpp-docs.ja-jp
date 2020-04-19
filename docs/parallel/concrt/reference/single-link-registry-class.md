---
title: single_link_registry クラス
ms.date: 11/04/2016
f1_keywords:
- single_link_registry
- AGENTS/concurrency::single_link_registry
- AGENTS/concurrency::single_link_registry::single_link_registry
- AGENTS/concurrency::single_link_registry::add
- AGENTS/concurrency::single_link_registry::begin
- AGENTS/concurrency::single_link_registry::contains
- AGENTS/concurrency::single_link_registry::count
- AGENTS/concurrency::single_link_registry::remove
helpviewer_keywords:
- single_link_registry class
ms.assetid: 09540a4e-c34e-4ff9-af49-21b8612b6ab3
ms.openlocfilehash: c29caf6d31df316e80b15fe6827c81e34ece8a18
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142722"
---
# <a name="single_link_registry-class"></a>single_link_registry クラス

`single_link_registry` オブジェクトは、単一のソース ブロックまたはターゲット ブロックのみを管理する `network_link_registry` です。

## <a name="syntax"></a>構文

```cpp
template<class _Block>
class single_link_registry : public network_link_registry<_Block>;
```

### <a name="parameters"></a>パラメーター

*_Block*<br/>
`single_link_registry` オブジェクトに格納されているブロックデータ型。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[single_link_registry](#ctor)|`single_link_registry` オブジェクトを構築します。|
|[~ single_link_registry デストラクター](#dtor)|`single_link_registry` オブジェクトを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[add](#add)|`single_link_registry` オブジェクトへのリンクを追加します。 ( [Network_link_registry:: add](network-link-registry-class.md#add)をオーバーライドします)。|
|[begin](#begin)|`single_link_registry` オブジェクト内の最初の要素を指す反復子を返します。 ( [Network_link_registry:: begin](network-link-registry-class.md#begin)をオーバーライドします)。|
|[contains](#contains)|`single_link_registry` オブジェクトで、指定したブロックを検索します。 ( [Network_link_registry:: contains](network-link-registry-class.md#contains)をオーバーライドします)。|
|[count](#count)|`single_link_registry` オブジェクト内の項目の数をカウントします。 ( [Network_link_registry:: count](network-link-registry-class.md#count)をオーバーライドします)。|
|[remove](#remove)|`single_link_registry` オブジェクトからリンクを削除します。 ( [Network_link_registry:: remove](network-link-registry-class.md#remove)をオーバーライドします)。|

## <a name="inheritance-hierarchy"></a>継承階層

[network_link_registry](network-link-registry-class.md)

`single_link_registry`

## <a name="requirements"></a>［要件］

**ヘッダー:** agents.h

**名前空間:** concurrency

## <a name="add"></a>アドイン

`single_link_registry` オブジェクトへのリンクを追加します。

```cpp
virtual void add(_EType _Link);
```

### <a name="parameters"></a>パラメーター

*_Link*<br/>
追加するブロックへのポインター。

### <a name="remarks"></a>解説

このレジストリにリンクが既に存在する場合、メソッドは[invalid_link_target](invalid-link-target-class.md)例外をスローします。

## <a name="begin"></a>初め

`single_link_registry` オブジェクト内の最初の要素を指す反復子を返します。

```cpp
virtual iterator begin();
```

### <a name="return-value"></a>戻り値

`single_link_registry` オブジェクト内の最初の要素を指す反復子。

### <a name="remarks"></a>解説

終了状態は、`NULL` リンクによって示されます。

## <a name="contains"></a>は

`single_link_registry` オブジェクトで、指定したブロックを検索します。

```cpp
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>パラメーター

*_Link*<br/>
`single_link_registry` オブジェクト内で検索されるブロックへのポインター。

### <a name="return-value"></a>戻り値

リンクが見つかった場合は**true** 、それ以外の場合は**false** 。

## <a name="count"></a>数

`single_link_registry` オブジェクト内の項目の数をカウントします。

```cpp
virtual size_t count();
```

### <a name="return-value"></a>戻り値

`single_link_registry` オブジェクト内の項目の数。

## <a name="remove"></a>から

`single_link_registry` オブジェクトからリンクを削除します。

```cpp
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>パラメーター

*_Link*<br/>
削除するブロックへのポインター (見つかった場合)。

### <a name="return-value"></a>戻り値

リンクが見つかり、削除された場合は**true** 、それ以外の場合は**false** 。

## <a name="ctor"></a>single_link_registry

`single_link_registry` オブジェクトを構築します。

```cpp
single_link_registry();
```

## <a name="dtor"></a>~ single_link_registry

`single_link_registry` オブジェクトを破棄します。

```cpp
virtual ~single_link_registry();
```

### <a name="remarks"></a>解説

このメソッドは、リンクが削除される前に呼び出された場合、 [invalid_operation](invalid-operation-class.md)例外をスローします。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[multi_link_registry クラス](multi-link-registry-class.md)
