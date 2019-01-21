---
title: Microsoft::WRL::Wrappers 名前空間
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
ms.openlocfilehash: 953318e09c4c0d00748f2b6189615dbd66677a96
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336557"
---
# <a name="microsoftwrlwrappers-namespace"></a>Microsoft::WRL::Wrappers 名前空間

オブジェクト、文字列、およびハンドルの有効期間管理を簡素化するリソースの取得は初期化 (RAII) のラッパー型を定義します。

## <a name="syntax"></a>構文

```cpp
namespace Microsoft::WRL::Wrappers;
```

## <a name="members"></a>メンバー

### <a name="typedefs"></a>Typedef

|名前|説明|
|----------|-----------------|
|`FileHandle`|`HandleT<HandleTraits::FileHandleTraits>`|

### <a name="classes"></a>クラス

|名前|説明|
|----------|-----------------|
|[CriticalSection クラス](criticalsection-class.md)|クリティカル セクション オブジェクトを表します。|
|[Event クラス (WRL)](event-class-wrl.md)|イベントを表します。|
|[HandleT クラス](handlet-class.md)|オブジェクトへのハンドルを表します。|
|[HString クラス](hstring-class.md)|HSTRING ハンドルの操作をサポートします。|
|[HStringReference クラス](hstringreference-class.md)|既存の文字列から作成された HSTRING を表します。|
|[Mutex クラス](mutex-class.md)|共有リソースを排他的に制御する同期オブジェクトを表します。|
|[RoInitializeWrapper クラス](roinitializewrapper-class.md)|Windows ランタイムを初期化します。|
|[Semaphore クラス](semaphore-class.md)|ユーザーの数に制限をサポートできる共有リソースを制御する同期オブジェクトを表します。|
|[SRWLock クラス](srwlock-class.md)|スリム リーダー/ライター ロックを表します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** corewrappers.h

**名前空間:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>関連項目

[Microsoft::WRL 名前空間](microsoft-wrl-namespace.md)