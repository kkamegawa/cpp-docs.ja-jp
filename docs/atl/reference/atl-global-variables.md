---
title: ATL グローバル変数
ms.date: 12/06/2017
f1_keywords:
- ATLBASE/_pAtlModule
helpviewer_keywords:
- global variables, ATL
- _pAtlModule
ms.assetid: e881a319-99ca-4f5d-8a0b-34b3dcd0f37f
ms.openlocfilehash: 4f98b31d2454b7c6e903e5b5b87bceb4ddcb6961
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62248161"
---
# <a name="atl-global-variables"></a>ATL グローバル変数

## <a name="patlmodule"></a>_pAtlModule

現在のモジュールへのポインターを格納するグローバル変数。

```cpp
__declspec(selectany) CAtlModule * _pAtlModule
```

### <a name="remarks"></a>Remarks

Visual C 6.0 で、(古い) クラスが提供される機能を提供する、このグローバル変数のメソッドを使用できます。

### <a name="example"></a>例

```cpp
LONG lLocks = _pAtlModule->GetLockCount();
```

### <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h
