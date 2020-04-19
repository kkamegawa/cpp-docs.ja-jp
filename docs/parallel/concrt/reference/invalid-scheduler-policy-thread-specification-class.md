---
title: invalid_scheduler_policy_thread_specification クラス
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_thread_specification
helpviewer_keywords:
- invalid_scheduler_policy_thread_specification class
ms.assetid: 2d0fafb2-18f8-4284-8040-3db640d33303
ms.openlocfilehash: b6c2fd853ae19c48ae04d6601eb47e5afcb71944
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143034"
---
# <a name="invalid_scheduler_policy_thread_specification-class"></a>invalid_scheduler_policy_thread_specification クラス

このクラスは、`SchedulerPolicy` オブジェクトのコンカレンシー数の限度を設定する際に、`MinConcurrency` キーに指定された値が `MaxConcurrency` キーの値よりも小さい場合にスローされる例外を表します。

## <a name="syntax"></a>構文

```cpp
class invalid_scheduler_policy_thread_specification : public std::exception;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-value-class.md#ctor|オーバーロードされます。 `invalid_scheduler_policy_value` オブジェクトを構築します。|

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

`invalid_scheduler_policy_thread_specification`

## <a name="requirements"></a>［要件］

**ヘッダー:** concrt .h

**名前空間:** concurrency

## <a name="ctor"></a>invalid_scheduler_policy_thread_specification

`invalid_scheduler_policy_value` オブジェクトを構築します。

```cpp
explicit _CRTIMP invalid_scheduler_policy_thread_specification(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_thread_specification() throw();
```

### <a name="parameters"></a>パラメーター

*_Message*<br/>
エラーの説明メッセージ。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[SchedulerPolicy クラス](schedulerpolicy-class.md)
