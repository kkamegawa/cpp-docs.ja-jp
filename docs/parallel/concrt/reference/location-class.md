---
title: location クラス
ms.date: 11/04/2016
f1_keywords:
- location
- CONCRT/concurrency::location
- CONCRT/concurrency::location::location
- CONCRT/concurrency::location::current
- CONCRT/concurrency::location::from_numa_node
helpviewer_keywords:
- location class
ms.assetid: c3289f51-5bf1-4dff-a18d-d0dab8e5d9c7
ms.openlocfilehash: 7f45ff6d3092bd7c27e81adddca72c9411f752d1
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139824"
---
# <a name="location-class"></a>location クラス

ハードウェアの物理位置の抽象化です。

## <a name="syntax"></a>構文

```cpp
class location;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[location](#ctor)|オーバーロードされます。 `location` オブジェクトを構築します。|
|[~ location デストラクター](#dtor)|`location` オブジェクトを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[現在の](#current)|呼び出し元のスレッドが実行している最も具体的な場所を表す `location` オブジェクトを返します。|
|[from_numa_node](#from_numa_node)|指定された NUMA ノードを表す `location` オブジェクトを返します。|

### <a name="public-operators"></a>パブリック演算子

|Name|説明|
|----------|-----------------|
|[operator!=](#operator_neq)|2つの `location` オブジェクトが異なる場所を表しているかどうかを判断します。|
|[operator=](#operator_eq)|別の `location` オブジェクトの内容をこのオブジェクトに割り当てます。|
|[operator==](#operator_eq_eq)|2つの `location` オブジェクトが同じ場所を表しているかどうかを判断します。|

## <a name="inheritance-hierarchy"></a>継承階層

`location`

## <a name="requirements"></a>要件

**ヘッダー:** concrt .h

**名前空間:** concurrency

## <a name="dtor"></a>~ location

`location` オブジェクトを破棄します。

```cpp
~location();
```

## <a name="current"></a>現在の

呼び出し元のスレッドが実行している最も具体的な場所を表す `location` オブジェクトを返します。

```cpp
static location __cdecl current();
```

### <a name="return-value"></a>戻り値

呼び出し元のスレッドが実行している最も具体的な場所を表す場所。

## <a name="from_numa_node"></a>from_numa_node

指定された NUMA ノードを表す `location` オブジェクトを返します。

```cpp
static location __cdecl from_numa_node(unsigned short _NumaNodeNumber);
```

### <a name="parameters"></a>パラメーター

*_NumaNodeNumber*<br/>
位置を構築する NUMA ノード番号。

### <a name="return-value"></a>戻り値

`_NumaNodeNumber` パラメーターによって指定された NUMA ノードを表す場所。

## <a name="ctor"></a>設置

`location` オブジェクトを構築します。

```cpp
location();

location(
    const location& _Src);

location(
    T _LocationType,
    unsigned int _Id,
    unsigned int _BindingId = 0,
    _Inout_opt_ void* _PBinding = NULL);
```

### <a name="parameters"></a>パラメーター

*_Src*<br/>

*_LocationType*<br/>

*_Id*<br/>

*_BindingId*<br/>

*_PBinding*<br/>
Optionalポインターをバインドしています。

### <a name="remarks"></a>コメント

構築された既定の場所は、システム全体を表します。

## <a name="operator_neq"></a>operator! =

2つの `location` オブジェクトが異なる場所を表しているかどうかを判断します。

```cpp
bool operator!= (const location& _Rhs) const;
```

### <a name="parameters"></a>パラメーター

*_Rhs*<br/>
オペランド `location`。

### <a name="return-value"></a>戻り値

2つの場所が異なる場合は**true** 、それ以外の場合は**false** 。

## <a name="operator_eq"></a>operator =

別の `location` オブジェクトの内容をこのオブジェクトに割り当てます。

```cpp
location& operator= (const location& _Rhs);
```

### <a name="parameters"></a>パラメーター

*_Rhs*<br/>
ソース `location` オブジェクト。

### <a name="return-value"></a>戻り値

## <a name="operator_eq_eq"></a>operator = =

2つの `location` オブジェクトが同じ場所を表しているかどうかを判断します。

```cpp
bool operator== (const location& _Rhs) const;
```

### <a name="parameters"></a>パラメーター

*_Rhs*<br/>
オペランド `location`。

### <a name="return-value"></a>戻り値

2つの場所が同一の場合は**true** 、それ以外の場合は**false** 。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
