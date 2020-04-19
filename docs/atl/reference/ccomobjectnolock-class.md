---
title: CComObjectNoLock クラス
ms.date: 11/04/2016
f1_keywords:
- CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::AddRef
- ATLCOM/ATL::CComObjectNoLock::QueryInterface
- ATLCOM/ATL::CComObjectNoLock::Release
helpviewer_keywords:
- CComObjectNoLock class
ms.assetid: 288c6506-7da8-4127-8d58-7f4bd779539a
ms.openlocfilehash: 9253c7495f4d13ed6ce609988251d8abd09592ad
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497036"
---
# <a name="ccomobjectnolock-class"></a>CComObjectNoLock クラス

このクラスは`IUnknown` 、非集計オブジェクトに対してを実装しますが、コンストラクターのモジュールロック数をインクリメントしません。

## <a name="syntax"></a>構文

```
template<class Base>
class CComObjectNoLock : public Base
```

#### <a name="parameters"></a>パラメーター

*常用*<br/>
[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)または[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)から派生したクラス、およびオブジェクトでサポートする他のインターフェイスから派生したクラス。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CComObjectNoLock::CComObjectNoLock](#ccomobjectnolock)|コンストラクターです。|
|[CComObjectNoLock:: ~ CComObjectNoLock](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComObjectNoLock::AddRef](#addref)|オブジェクトの参照カウントをインクリメントします。|
|[CComObjectNoLock::QueryInterface](#queryinterface)|要求されたインターフェイスへのポインターを返します。|
|[CComObjectNoLock::Release](#release)|オブジェクトの参照カウントをデクリメントします。|

## <a name="remarks"></a>Remarks

`CComObjectNoLock`は、非集計オブジェクトに対して[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)を実装するという点で、 [CComObject](../../atl/reference/ccomobject-class.md)に似ています。ただし、 `CComObjectNoLock`では、コンストラクターのモジュールロックカウントはインクリメントされません。

ATL で`CComObjectNoLock`は、クラスファクトリに対して内部的にを使用します。 一般に、このクラスは直接使用しません。

## <a name="inheritance-hierarchy"></a>継承階層

`Base`

`CComObjectNoLock`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="addref"></a>  CComObjectNoLock::AddRef

オブジェクトの参照カウントをインクリメントします。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>戻り値

診断またはテストに役立つ可能性のある値。

##  <a name="ccomobjectnolock"></a>  CComObjectNoLock::CComObjectNoLock

コンストラクターです。 [CComObject](../../atl/reference/ccomobject-class.md)とは異なり、はモジュールのロックカウントをインクリメントしません。

```
CComObjectNoLock(void* = NULL);
```

### <a name="parameters"></a>パラメーター

<em>void\*</em><br/>
からこの無名パラメーターは使用されません。 これは、他の`CComXXXObjectXXX`コンストラクターとの対称のために存在します。

##  <a name="dtor"></a>CComObjectNoLock:: ~ CComObjectNoLock

デストラクターです。

```
~CComObjectNoLock();
```

### <a name="remarks"></a>Remarks

割り当てられたすべてのリソースを解放し、 [FinalRelease](ccomobjectrootex-class.md#finalrelease)を呼び出します。

##  <a name="queryinterface"></a>  CComObjectNoLock::QueryInterface

要求されたインターフェイスへのポインターを取得します。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>パラメーター

*iid*<br/>
から要求されているインターフェイスの識別子。

*ppvObject*<br/>
入出力*Iid*によって識別されるインターフェイスポインターへのポインター。 オブジェクトがこのインターフェイスをサポートしていない場合、 *ppvObject*は NULL に設定されます。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

##  <a name="release"></a>  CComObjectNoLock::Release

オブジェクトの参照カウントをデクリメントします。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>戻り値

デバッグビルドでは`Release` 、診断またはテストに役立つ値が返されます。 非デバッグビルドでは、 `Release`は常に0を返します。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
