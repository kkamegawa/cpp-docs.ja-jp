---
title: scheduler_ptr 構造体
ms.date: 11/04/2016
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
ms.openlocfilehash: fd044a6255a17882c26183223f71564f98c9f7b2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142772"
---
# <a name="scheduler_ptr-structure"></a>scheduler_ptr 構造体

スケジューラへのポインターを表します。 このクラスは、shared_ptr を使用して共有の有効期間を指定できるようにするか、生のポインターを使用して単純な参照のみを許可するために存在します。

## <a name="syntax"></a>構文

```cpp
struct scheduler_ptr;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[scheduler_ptr:: scheduler_ptr](#ctor)|オーバーロードされます。 shared_ptr からスケジューラを指すスケジューラ ポインターを作成します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[scheduler_ptr:: get](#get)|スケジューラへの生のポインターを返します。|

### <a name="public-operators"></a>パブリック演算子

|Name|説明|
|----------|-----------------|
|[scheduler_ptr:: operator bool](#operator_bool)|スケジューラ ポインターが null 以外であるかどうかをテストします。|
|[scheduler_ptr:: operator-&gt;](#operator_ptr)|ポインターのように動作します。|

## <a name="inheritance-hierarchy"></a>継承階層

`scheduler_ptr`

## <a name="requirements"></a>要件

**ヘッダー:** pplinterface.h

**名前空間:** concurrency

## <a name="get"></a>scheduler_ptr:: get メソッド

スケジューラへの生のポインターを返します。

```cpp
scheduler_interface* get() const;
```

### <a name="return-value"></a>戻り値

## <a name="operator_bool"></a>scheduler_ptr:: operator bool

スケジューラポインターが null でないかどうかをテストします。

```cpp
operator bool() const;
```

## <a name="operator_ptr"></a>scheduler_ptr:: operator-&gt;

ポインターのように動作します。

```cpp
scheduler_interface* operator->() const;
```

### <a name="return-value"></a>戻り値

## <a name="ctor"></a>scheduler_ptr:: scheduler_ptr コンストラクター

Shared_ptr から scheduler へのスケジューラポインターを作成します。

```cpp
explicit scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);
explicit scheduler_ptr(_In_opt_ scheduler_interface* pScheduler);
```

### <a name="parameters"></a>パラメーター

*組む*<br/>
変換するスケジューラ。

*pScheduler*<br/>
変換するスケジューラポインター。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
