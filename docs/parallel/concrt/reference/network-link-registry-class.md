---
title: network_link_registry クラス
ms.date: 11/04/2016
f1_keywords:
- network_link_registry
- AGENTS/concurrency::network_link_registry
- AGENTS/concurrency::network_link_registry::add
- AGENTS/concurrency::network_link_registry::begin
- AGENTS/concurrency::network_link_registry::contains
- AGENTS/concurrency::network_link_registry::count
- AGENTS/concurrency::network_link_registry::remove
helpviewer_keywords:
- network_link_registry class
ms.assetid: 3e7b4097-09f1-4252-964e-b15b8f7f7fc6
ms.openlocfilehash: 430190c11ec06a4f26eb9d8c4237552848420ad7
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138886"
---
# <a name="network_link_registry-class"></a>network_link_registry クラス

`network_link_registry` 抽象基底クラスによって、ソース ブロックとターゲット ブロック間のリンクを管理します。

## <a name="syntax"></a>構文

```cpp
template<class _Block>
class network_link_registry;
```

### <a name="parameters"></a>パラメーター

*_Block*<br/>
`network_link_registry`に格納されているブロックデータ型。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|Name|説明|
|----------|-----------------|
|`const_pointer`|`network_link_registry` オブジェクト内の `const` 要素へのポインターを提供する型。|
|`const_reference`|読み取りと const 操作の実行のために `network_link_registry` オブジェクトに格納されている `const` 要素への参照を提供する型。|
|`iterator`|`network_link_registry` オブジェクト内の任意の要素の読み取りまたは変更ができる反復子を提供する型。|
|`type`|`network_link_registry` オブジェクトに格納されているブロック型を表す型。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[add](#add)|派生クラスでオーバーライドされた場合、`network_link_registry` オブジェクトへのリンクを追加します。|
|[begin](#begin)|派生クラスでオーバーライドされた場合、`network_link_registry` オブジェクト内の最初の要素を指す反復子を返します。|
|[contains](#contains)|派生クラスでオーバーライドされると、指定したブロックの `network_link_registry` オブジェクトを検索します。|
|[count](#count)|派生クラスでオーバーライドされると、`network_link_registry` オブジェクト内の項目の数を返します。|
|[remove](#remove)|派生クラスでオーバーライドされると、指定したブロックを `network_link_registry` オブジェクトから削除します。|

## <a name="remarks"></a>解説

`network link registry` は、同時アクセスには安全ではありません。

## <a name="inheritance-hierarchy"></a>継承階層

`network_link_registry`

## <a name="requirements"></a>［要件］

**ヘッダー:** agents.h

**名前空間:** concurrency

## <a name="add"></a>アドイン

派生クラスでオーバーライドされた場合、`network_link_registry` オブジェクトへのリンクを追加します。

```cpp
virtual void add(_EType _Link) = 0;
```

### <a name="parameters"></a>パラメーター

*_Link*<br/>
追加するブロックへのポインター。

## <a name="begin"></a>初め

派生クラスでオーバーライドされた場合、`network_link_registry` オブジェクト内の最初の要素を指す反復子を返します。

```cpp
virtual iterator begin() = 0;
```

### <a name="return-value"></a>戻り値

`network_link_registry` オブジェクト内の最初の要素を指す反復子。

### <a name="remarks"></a>解説

反復子の終了状態は、`NULL` リンクによって示されます。

## <a name="contains"></a>は

派生クラスでオーバーライドされると、指定したブロックの `network_link_registry` オブジェクトを検索します。

```cpp
virtual bool contains(_EType _Link) = 0;
```

### <a name="parameters"></a>パラメーター

*_Link*<br/>
`network_link_registry` オブジェクト内で検索されているブロックへのポインター。

### <a name="return-value"></a>戻り値

ブロックが見つかった場合は**true** 、それ以外の場合は**false** 。

## <a name="count"></a>数

派生クラスでオーバーライドされると、`network_link_registry` オブジェクト内の項目の数を返します。

```cpp
virtual size_t count() = 0;
```

### <a name="return-value"></a>戻り値

`network_link_registry` オブジェクト内の項目の数。

## <a name="remove"></a>から

派生クラスでオーバーライドされると、指定したブロックを `network_link_registry` オブジェクトから削除します。

```cpp
virtual bool remove(_EType _Link) = 0;
```

### <a name="parameters"></a>パラメーター

*_Link*<br/>
削除するブロックへのポインター (見つかった場合)。

### <a name="return-value"></a>戻り値

リンクが見つかり、削除された場合は**true** 、それ以外の場合は**false** 。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[single_link_registry クラス](single-link-registry-class.md)<br/>
[multi_link_registry クラス](multi-link-registry-class.md)
