---
title: default_scheduler_exists クラス
ms.date: 11/04/2016
f1_keywords:
- default_scheduler_exists
- CONCRT/concurrency::default_scheduler_exists
- CONCRT/concurrency::default_scheduler_exists::default_scheduler_exists
helpviewer_keywords:
- default_scheduler_exists class
ms.assetid: f6e575e2-4e0f-455a-9e06-54f462ce0c1c
ms.openlocfilehash: eed5dd242beb4c4cd481f22635e0d5f71c28d7e6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139188"
---
# <a name="default_scheduler_exists-class"></a>default_scheduler_exists クラス

このクラスは、既定のスケジューラが既にプロセス内に存在するときに `Scheduler::SetDefaultSchedulerPolicy` メソッドが呼び出された場合にスローされる例外を表します。

## <a name="syntax"></a>構文

```cpp
class default_scheduler_exists : public std::exception;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[default_scheduler_exists](#ctor)|オーバーロードされます。 `default_scheduler_exists` オブジェクトを構築します。|

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

`default_scheduler_exists`

## <a name="requirements"></a>要件

**ヘッダー:** concrt .h

**名前空間:** concurrency

## <a name="ctor"></a>default_scheduler_exists

`default_scheduler_exists` オブジェクトを構築します。

```cpp
explicit _CRTIMP default_scheduler_exists(_In_z_ const char* _Message) throw();

default_scheduler_exists() throw();
```

### <a name="parameters"></a>パラメーター

*_Message*<br/>
エラーの説明メッセージ。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
