---
title: CComObjectGlobal クラス
ms.date: 11/04/2016
f1_keywords:
- CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::AddRef
- ATLCOM/ATL::CComObjectGlobal::QueryInterface
- ATLCOM/ATL::CComObjectGlobal::Release
- ATLCOM/ATL::CComObjectGlobal::m_hResFinalConstruct
helpviewer_keywords:
- CComObjectGlobal class
ms.assetid: 79bdee55-66e4-4536-b5b3-bdf09f78b9a6
ms.openlocfilehash: ec3abd04ce72cce98dae72a1ed8cbb8d9fe72079
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259340"
---
# <a name="ccomobjectglobal-class"></a>CComObjectGlobal クラス

このクラスの参照カウントを含むモジュールの管理、`Base`オブジェクト。

## <a name="syntax"></a>構文

```
template<class Base>
class CComObjectGlobal : public Base
```

#### <a name="parameters"></a>パラメーター

*ベース*<br/>
派生したクラス、 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)または[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)オブジェクトでサポートするその他のインターフェイスからも、します。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CComObjectGlobal::CComObjectGlobal](#ccomobjectglobal)|コンストラクターです。|
|[CComObjectGlobal:: ~ CComObjectGlobal](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComObjectGlobal::AddRef](#addref)|グローバル実装`AddRef`します。|
|[CComObjectGlobal::QueryInterface](#queryinterface)|グローバル実装`QueryInterface`します。|
|[CComObjectGlobal::Release](#release)|グローバル実装`Release`します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CComObjectGlobal::m_hResFinalConstruct](#m_hresfinalconstruct)|構築時に返される HRESULT を含む、`CComObjectGlobal`オブジェクト。|

## <a name="remarks"></a>Remarks

`CComObjectGlobal` 参照カウントを含むモジュールを管理、`Base`オブジェクト。 `CComObjectGlobal` により、モジュールが解放されない限り、オブジェクトは削除されません。 オブジェクトは、モジュール全体の参照カウントがゼロになったときにのみ削除されます。

たとえばを使用して`CComObjectGlobal`、クラス ファクトリは、すべてのクライアントで共有されている一般的なグローバル オブジェクトを保持できます。

## <a name="inheritance-hierarchy"></a>継承階層

`Base`

`CComObjectGlobal`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom.h

##  <a name="addref"></a>  CComObjectGlobal::AddRef

オブジェクトの参照カウントを 1 だけインクリメントします。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>戻り値

診断に役立ちますし、テスト可能性のある値。

### <a name="remarks"></a>Remarks

既定では、`AddRef`呼び出し`_Module::Lock`ここで、`_Module`のグローバル インスタンス[CComModule](../../atl/reference/ccommodule-class.md)またはその派生クラス。

##  <a name="ccomobjectglobal"></a>  CComObjectGlobal::CComObjectGlobal

コンストラクターです。 呼び出し`FinalConstruct`し、設定[m_hResFinalConstruct](#m_hresfinalconstruct)を`HRESULT`によって返される`FinalConstruct`します。

```
CComObjectGlobal(void* = NULL));
```

### <a name="remarks"></a>Remarks

基底クラスを派生していない場合[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)、独自に指定する必要があります`FinalConstruct`メソッド。 このデストラクターは `FinalRelease` を呼び出します。

##  <a name="dtor"></a>  CComObjectGlobal:: ~ CComObjectGlobal

デストラクターです。

```
CComObjectGlobal();
```

### <a name="remarks"></a>Remarks

割り当てられているすべてのリソースを解放[FinalRelease](ccomobjectrootex-class.md#finalrelease)します。

##  <a name="m_hresfinalconstruct"></a>  CComObjectGlobal::m_hResFinalConstruct

呼び出しから HRESULT を含む`FinalConstruct`の構築時に、`CComObjectGlobal`オブジェクト。

```
HRESULT m_hResFinalConstruct;
```

##  <a name="queryinterface"></a>  CComObjectGlobal::QueryInterface

要求されたインターフェイス ポインターへのポインターを取得します。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>パラメーター

*iid*<br/>
[in]要求されているインターフェイスの GUID です。

*ppvObject*<br/>
[out]インターフェイスが見つからない場合は、iid、または NULL で識別されるインターフェイス ポインターへのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

`QueryInterface` が処理するのは、COM マップ テーブル内のインターフェイスのみです。

##  <a name="release"></a>  CComObjectGlobal::Release

オブジェクトの参照カウントを 1 だけデクリメントします。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>戻り値

デバッグ ビルドで`Release`診断に役立ちますし、テスト可能性のある値を返します。 非デバッグ ビルドで`Release`常に 0 を返します。

### <a name="remarks"></a>Remarks

既定では、`Release`呼び出し`_Module::Unlock`ここで、`_Module`のグローバル インスタンス[CComModule](../../atl/reference/ccommodule-class.md)またはその派生クラス。

## <a name="see-also"></a>関連項目

[CComObjectStack クラス](../../atl/reference/ccomobjectstack-class.md)<br/>
[CComAggObject クラス](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject クラス](../../atl/reference/ccomobject-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
