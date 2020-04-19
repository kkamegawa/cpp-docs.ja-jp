---
title: CAtlWinModule クラス
ms.date: 11/04/2016
f1_keywords:
- CAtlWinModule
- ATLBASE/ATL::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::AddCreateWndData
- ATLBASE/ATL::CAtlWinModule::ExtractCreateWndData
helpviewer_keywords:
- CAtlWinModule class
ms.assetid: 7ec844af-0f68-4a34-b0c8-9de50a025df0
ms.openlocfilehash: d0bc98fa48f84e67ab38106dea3fe22d5ad1757d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246825"
---
# <a name="catlwinmodule-class"></a>CAtlWinModule クラス

このクラスは、ATL windowing コンポーネントのサポートを提供します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CAtlWinModule : public _ATL_WIN_MODULE
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAtlWinModule::CAtlWinModule](#catlwinmodule)|コンストラクターです。|
|[CAtlWinModule::~CAtlWinModule](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAtlWinModule::AddCreateWndData](#addcreatewnddata)|データ オブジェクトを追加します。|
|[CAtlWinModule::ExtractCreateWndData](#extractcreatewnddata)|ウィンドウのモジュールのデータ オブジェクトへのポインターを返します。|

## <a name="remarks"></a>Remarks

このクラスは、ウィンドウ機能を必要とするすべての ATL クラスのサポートを提供します。

## <a name="inheritance-hierarchy"></a>継承階層

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)

`CAtlWinModule`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="addcreatewnddata"></a>  CAtlWinModule::AddCreateWndData

このメソッドを初期化し、追加、`_AtlCreateWndData`構造体。

```
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>パラメーター

*pData*<br/>
ポインター、`_AtlCreateWndData`構造体を初期化して、現在のモジュールに追加します。

*pObject*<br/>
オブジェクトへのポインター**this**ポインター。

### <a name="remarks"></a>Remarks

このメソッドを呼び出す[AtlWinModuleAddCreateWndData](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata)どの初期化、 [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)構造体。 この構造体を格納する、**this**ポインターをウィンドウ プロシージャ内のクラスのインスタンスを取得するために使用します。

##  <a name="catlwinmodule"></a>  CAtlWinModule::CAtlWinModule

コンストラクターです。

```
CAtlWinModule();
```

### <a name="remarks"></a>Remarks

初期化に失敗した場合、 **EXCEPTION_NONCONTINUABLE**例外が発生します。

##  <a name="dtor"></a>  CAtlWinModule::~CAtlWinModule

デストラクターです。

```
~CAtlWinModule();
```

### <a name="remarks"></a>Remarks

割り当てられているすべてのリソースを解放します。

##  <a name="extractcreatewnddata"></a>  CAtlWinModule::ExtractCreateWndData

このメソッドへのポインターを返します、`_AtlCreateWndData`構造体。

```
void* ExtractCreateWndData();
```

### <a name="return-value"></a>戻り値

ポインターを返します、`_AtlCreateWndData`構造に追加した[CAtlWinModule::AddCreateWndData](#addcreatewnddata)、使用可能なオブジェクトがない場合は null です。

## <a name="see-also"></a>関連項目

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[クラスの概要](../../atl/atl-class-overview.md)<br/>
[モジュール クラス](../../atl/atl-module-classes.md)
