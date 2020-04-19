---
title: Winmodule に関するグローバル関数
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
ms.openlocfilehash: 0e7450ea2a42c0b35dc5a6d1b77dfb0f2acb9520
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196860"
---
# <a name="winmodule-global-functions"></a>Winmodule に関するグローバル関数

これらの関数のサポートを提供する`_AtlCreateWndData`操作を構造体します。

> [!IMPORTANT]
> Windows ランタイムで実行するアプリケーションでは、次の表に示す関数を使用できません。

|||
|-|-|
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|`_AtlCreateWndData` 構造体を初期化して追加します。|
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|既存の `_AtlCreateWndData` 構造体を抽出します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="atlwinmoduleaddcreatewnddata"></a>  AtlWinModuleAddCreateWndData

`_AtlCreateWndData` 構造体を初期化して追加します。

```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```

### <a name="parameters"></a>パラメーター

*pWinModule*<br/>
モジュールへのポインター [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)構造体。

*pData*<br/>
ポインター、 [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)構造体を初期化して、現在のモジュールに追加します。

*pObject*<br/>
オブジェクトへのポインター**this**ポインター。

### <a name="remarks"></a>Remarks

初期化します、`_AtlCreateWndData`を格納するために使用する構造体、**this**ポインター クラスのインスタンスを参照するために使用し、モジュールの参照の一覧に追加`_ATL_WIN_MODULE70`構造体。 によって呼び出される[CAtlWinModule::AddCreateWndData](catlwinmodule-class.md#addcreatewnddata)します。

##  <a name="atlwinmoduleextractcreatewnddata"></a>  AtlWinModuleExtractCreateWndData

既存の `_AtlCreateWndData` 構造体を抽出します。

```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```

### <a name="parameters"></a>パラメーター

*pWinModule*<br/>
モジュールへのポインター [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)構造体。

### <a name="return-value"></a>戻り値

ポインターを返します、 [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)構造体。

### <a name="remarks"></a>Remarks

この関数は、既存の抽出`_AtlCreateWndData`モジュールのによって参照されている一覧から構造`_ATL_WIN_MODULE70`構造体。

## <a name="see-also"></a>関連項目

[関数](../../atl/reference/atl-functions.md)
