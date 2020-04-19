---
title: source_link_manager クラス
ms.date: 11/04/2016
f1_keywords:
- source_link_manager
- AGENTS/concurrency::source_link_manager
- AGENTS/concurrency::source_link_manager::source_link_manager
- AGENTS/concurrency::source_link_manager::add
- AGENTS/concurrency::source_link_manager::begin
- AGENTS/concurrency::source_link_manager::contains
- AGENTS/concurrency::source_link_manager::count
- AGENTS/concurrency::source_link_manager::reference
- AGENTS/concurrency::source_link_manager::register_target_block
- AGENTS/concurrency::source_link_manager::release
- AGENTS/concurrency::source_link_manager::remove
- AGENTS/concurrency::source_link_manager::set_bound
helpviewer_keywords:
- source_link_manager class
ms.assetid: 287487cf-e0fe-4c35-aa3c-24f081d1ddae
ms.openlocfilehash: 35c7cc72520cdb0675abf9c15574a49e33741d0b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142694"
---
# <a name="source_link_manager-class"></a>source_link_manager クラス

`source_link_manager` オブジェクトは、`ISource` ブロックへのメッセージング ブロック ネットワーク リンクを管理します。

## <a name="syntax"></a>構文

```cpp
template<class _LinkRegistry>
class source_link_manager;
```

### <a name="parameters"></a>パラメーター

*_LinkRegistry*<br/>
ネットワークリンクレジストリ。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|Name|説明|
|----------|-----------------|
|`const_pointer`|`source_link_manager` オブジェクト内の `const` 要素へのポインターを提供する型。|
|`const_reference`|読み取りと const 操作の実行のために `source_link_manager` オブジェクトに格納されている `const` 要素への参照を提供する型。|
|`iterator`|`source_link_manager` オブジェクト内の任意の要素の読み取りまたは変更ができる反復子を提供する型。|
|`type`|`source_link_manager` オブジェクトによって管理されているリンクレジストリの種類。|

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[source_link_manager](#ctor)|`source_link_manager` オブジェクトを構築します。|
|[~ source_link_manager デストラクター](#dtor)|`source_link_manager` オブジェクトを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[add](#add)|`source_link_manager` オブジェクトにソースリンクを追加します。|
|[begin](#begin)|`source_link_manager` オブジェクト内の最初の要素を指す反復子を返します。|
|[contains](#contains)|この `source_link_manager` オブジェクト内の `network_link_registry` 内で、指定したブロックを検索します。|
|[count](#count)|`source_link_manager` オブジェクト内のリンクされたブロックの数をカウントします。|
|[reference](#reference)|`source_link_manager` オブジェクトの参照を取得します。|
|[register_target_block](#register_target_block)|この `source_link_manager` オブジェクトを保持するターゲットブロックを登録します。|
|[release](#release)|`source_link_manager` オブジェクトの参照を解放します。|
|[remove](#remove)|`source_link_manager` オブジェクトからリンクを削除します。|
|[set_bound](#set_bound)|この `source_link_manager` オブジェクトに追加できるソースリンクの最大数を設定します。|

## <a name="remarks"></a>解説

現在、ソースブロックは参照カウントされています。 これは、リンクへの同時アクセスを可能にし、コールバックを介してリンクを参照する機能を提供する、`network_link_registry` オブジェクトのラッパーです。 メッセージブロック (`target_block`s または `propagator_block`s) では、ソースリンクにこのクラスを使用する必要があります。

## <a name="inheritance-hierarchy"></a>継承階層

`source_link_manager`

## <a name="requirements"></a>［要件］

**ヘッダー:** agents.h

**名前空間:** concurrency

## <a name="add"></a>アドイン

`source_link_manager` オブジェクトにソースリンクを追加します。

```cpp
void add(_EType _Link);
```

### <a name="parameters"></a>パラメーター

*_Link*<br/>
追加するブロックへのポインター。

## <a name="begin"></a>初め

`source_link_manager` オブジェクト内の最初の要素を指す反復子を返します。

```cpp
iterator begin();
```

### <a name="return-value"></a>戻り値

`source_link_manager` オブジェクト内の最初の要素を指す反復子。

### <a name="remarks"></a>解説

反復子の終了状態は、`NULL` リンクによって示されます。

## <a name="contains"></a>は

この `source_link_manager` オブジェクト内の `network_link_registry` 内で、指定したブロックを検索します。

```cpp
bool contains(_EType _Link);
```

### <a name="parameters"></a>パラメーター

*_Link*<br/>
`source_link_manager` オブジェクト内で検索されるブロックへのポインター。

### <a name="return-value"></a>戻り値

指定されたブロックが見つかった場合は**true** 、それ以外の場合は**false** 。

## <a name="count"></a>数

`source_link_manager` オブジェクト内のリンクされたブロックの数をカウントします。

```cpp
size_t count();
```

### <a name="return-value"></a>戻り値

`source_link_manager` オブジェクト内のリンクされたブロックの数。

## <a name="reference"></a>「

`source_link_manager` オブジェクトの参照を取得します。

```cpp
void reference();
```

## <a name="register_target_block"></a>register_target_block

この `source_link_manager` オブジェクトを保持するターゲットブロックを登録します。

```cpp
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
この `source_link_manager` オブジェクトを保持しているターゲットブロック。

## <a name="release"></a>解除

`source_link_manager` オブジェクトの参照を解放します。

```cpp
void release();
```

## <a name="remove"></a>から

`source_link_manager` オブジェクトからリンクを削除します。

```cpp
bool remove(_EType _Link);
```

### <a name="parameters"></a>パラメーター

*_Link*<br/>
削除するブロックへのポインター (見つかった場合)。

### <a name="return-value"></a>戻り値

リンクが見つかり、削除された場合は**true** 、それ以外の場合は**false** 。

## <a name="set_bound"></a>set_bound

この `source_link_manager` オブジェクトに追加できるソースリンクの最大数を設定します。

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>パラメーター

*_MaxLinks*<br/>
リンクの最大数。

## <a name="ctor"></a>source_link_manager

`source_link_manager` オブジェクトを構築します。

```cpp
source_link_manager();
```

## <a name="dtor"></a>~ source_link_manager

`source_link_manager` オブジェクトを破棄します。

```cpp
~source_link_manager();
```

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[single_link_registry クラス](single-link-registry-class.md)<br/>
[multi_link_registry クラス](multi-link-registry-class.md)
