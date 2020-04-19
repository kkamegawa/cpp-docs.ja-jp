---
title: out_of_memory クラス
ms.date: 11/04/2016
f1_keywords:
- out_of_memory
- AMPRT/out_of_memory
- AMPRT/Concurrency::out_of_memory::out_of_memory
helpviewer_keywords:
- out_of_memory class
ms.assetid: 3aa7e682-8f13-4ae6-9188-31fb423956e4
ms.openlocfilehash: 4edc1db3c1a70a41f9a0493bd3dc484e27f99b44
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126449"
---
# <a name="out_of_memory-class"></a>out_of_memory クラス

システムまたはデバイスのメモリ不足のためにメソッドが失敗した場合にスローされる例外。

## <a name="syntax"></a>構文

```cpp
class out_of_memory : public runtime_exception;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[out_of_memory コンストラクター](#ctor)|`out_of_memory` クラスの新しいインスタンスを初期化します。|

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>［要件］

**ヘッダー:** amprt. h

**名前空間:** Concurrency
## <a name="ctor"></a>out_of_memory

クラスの新しいインスタンスを初期化します。

### <a name="syntax"></a>構文

```cpp
explicit out_of_memory(
    const char * _Message ) throw();

out_of_memory () throw();
```

### <a name="parameters"></a>パラメーター

*_Message*<br/>
エラーの説明。

### <a name="return-value"></a>戻り値

`out_of_memory` クラスの新しいインスタンス。

## <a name="see-also"></a>参照

[コンカレンシー名前空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
