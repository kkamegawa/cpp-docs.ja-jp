---
title: multi_link_registry クラス
ms.date: 11/04/2016
f1_keywords:
- multi_link_registry
- AGENTS/concurrency::multi_link_registry
- AGENTS/concurrency::multi_link_registry::multi_link_registry
- AGENTS/concurrency::multi_link_registry::add
- AGENTS/concurrency::multi_link_registry::begin
- AGENTS/concurrency::multi_link_registry::contains
- AGENTS/concurrency::multi_link_registry::count
- AGENTS/concurrency::multi_link_registry::remove
- AGENTS/concurrency::multi_link_registry::set_bound
helpviewer_keywords:
- multi_link_registry class
ms.assetid: b2aa73a8-e8a6-4255-b117-d07530c328b2
ms.openlocfilehash: e22df5ee65d0219a46065044385dca46aac297a3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142368"
---
# <a name="multi_link_registry-class"></a>multi_link_registry クラス

`multi_link_registry` オブジェクトは、複数のソース ブロックまたは複数のターゲット ブロックを管理する `network_link_registry` です。

## <a name="syntax"></a>構文

```cpp
template<class _Block>
class multi_link_registry : public network_link_registry<_Block>;
```

### <a name="parameters"></a>パラメーター

*_Block*<br/>
`multi_link_registry` オブジェクトに格納されているブロックデータ型。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[multi_link_registry](#ctor)|`multi_link_registry` オブジェクトを構築します。|
|[~ multi_link_registry デストラクター](#dtor)|`multi_link_registry` オブジェクトを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[add](#add)|`multi_link_registry` オブジェクトへのリンクを追加します。 ( [Network_link_registry:: add](network-link-registry-class.md#add)をオーバーライドします)。|
|[begin](#begin)|`multi_link_registry` オブジェクト内の最初の要素を指す反復子を返します。 ( [Network_link_registry:: begin](network-link-registry-class.md#begin)をオーバーライドします)。|
|[contains](#contains)|`multi_link_registry` オブジェクトで、指定したブロックを検索します。 ( [Network_link_registry:: contains](network-link-registry-class.md#contains)をオーバーライドします)。|
|[count](#count)|`multi_link_registry` オブジェクト内の項目の数をカウントします。 ( [Network_link_registry:: count](network-link-registry-class.md#count)をオーバーライドします)。|
|[remove](#remove)|`multi_link_registry` オブジェクトからリンクを削除します。 ( [Network_link_registry:: remove](network-link-registry-class.md#remove)をオーバーライドします)。|
|[set_bound](#set_bound)|`multi_link_registry` オブジェクトが保持できるリンクの数の上限を設定します。|

## <a name="inheritance-hierarchy"></a>継承階層

[network_link_registry](network-link-registry-class.md)

`multi_link_registry`

## <a name="requirements"></a>要件

**ヘッダー:** agents.h

**名前空間:** concurrency

## <a name="add"></a>アドイン

`multi_link_registry` オブジェクトへのリンクを追加します。

```cpp
virtual void add(_EType _Link);
```

### <a name="parameters"></a>パラメーター

*_Link*<br/>
追加するブロックへのポインター。

### <a name="remarks"></a>コメント

リンクが既にレジストリに存在する場合、またはバインドされているが既に `set_bound` 関数で設定されていて、リンクが削除されている場合、このメソッドは[invalid_link_target](invalid-link-target-class.md)例外をスローします。

## <a name="begin"></a>初め

`multi_link_registry` オブジェクト内の最初の要素を指す反復子を返します。

```cpp
virtual iterator begin();
```

### <a name="return-value"></a>戻り値

`multi_link_registry` オブジェクト内の最初の要素を指す反復子。

### <a name="remarks"></a>コメント

終了状態は、`NULL` リンクによって示されます。

## <a name="contains"></a>は

`multi_link_registry` オブジェクトで、指定したブロックを検索します。

```cpp
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>パラメーター

*_Link*<br/>
`multi_link_registry` オブジェクト内で検索されるブロックへのポインター。

### <a name="return-value"></a>戻り値

指定されたブロックが見つかった場合は**true** 、それ以外の場合は**false** 。

## <a name="count"></a>数

`multi_link_registry` オブジェクト内の項目の数をカウントします。

```cpp
virtual size_t count();
```

### <a name="return-value"></a>戻り値

`multi_link_registry` オブジェクト内の項目の数。

## <a name="ctor"></a>multi_link_registry

`multi_link_registry` オブジェクトを構築します。

```cpp
multi_link_registry();
```

## <a name="dtor"></a>~ multi_link_registry

`multi_link_registry` オブジェクトを破棄します。

```cpp
virtual ~multi_link_registry();
```

### <a name="remarks"></a>コメント

メソッドは、すべてのリンクが削除される前に呼び出された場合、 [invalid_operation](invalid-operation-class.md)例外をスローします。

## <a name="remove"></a>から

`multi_link_registry` オブジェクトからリンクを削除します。

```cpp
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>パラメーター

*_Link*<br/>
削除するブロックへのポインター (見つかった場合)。

### <a name="return-value"></a>戻り値

リンクが見つかり、削除された場合は**true** 、それ以外の場合は**false** 。

## <a name="set_bound"></a>set_bound

`multi_link_registry` オブジェクトが保持できるリンクの数の上限を設定します。

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>パラメーター

*_MaxLinks*<br/>
`multi_link_registry` オブジェクトが保持できるリンクの最大数。

### <a name="remarks"></a>コメント

バインドされたが設定されると、エントリのリンクを解除すると、`multi_link_registry` オブジェクトは変更できない状態になり、`add` を呼び出すと `invalid_link_target` 例外がスローされます。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[single_link_registry クラス](single-link-registry-class.md)
