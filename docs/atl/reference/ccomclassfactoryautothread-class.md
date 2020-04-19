---
title: CComClassFactoryAutoThread クラス
ms.date: 11/04/2016
f1_keywords:
- CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread::CreateInstance
- ATLCOM/ATL::CComClassFactoryAutoThread::LockServer
helpviewer_keywords:
- CComClassFactoryAutoThread class
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
ms.openlocfilehash: 73879a73a48290e19d2a27307884953129826df7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497488"
---
# <a name="ccomclassfactoryautothread-class"></a>CComClassFactoryAutoThread クラス

このクラスは、 [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)インターフェイスを実装し、複数のアパートメントでオブジェクトを作成できるようにします。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CComClassFactoryAutoThread
    : public IClassFactory,
      public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComClassFactoryAutoThread:: CreateInstance](#createinstance)|指定された CLSID のオブジェクトを作成します。|
|[CComClassFactoryAutoThread:: LockServer](#lockserver)|メモリ内のクラスファクトリをロックします。|

## <a name="remarks"></a>Remarks

`CComClassFactoryAutoThread`は[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)に似ていますが、複数のアパートメントでオブジェクトを作成することができます。 このサポートを利用するには、 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)から EXE モジュールを派生させます。

ATL オブジェクトは通常、 [CComCoClass](../../atl/reference/ccomcoclass-class.md)から派生することによってクラスファクトリを取得します。 このクラスには、 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)を既定のクラスファクトリとして宣言する[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)マクロが含まれています。 を使用`CComClassFactoryAutoThread`するには、オブジェクトのクラス定義で[DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)マクロを指定します。 例えば:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]

## <a name="inheritance-hierarchy"></a>継承階層

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

`CComClassFactoryAutoThread`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="createinstance"></a>CComClassFactoryAutoThread:: CreateInstance

指定した CLSID のオブジェクトを作成し、このオブジェクトへのインターフェイスポインターを取得します。

```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>パラメーター

*pUnkOuter*<br/>
からオブジェクトが集計の一部として作成されている場合、 *pUnkOuter*は外側の unknown である必要があります。 それ以外の場合、 *pUnkOuter*は NULL である必要があります。

*riid*<br/>
から要求されたインターフェイスの IID。 *PUnkOuter*が NULL 以外の場合、 *riid*はで`IID_IUnknown`ある必要があります。

*ppvObj*<br/>
入出力*Riid*によって識別されるインターフェイスポインターへのポインター。 オブジェクトがこのインターフェイスをサポートしていない場合、 *ppvObj*は NULL に設定されます。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

モジュールが[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)から派生した`CreateInstance`場合、はまず、関連付けられているアパートメントにオブジェクトを作成するスレッドを選択します。

##  <a name="lockserver"></a>  CComClassFactoryAutoThread::LockServer

`_Module::Lock` と`_Module::Unlock`をそれぞれ呼び出して、モジュールのロックカウントをインクリメントおよびデクリメントします。

```
STDMETHODIMP LockServer(BOOL fLock);
```

### <a name="parameters"></a>パラメーター

*fLock*<br/>
からTRUE の場合、ロック数がインクリメントされます。それ以外の場合は、ロック数が減少します。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

を使用`CComClassFactoryAutoThread`する`_Module`場合、通常は[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)のグローバルインスタンスを参照します。

を`LockServer`呼び出すことで、クライアントは、複数のオブジェクトをすばやく作成できるように、クラスファクトリに保持できます。

## <a name="see-also"></a>関連項目

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2 クラス](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComClassFactorySingleton クラス](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[CComObjectRootEx クラス](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
