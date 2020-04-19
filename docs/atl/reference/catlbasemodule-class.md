---
title: CAtlBaseModule クラス
ms.date: 11/04/2016
f1_keywords:
- CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::AddResourceInstance
- ATLCORE/ATL::CAtlBaseModule::GetHInstanceAt
- ATLCORE/ATL::CAtlBaseModule::GetModuleInstance
- ATLCORE/ATL::CAtlBaseModule::GetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::RemoveResourceInstance
- ATLCORE/ATL::CAtlBaseModule::SetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::m_bInitFailed
helpviewer_keywords:
- CAtlBaseModule class
ms.assetid: 55ade80c-9b0c-4c51-933e-2158436c1096
ms.openlocfilehash: d382d1fe7d50a2fdeefc9b477625580792de7d6f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62247153"
---
# <a name="catlbasemodule-class"></a>CAtlBaseModule クラス

このクラスは、すべての ATL プロジェクトでインスタンス化されます。

## <a name="syntax"></a>構文

```
class CAtlBaseModule : public _ATL_BASE_MODULE
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAtlBaseModule::CAtlBaseModule](#catlbasemodule)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAtlBaseModule::AddResourceInstance](#addresourceinstance)|格納されているハンドルの一覧には、リソースのインスタンスを追加します。|
|[CAtlBaseModule::GetHInstanceAt](#gethinstanceat)|指定されたリソースのインスタンスへのハンドルを返します。|
|[CAtlBaseModule::GetModuleInstance](#getmoduleinstance)|モジュールのインスタンスを返します、`CAtlBaseModule`オブジェクト。|
|[CAtlBaseModule::GetResourceInstance](#getresourceinstance)|リソース インスタンスを返します、`CAtlBaseModule`オブジェクト。|
|[CAtlBaseModule::RemoveResourceInstance](#removeresourceinstance)|格納されているハンドルの一覧からリソース インスタンスを削除します。|
|[CAtlBaseModule::SetResourceInstance](#setresourceinstance)|リソース インスタンスを設定、`CAtlBaseModule`オブジェクト。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CAtlBaseModule::m_bInitFailed](#m_binitfailed)|モジュールの初期化が失敗したかどうかを示す変数。|

## <a name="remarks"></a>Remarks

インスタンス`CAtlBaseModule`名前付き _AtlBaseModule がモジュールのインスタンスへのハンドルを (既定では、1 つは) リソースが含まれるモジュールと、プライマリを提供するモジュールへのハンドルの配列を識別するハンドルを含む、すべての ATL プロジェクトに存在します。リソース。 `CAtlBaseModule` 複数のスレッドから安全にアクセスします。

このクラスは廃止された置換[CComModule](../../atl/reference/ccommodule-class.md) ATL の以前のバージョンで使用されるクラス

## <a name="inheritance-hierarchy"></a>継承階層

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)

`CAtlBaseModule`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcore.h

##  <a name="addresourceinstance"></a>  CAtlBaseModule::AddResourceInstance

格納されているハンドルの一覧には、リソースのインスタンスを追加します。

```
bool AddResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>パラメーター

*hInst*<br/>
追加するリソースのインスタンス。

### <a name="return-value"></a>戻り値

True を返します、リソースが正常に追加、false それ以外の場合。

##  <a name="catlbasemodule"></a>  CAtlBaseModule::CAtlBaseModule

コンストラクターです。

```
CAtlBaseModule() throw();
```

### <a name="remarks"></a>Remarks

`CAtlBaseModule` を作成します。

##  <a name="gethinstanceat"></a>  CAtlBaseModule::GetHInstanceAt

指定されたリソースのインスタンスへのハンドルを返します。

```
HINSTANCE GetHInstanceAt(int i) throw();
```

### <a name="parameters"></a>パラメーター

*i*<br/>
リソース インスタンスの数。

### <a name="return-value"></a>戻り値

対応するリソースのインスタンスが存在しない場合は、リソースのインスタンス、または NULL にハンドルを返します。

##  <a name="getmoduleinstance"></a>  CAtlBaseModule::GetModuleInstance

モジュールのインスタンスを返します、`CAtlBaseModule`オブジェクト。

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>戻り値

モジュールのインスタンスを返します。

##  <a name="getresourceinstance"></a>  CAtlBaseModule::GetResourceInstance

リソースのインスタンスを返します。

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>戻り値

リソースのインスタンスを返します。

##  <a name="m_binitfailed"></a>  CAtlBaseModule::m_bInitFailed

モジュールの初期化が失敗したかどうかを示す変数。

```
static bool m_bInitFailed;
```

### <a name="remarks"></a>Remarks

True の場合、モジュールが初期化されて、false に初期化に失敗した場合。

##  <a name="removeresourceinstance"></a>  CAtlBaseModule::RemoveResourceInstance

格納されているハンドルの一覧からリソース インスタンスを削除します。

```
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>パラメーター

*hInst*<br/>
削除するリソースのインスタンス。

### <a name="return-value"></a>戻り値

場合は、リソースが正常に削除それ以外の場合は true を返します。

##  <a name="setresourceinstance"></a>  CAtlBaseModule::SetResourceInstance

リソース インスタンスを設定、`CAtlBaseModule`オブジェクト。

```
HINSTANCE SetResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>パラメーター

*hInst*<br/>
リソースの新しいインスタンス。

### <a name="return-value"></a>戻り値

更新されたリソース インスタンスを返します。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)<br/>
[モジュール クラス](../../atl/atl-module-classes.md)
