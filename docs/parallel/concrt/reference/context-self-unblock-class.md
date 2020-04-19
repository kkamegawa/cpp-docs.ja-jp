---
title: context_self_unblock クラス
ms.date: 11/04/2016
f1_keywords:
- context_self_unblock
- CONCRT/concurrency::context_self_unblock
- CONCRT/concurrency::context_self_unblock::context_self_unblock
helpviewer_keywords:
- context_self_unblock class
ms.assetid: 9601cd28-4f40-4c2e-89ab-747068956331
ms.openlocfilehash: 883d5630251a6ea13afba1164f221a0da1773c17
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143111"
---
# <a name="context_self_unblock-class"></a>context_self_unblock クラス

このクラスは、同じコンテキストから `Unblock` オブジェクトの `Context` メソッドが呼び出された場合にスローされる例外を表します。 これは、特定のコンテキストがそれ自体のブロックを解除しようとしたことを示します。

## <a name="syntax"></a>構文

```cpp
class context_self_unblock : public std::exception;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[context_self_unblock](#ctor)|オーバーロードされます。 `context_self_unblock` オブジェクトを構築します。|

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

`context_self_unblock`

## <a name="requirements"></a>要件

**ヘッダー:** concrt .h

**名前空間:** concurrency

## <a name="ctor"></a>context_self_unblock

`context_self_unblock` オブジェクトを構築します。

```cpp
explicit _CRTIMP context_self_unblock(_In_z_ const char* _Message) throw();

context_self_unblock() throw();
```

### <a name="parameters"></a>パラメーター

*_Message*<br/>
エラーの説明メッセージ。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
