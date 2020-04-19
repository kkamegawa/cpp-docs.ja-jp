---
title: IUMSCompletionList 構造体
ms.date: 11/04/2016
f1_keywords:
- IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList::IUMSCompletionList::GetUnblockNotifications
helpviewer_keywords:
- IUMSCompletionList structure
ms.assetid: 81b5250e-3065-492c-b20d-2cdabf12271a
ms.openlocfilehash: 02382ef4606a6e73804fcbd5ce7735ecf2f0dcc7
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140047"
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList 構造体

UMS の完了リストを表します。 UMS スレッドがブロックされると、基になる仮想プロセッサ ルートでスケジュールする内容を決定するためにスケジューラで指定されているスケジュールのコンテキストがディスパッチされ、元のスレッドがブロックされます。 元のスレッドがブロックされない場合、オペレーション システムは、このインターフェイスからアクセスできる完了リストのキューにそれを配置します。 スケジューラは指定されたスケジュール コンテキスト、または作業を検索するその他の場所にある完了リストを照会できます。

## <a name="syntax"></a>構文

```cpp
struct IUMSCompletionList;
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[IumsGetUnblockNotifications List::](#getunblocknotifications)|このメソッドが最後に呼び出された後に、関連付けられたスレッドプロキシによってブロック解除された実行コンテキストを表す `IUMSUnblockNotification` インターフェイスのチェーンを取得します。|

## <a name="remarks"></a>コメント

スケジューラは、このインターフェイスを利用して入力候補一覧から項目をデキューした後に実行されるアクションについて、非常に注意する必要があります。 項目はスケジューラの実行可能なコンテキストの一覧に配置され、一般にできるだけ早くアクセスできる必要があります。 デキューされた項目の1つに、任意のロックの所有権が与えられている可能性があります。 スケジューラは、デキュー項目への呼び出しと、スケジューラ内から一般にアクセスできるリスト上の項目の配置との間でブロックされる可能性がある任意の関数呼び出しを行うことができません。

## <a name="inheritance-hierarchy"></a>継承階層

`IUMSCompletionList`

## <a name="requirements"></a>要件

**ヘッダー:** concrtrm. h

**名前空間:** concurrency

## <a name="getunblocknotifications"></a>IumsGetUnblockNotifications List:: メソッド

このメソッドが最後に呼び出された後に、関連付けられたスレッドプロキシによってブロック解除された実行コンテキストを表す `IUMSUnblockNotification` インターフェイスのチェーンを取得します。

```cpp
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```

### <a name="return-value"></a>戻り値

`IUMSUnblockNotification` インターフェイスのチェーン。

### <a name="remarks"></a>コメント

実行コンテキストが再スケジュールされると、返された通知は無効になります。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[IUMSScheduler 構造体](iumsscheduler-structure.md)<br/>
[IUMSUnblockNotification 構造体](iumsunblocknotification-structure.md)
