---
title: CComObjectStack クラス
ms.date: 11/04/2016
f1_keywords:
- CComObjectStack
- ATLCOM/ATL::CComObjectStack
- ATLCOM/ATL::CComObjectStack::CComObjectStack
- ATLCOM/ATL::CComObjectStack::AddRef
- ATLCOM/ATL::CComObjectStack::QueryInterface
- ATLCOM/ATL::CComObjectStack::Release
- ATLCOM/ATL::CComObjectStack::m_hResFinalConstruct
helpviewer_keywords:
- CComObjectStack class
ms.assetid: 3da72c40-c834-45f6-bb76-6ac204028d80
ms.openlocfilehash: 19fd226e617e4cdb1bba8a113b8984c36bf28d59
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259587"
---
# <a name="ccomobjectstack-class"></a>CComObjectStack クラス

このクラスは、一時的な COM オブジェクトを作成し、スケルトンの実装が提供されます`IUnknown`します。

## <a name="syntax"></a>構文

```
template <class  Base>
class CComObjectStack : public Base
```

#### <a name="parameters"></a>パラメーター

*ベース*<br/>
派生したクラス、 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)または[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)オブジェクトでサポートするその他のインターフェイスからも、します。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CComObjectStack::CComObjectStack](#ccomobjectstack)|コンストラクターです。|
|[CComObjectStack::~CComObjectStack](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComObjectStack::AddRef](#addref)|0 を返します。 デバッグ モードで呼び出して`_ASSERTE`します。|
|[CComObjectStack::QueryInterface](#queryinterface)|E_NOINTERFACE を返します。 デバッグ モードで呼び出して`_ASSERTE`します。|
|[CComObjectStack::Release](#release)|0 を返します。 デバッグ モードで呼び出して`_ASSERTE`します。 ~|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CComObjectStack::m_hResFinalConstruct](#m_hresfinalconstruct)|構築時に返される HRESULT を含む、`CComObjectStack`オブジェクト。|

## <a name="remarks"></a>Remarks

`CComObjectStack` 一時的な COM オブジェクトを作成し、オブジェクトのスケルトンの実装を提供するために使用`IUnknown`します。 通常、オブジェクトは、1 つの関数は、スタックにプッシュ) 内のローカル変数として使用されます。 関数が終了するときに、オブジェクトが破棄されるため、効率を向上させる参照カウントが実行されませんが。

次の例では、関数内で使用される COM オブジェクトを作成する方法を示します。

[!code-cpp[NVC_ATL_COM#42](../../atl/codesnippet/cpp/ccomobjectstack-class_1.cpp)]

一時オブジェクト`Tempobj`がスタックにプッシュされ、自動的には、関数が終了したときに表示されなくなります。

## <a name="inheritance-hierarchy"></a>継承階層

`Base`

`CComObjectStack`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom.h

##  <a name="addref"></a>  CComObjectStack::AddRef

0 を返します。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>戻り値

0 を返します。

### <a name="remarks"></a>Remarks

デバッグ モードで呼び出して`_ASSERTE`します。

##  <a name="ccomobjectstack"></a>  CComObjectStack::CComObjectStack

コンストラクターです。

```
CComObjectStack(void* = NULL);
```

### <a name="remarks"></a>Remarks

呼び出し`FinalConstruct`し、設定[m_hResFinalConstruct](#m_hresfinalconstruct)によって返される HRESULT に`FinalConstruct`します。 基底クラスを派生していない場合[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)、独自に指定する必要があります`FinalConstruct`メソッド。 このデストラクターは `FinalRelease` を呼び出します。

##  <a name="dtor"></a>  CComObjectStack:: ~ CComObjectStack

デストラクターです。

```
CComObjectStack();
```

### <a name="remarks"></a>Remarks

割り当てられているすべてのリソースを解放[FinalRelease](ccomobjectrootex-class.md#finalrelease)します。

##  <a name="m_hresfinalconstruct"></a>  CComObjectStack::m_hResFinalConstruct

呼び出しから返される HRESULT を含む`FinalConstruct`の構築時に、`CComObjectStack`オブジェクト。

```
HRESULT    m_hResFinalConstruct;
```

##  <a name="queryinterface"></a>  CComObjectStack::QueryInterface

E_NOINTERFACE を返します。

```
HRESULT    QueryInterface(REFIID, void**);
```

### <a name="return-value"></a>戻り値

E_NOINTERFACE を返します。

### <a name="remarks"></a>Remarks

デバッグ モードで呼び出して`_ASSERTE`します。

##  <a name="release"></a>  CComObjectStack::Release

0 を返します。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>戻り値

0 を返します。

### <a name="remarks"></a>Remarks

デバッグ モードで呼び出して`_ASSERTE`します。

## <a name="see-also"></a>関連項目

[CComAggObject クラス](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject クラス](../../atl/reference/ccomobject-class.md)<br/>
[CComObjectGlobal クラス](../../atl/reference/ccomobjectglobal-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
