---
title: unsupported_os クラス
ms.date: 11/04/2016
f1_keywords:
- unsupported_os
- CONCRT/concurrency::unsupported_os
- CONCRT/concurrency::unsupported_os::unsupported_os
helpviewer_keywords:
- unsupported_os class
ms.assetid: 6fa57636-341b-4b51-84cc-261d283ff736
ms.openlocfilehash: 253cd76182e1b6f85be3701663bd10c86c10e6ba
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142342"
---
# <a name="unsupported_os-class"></a>unsupported_os クラス

このクラスは、サポート外のオペレーティング システムが使用された場合にスローされる例外を表します。

## <a name="syntax"></a>構文

```cpp
class unsupported_os : public std::exception;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[unsupported_os](#ctor)|オーバーロードされます。 `unsupported_os` オブジェクトを構築します。|

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

`unsupported_os`

## <a name="requirements"></a>要件

**ヘッダー:** concrt .h

**名前空間:** concurrency

## <a name="ctor"></a>unsupported_os

`unsupported_os` オブジェクトを構築します。

### <a name="syntax"></a>構文

```cpp
explicit _CRTIMP unsupported_os(_In_z_ const char* _Message) throw();

unsupported_os() throw();
```

### <a name="parameters"></a>パラメーター

*_Message*<br/>
エラーの説明メッセージ。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
