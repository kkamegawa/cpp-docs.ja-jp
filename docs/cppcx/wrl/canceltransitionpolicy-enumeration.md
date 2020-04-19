---
title: CancelTransitionPolicy 列挙型
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::CancelTransitionPolicy::TransitionFromCanceled
- module/Microsoft::WRL::CancelTransitionPolicy::RemainCanceled
- module/Microsoft::WRL::CancelTransitionPolicy
helpviewer_keywords:
- CancelTransitionPolicy Enumeration
ms.assetid: 5de49f7d-e5e3-43e9-bbca-666caf226cef
ms.openlocfilehash: cb07f28794d466dde08719057a21ebf62f989e85
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398759"
---
# <a name="canceltransitionpolicy-enumeration"></a>CancelTransitionPolicy 列挙型

どの非同期操作をしようと終了の状態に遷移することを示します。 完了するか、クライアントが要求の取り消し状態に関してエラーが動作する必要があります。

## <a name="syntax"></a>構文

```cpp
enum CancelTransitionPolicy;
```

## <a name="members"></a>メンバー

### <a name="values"></a>値

|名前|説明|
|----------|-----------------|
|`RemainCanceled`|非同期操作は、クライアントが要求の取り消された状態では現在場合、は、ターミナルの完了またはエラー状態に遷移するのではなく、取り消しの状態が保持することを示します。|
|`TransitionFromCanceled`|状態のターミナル状態に取り消された状態の完了を移行する必要があることを示しますこの場合は、非同期操作は、クライアントが要求の取り消された状態では現在、またはこのフラグを使用する呼び出しによって決定されるエラー。|

## <a name="requirements"></a>必要条件

**ヘッダー:** async.h

**名前空間:** Microsoft::wrl

## <a name="see-also"></a>関連項目

[Microsoft::WRL 名前空間](microsoft-wrl-namespace.md)