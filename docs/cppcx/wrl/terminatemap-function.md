---
title: TerminateMap 関数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
ms.openlocfilehash: 2a451bf68bfb543ee5e82a9a48097cac7e8a9821
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398122"
---
# <a name="terminatemap-function"></a>TerminateMap 関数

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
inline bool TerminateMap(
   _In_ ModuleBase *module,
   _In_opt_z_ const wchar_t *serverName,
    bool forceTerminate) throw()
```

### <a name="parameters"></a>パラメーター

*module*<br/>
A[モジュール](module-class.md)します。

*serverName*<br/>
パラメーターで指定されたモジュールでクラス ファクトリのサブセットの名前*モジュール*します。

*forceTerminate*<br/>
**true**クラスを終了するに関係なく、ファクトリがアクティブです。**false**クラス ファクトリを終了しない場合は、ファクトリがアクティブにします。

## <a name="return-value"></a>戻り値

**true**クラス ファクトリをすべてが終了した。 それ以外の場合**false**します。

## <a name="remarks"></a>Remarks

指定されたモジュールでクラス ファクトリをシャット ダウンします。

## <a name="requirements"></a>必要条件

**ヘッダー:** module.h

**名前空間:** Microsoft::WRL::Details

## <a name="see-also"></a>関連項目

[Microsoft::WRL::Details 名前空間](microsoft-wrl-details-namespace.md)