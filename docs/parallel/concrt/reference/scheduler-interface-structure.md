---
title: scheduler_interface 構造体
ms.date: 11/04/2016
f1_keywords:
- scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface::scheduler_interface::schedule
ms.assetid: 4de61c78-a2c6-4698-bd47-964baf7fa287
ms.openlocfilehash: 36feff80cab1c5d301c009a581b869d5c2bad5e9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142149"
---
# <a name="scheduler_interface-structure"></a>scheduler_interface 構造体

スケジューラ インターフェイス

## <a name="syntax"></a>構文

```cpp
struct __declspec(novtable) scheduler_interface;
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[scheduler_interface:: schedule](#schedule)||

## <a name="inheritance-hierarchy"></a>継承階層

`scheduler_interface`

## <a name="requirements"></a>［要件］

**ヘッダー:** pplinterface.h

**名前空間:** concurrency

## <a name="schedule"></a>scheduler_interface:: schedule メソッド

```cpp
virtual void schedule(
    TaskProc_t,
void*) = 0;
```

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
