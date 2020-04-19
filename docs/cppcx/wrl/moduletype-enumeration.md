---
title: ModuleType 列挙型
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
ms.openlocfilehash: 3c7486cbc761975dd133f229f23dcf0b70e7e3ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403231"
---
# <a name="moduletype-enumeration"></a>ModuleType 列挙型

モジュールがインプロセス サーバーまたはアウトプロセス サーバーをサポートするかどうかを指定します。

## <a name="syntax"></a>構文

```cpp
enum ModuleType;
```

## <a name="members"></a>メンバー

### <a name="values"></a>値

|名前|説明|
|----------|-----------------|
|`InProc`|・ インプロセス サーバーです。|
|`OutOfProc`|アウト プロセス サーバーの場合。|
|`DisableCaching`|モジュールのキャッシュ メカニズムを無効にします。|
|`InProcDisableCaching`|組み合わせた`InProc`と`DisableCaching`します。|
|`OutOfProcDisableCaching`|組み合わせた`OutOfProc`と`DisableCaching`します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** module.h

**名前空間:** Microsoft::wrl

## <a name="see-also"></a>関連項目

[Microsoft::WRL 名前空間](microsoft-wrl-namespace.md)