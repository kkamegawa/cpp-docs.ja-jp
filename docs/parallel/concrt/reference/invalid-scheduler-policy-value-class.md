---
title: invalid_scheduler_policy_value クラス
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_value
helpviewer_keywords:
- invalid_scheduler_policy_value class
ms.assetid: 8c533e3f-2774-4192-8616-b2313b859bf7
ms.openlocfilehash: 6a66b2b303a4b3b0cb8c2c7a3c515ac8cd1b33a0
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142993"
---
# <a name="invalid_scheduler_policy_value-class"></a>invalid_scheduler_policy_value クラス

このクラスは、`SchedulerPolicy` オブジェクトのポリシー キーがそのキーの無効な値に設定された場合にスローされる例外を表します。

## <a name="syntax"></a>構文

```cpp
class invalid_scheduler_policy_value : public std::exception;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[invalid_scheduler_policy_value](無効-スケジューラ-ポリシー-スレッドの指定-クラス。 md # .ctor|オーバーロードされます。 `invalid_scheduler_policy_value` オブジェクトを構築します。|

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

`invalid_scheduler_policy_value`

## <a name="requirements"></a>［要件］

**ヘッダー:** concrt .h

**名前空間:** concurrency

## <a name="ctor"></a>invalid_scheduler_policy_value

`invalid_scheduler_policy_value` オブジェクトを構築します。

```cpp
explicit _CRTIMP invalid_scheduler_policy_value(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_value() throw();
```

### <a name="parameters"></a>パラメーター

*_Message*<br/>
エラーの説明メッセージ。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[SchedulerPolicy クラス](schedulerpolicy-class.md)
