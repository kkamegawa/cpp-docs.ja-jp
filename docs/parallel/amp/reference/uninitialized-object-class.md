---
title: uninitialized_object クラス
ms.date: 03/27/2019
f1_keywords:
- uninitialized_object
- AMPRT/uninitialized_object
- AMPRT/Concurrency::uninitialized_object
helpviewer_keywords:
- uninitialized_object class
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
ms.openlocfilehash: ef7ded0bf925d3430b70064c4979b75e08f9cf45
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127700"
---
# <a name="uninitialized_object-class"></a>uninitialized_object クラス

初期化されていないオブジェクトが使用される場合にスローされる例外です。

## <a name="syntax"></a>構文

```cpp
class uninitialized_object : public runtime_exception;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[uninitialized_object コンストラクター](#uninitialized_object)|`uninitialized_object` クラスの新しいインスタンスを初期化します。|

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

`runtime_exception`

`uninitialized_object`

## <a name="requirements"></a>［要件］

**ヘッダー:** amprt. h

**名前空間:** Concurrency

## <a name="uninitialized_object"></a>uninitialized_object

`uninitialized_object` 例外の新しいインスタンスを構築します。

### <a name="syntax"></a>構文

```cpp
explicit uninitialized_object(
    const char * _Message ) throw();

uninitialized_object() throw();
```

### <a name="parameters"></a>パラメーター

*_Message*<br/>
エラーの説明。

### <a name="return-value"></a>戻り値

`uninitialized_object` exception オブジェクトです。

## <a name="see-also"></a>参照

[コンカレンシー名前空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
