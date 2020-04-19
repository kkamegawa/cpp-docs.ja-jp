---
title: DispatchState 構造体
ms.date: 11/04/2016
f1_keywords:
- DispatchState
- CONCRTRM/concurrency::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::m_dispatchStateSize
- CONCRTRM/concurrency::DispatchState::DispatchState::m_fIsPreviousContextAsynchronouslyBlocked
- CONCRTRM/concurrency::DispatchState::DispatchState::m_reserved
helpviewer_keywords:
- DispatchState structure
ms.assetid: 8c52546e-1650-48a0-985f-7e4a0fc26a90
ms.openlocfilehash: 69e00893373ccca6e2ed676fbb7f5a109c49efdf
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143043"
---
# <a name="dispatchstate-structure"></a>DispatchState 構造体

`DispatchState` 構造体は、状態を `IExecutionContext::Dispatch` メソッドに転送するために使用されます。 `Dispatch` メソッドが `IExecutionContext` インターフェイスで呼び出される状況を示します。

## <a name="syntax"></a>構文

```cpp
struct DispatchState;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[DispatchState::D ispatchState](#ctor)|新しい `DispatchState` オブジェクトを構築します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|Name|説明|
|----------|-----------------|
|[DispatchState:: m_dispatchStateSize](#m_dispatchstatesize)|この構造体のサイズ。バージョン管理に使用されます。|
|[DispatchState:: m_fIsPreviousContextAsynchronouslyBlocked](#m_fispreviouscontextasynchronouslyblocked)|前のコンテキストが非同期的にブロックされているために、このコンテキストが `Dispatch` メソッドに入ったかどうかを示します。 これは、UMS スケジューリングコンテキストでのみ使用され、他のすべての実行コンテキストの `0` 値に設定されます。|
|[DispatchState:: m_reserved](#m_reserved)|将来の情報を渡すために予約されているビット。|

## <a name="inheritance-hierarchy"></a>継承階層

`DispatchState`

## <a name="requirements"></a>要件

**ヘッダー:** concrtrm. h

**名前空間:** concurrency

## <a name="ctor"></a>DispatchState::D ispatchState コンストラクター

新しい `DispatchState` オブジェクトを構築します。

```cpp
DispatchState();
```

## <a name="m_dispatchstatesize"></a>DispatchState:: m_dispatchStateSize データメンバー

この構造体のサイズ。バージョン管理に使用されます。

```cpp
unsigned long m_dispatchStateSize;
```

## <a name="m_fispreviouscontextasynchronouslyblocked"></a>DispatchState:: m_fIsPreviousContextAsynchronouslyBlocked データメンバー

前のコンテキストが非同期的にブロックされているために、このコンテキストが `Dispatch` メソッドに入ったかどうかを示します。 これは、UMS スケジューリングコンテキストでのみ使用され、他のすべての実行コンテキストの `0` 値に設定されます。

```cpp
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```

## <a name="m_reserved"></a>DispatchState:: m_reserved データメンバー

将来の情報を渡すために予約されているビット。

```cpp
unsigned int m_reserved : 31;
```

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
