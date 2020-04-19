---
title: IUMSScheduler 構造体
ms.date: 11/04/2016
f1_keywords:
- IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler::IUMSScheduler::SetCompletionList
helpviewer_keywords:
- IUMSScheduler structure
ms.assetid: 3a500225-4e02-4849-bb56-d744865f5870
ms.openlocfilehash: 45df744a9850510006e4bf887c8ed61b000a8e5c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139992"
---
# <a name="iumsscheduler-structure"></a>IUMSScheduler 構造体

コンカレンシー ランタイムのリソース マネージャーによってユーザー モード スケジュール可能 (UMS) スレッドが渡される必要がある作業スケジューラの抽象化のインターフェイスです。 リソース マネージャーでは、このインターフェイスを使用して UMS スレッド スケジューラと通信します。 `IUMSScheduler` インターフェイスは `IScheduler` インターフェイスを継承します。

## <a name="syntax"></a>構文

```cpp
struct IUMSScheduler : public IScheduler;
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[IUMSScheduler:: Set補完リスト](#setcompletionlist)|`IUMSCompletionList` インターフェイスを UMS スレッドスケジューラに割り当てます。|

## <a name="remarks"></a>コメント

リソースマネージャーと通信するカスタムスケジューラを実装していて、通常の Win32 スレッドではなく、UMS スレッドをスケジューラに渡す必要がある場合は、`IUMSScheduler` インターフェイスの実装を提供する必要があります。 また、スケジューラポリシーキー `SchedulerKind` のポリシー値を `UmsThreadDefault`に設定する必要があります。 ポリシーで UMS スレッドが指定されている場合、 [Iresourcemanager:: RegisterScheduler](iresourcemanager-structure.md#registerscheduler)メソッドにパラメーターとして渡される `IScheduler` インターフェイスは、`IUMSScheduler` インターフェイスである必要があります。

リソースマネージャーは、UMS 機能を持つオペレーティングシステムでのみ、UMS スレッドを渡すことができます。 Windows 7 以降のバージョンの64ビットオペレーティングシステムでは、UMS スレッドがサポートされています。 `SchedulerKind` キーを値 `UmsThreadDefault` に設定し、基になるプラットフォームで UMS がサポートされていないスケジューラポリシーを作成すると、そのポリシーの `SchedulerKind` キーの値が `ThreadScheduler`の値に変更されます。 UMS スレッドを受け取ることが予想される前に、常にこのポリシー値を読み取る必要があります。

`IUMSScheduler` インターフェイスは、スケジューラとリソースマネージャーの間の通信の双方向チャネルの1つの端です。 もう一方の端は、リソースマネージャーによって実装される `IResourceManager` および `ISchedulerProxy` インターフェイスによって表されます。

## <a name="inheritance-hierarchy"></a>継承階層

[IScheduler](ischeduler-structure.md)

`IUMSScheduler`

## <a name="requirements"></a>要件

**ヘッダー:** concrtrm. h

**名前空間:** concurrency

## <a name="setcompletionlist"></a>IUMSScheduler:: Set補完リストメソッド

`IUMSCompletionList` インターフェイスを UMS スレッドスケジューラに割り当てます。

```cpp
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```

### <a name="parameters"></a>パラメーター

*P補完の一覧*<br/>
スケジューラの入力候補一覧のインターフェイス。 スケジューラごとにリストが1つあります。

### <a name="remarks"></a>コメント

リソースマネージャーは、スケジューラがリソースの初期割り当てを要求した後に、UMS スレッドを必要とすることを指定するスケジューラでこのメソッドを呼び出します。 スケジューラは、`IUMSCompletionList` インターフェイスを使用して、UMS スレッドプロキシがブロック解除されたタイミングを判断できます。 このインターフェイスにアクセスできるのは、UMS スケジューラに割り当てられている仮想プロセッサルートで実行されているスレッドプロキシからだけです。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[IScheduler 構造体](ischeduler-structure.md)<br/>
[IUMSCompletionList 構造体](iumscompletionlist-structure.md)<br/>
[IResourceManager 構造体](iresourcemanager-structure.md)
