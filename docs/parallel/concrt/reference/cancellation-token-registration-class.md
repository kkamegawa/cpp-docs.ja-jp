---
title: cancellation_token_registration クラス
ms.date: 11/04/2016
f1_keywords:
- cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration::cancellation_token_registration
helpviewer_keywords:
- cancellation_token_registration class
ms.assetid: 823d63f4-7233-4d65-8976-6152ccf12d0e
ms.openlocfilehash: 9342841e207c93b66521c2fc742c1b1114682f78
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142238"
---
# <a name="cancellation_token_registration-class"></a>cancellation_token_registration クラス

`cancellation_token_registration` クラスは、`cancellation_token` からのコールバック通知を表します。 `register` の `cancellation_token` メソッドを使用して取り消し発生の通知を受け取るとき、`cancellation_token_registration` オブジェクトはハンドルとしてコールバックに返されます。したがって、呼び出し元は `deregister` メソッドを使用して、特定のコールバックが以降行われないように要求できます。

## <a name="syntax"></a>構文

```cpp
class cancellation_token_registration;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[cancellation_token_registration](#ctor)||
|[~ cancellation_token_registration デストラクター](#dtor)||

### <a name="public-operators"></a>パブリック演算子

|Name|説明|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operator=](#operator_eq)||
|[operator==](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>継承階層

`cancellation_token_registration`

## <a name="requirements"></a>要件

**ヘッダー:** pplcancellation_token

**名前空間:** concurrency

## <a name="dtor"></a>~ cancellation_token_registration

```cpp
~cancellation_token_registration();
```

## <a name="ctor"></a>cancellation_token_registration

```cpp
cancellation_token_registration();

cancellation_token_registration(const cancellation_token_registration& _Src);

cancellation_token_registration(cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>パラメーター

*_Src*<br/>
コピーまたは移動する `cancellation_token_registration`。

## <a name="operator_neq"></a>operator! =

```cpp
bool operator!= (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>パラメーター

*_Rhs*<br/>
比較対象の `cancellation_token_registration`。

### <a name="return-value"></a>戻り値

## <a name="operator_eq"></a>operator =

```cpp
cancellation_token_registration& operator= (const cancellation_token_registration& _Src);

cancellation_token_registration& operator= (cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>パラメーター

*_Src*<br/>
割り当てる `cancellation_token_registration`。

### <a name="return-value"></a>戻り値

## <a name="operator_eq_eq"></a>operator = =

```cpp
bool operator== (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>パラメーター

*_Rhs*<br/>
比較対象の `cancellation_token_registration`。

### <a name="return-value"></a>戻り値

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
