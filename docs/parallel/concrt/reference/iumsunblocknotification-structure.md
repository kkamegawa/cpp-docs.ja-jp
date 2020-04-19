---
title: IUMSUnblockNotification 構造体
ms.date: 11/04/2016
f1_keywords:
- IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetContext
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetNextUnblockNotification
helpviewer_keywords:
- IUMSUnblockNotification structure
ms.assetid: eaca9529-c1cc-472b-8ec6-722a1ff0fa2a
ms.openlocfilehash: d4fd95b1f11ed6edac26cb03e41e8b650acfafa3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139980"
---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification 構造体

ブロックされ、スケジューラの指定されたスケジュール コンテキストに制御を戻すことをトリガーされたスレッド プロキシが、ブロック解除され、スケジュールできる状態であることを示す、リソース マネージャーからの通知を表します。 このインターフェイスは、`GetContext` メソッドから返される、スレッド プロキシの関連付けられた実行コンテキストが再スケジュールされると無効になります。

## <a name="syntax"></a>構文

```cpp
struct IUMSUnblockNotification;
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[IUMSUnblockNotification:: GetContext](#getcontext)|ブロック解除されたスレッドプロキシに関連付けられている実行コンテキストの `IExecutionContext` インターフェイスを返します。 このメソッドが返され、基になる実行コンテキストが `IThreadProxy::SwitchTo` メソッドの呼び出しによって再スケジュールされると、このインターフェイスは無効になります。|
|[IUMSUnblockNotification:: GetNextUnblockNotification](#getnextunblocknotification)|メソッド `IUMSCompletionList::GetUnblockNotifications`から返されたチェーン内の次の `IUMSUnblockNotification` インターフェイスを返します。|

## <a name="inheritance-hierarchy"></a>継承階層

`IUMSUnblockNotification`

## <a name="requirements"></a>［要件］

**ヘッダー:** concrtrm. h

**名前空間:** concurrency

## <a name="getcontext"></a>IUMSUnblockNotification:: GetContext メソッド

ブロック解除されたスレッドプロキシに関連付けられている実行コンテキストの `IExecutionContext` インターフェイスを返します。 このメソッドが返され、基になる実行コンテキストが `IThreadProxy::SwitchTo` メソッドの呼び出しによって再スケジュールされると、このインターフェイスは無効になります。

```cpp
virtual IExecutionContext* GetContext() = 0;
```

### <a name="return-value"></a>戻り値

ブロック解除されたスレッドプロキシへの実行コンテキストの `IExecutionContext` インターフェイス。

## <a name="getnextunblocknotification"></a>IUMSUnblockNotification:: GetNextUnblockNotification メソッド

メソッド `IUMSCompletionList::GetUnblockNotifications`から返されたチェーン内の次の `IUMSUnblockNotification` インターフェイスを返します。

```cpp
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```

### <a name="return-value"></a>戻り値

メソッド `IUMSCompletionList::GetUnblockNotifications`から返されたチェーン内の次の `IUMSUnblockNotification` インターフェイス。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[IUMSScheduler 構造体](iumsscheduler-structure.md)<br/>
[IUMSCompletionList 構造体](iumscompletionlist-structure.md)
