---
title: CComClassFactory クラス
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory
- ATLCOM/ATL::CComClassFactory
- ATLCOM/ATL::CComClassFactory::CreateInstance
- ATLCOM/ATL::CComClassFactory::LockServer
helpviewer_keywords:
- CComClassFactory class
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
ms.openlocfilehash: 892153e47ac4e9dd45d5dfc01b76f1ce29d23938
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497449"
---
# <a name="ccomclassfactory-class"></a>CComClassFactory クラス

このクラスは、 [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)インターフェイスを実装します。

## <a name="syntax"></a>構文

```
class CComClassFactory
    : public IClassFactory,
      public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComClassFactory:: CreateInstance](#createinstance)|指定された CLSID のオブジェクトを作成します。|
|[CComClassFactory:: LockServer](#lockserver)|メモリ内のクラスファクトリをロックします。|

## <a name="remarks"></a>Remarks

`CComClassFactory`[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)インターフェイスを実装します。このインターフェイスには、特定の CLSID のオブジェクトを作成するためのメソッドが含まれています。また、新しいオブジェクトをより迅速に作成できるように、メモリ内のクラスファクトリをロックすることもできます。 `IClassFactory`は、システムレジストリに登録し、CLSID を割り当てるすべてのクラスに対して実装する必要があります。

ATL オブジェクトは通常、 [CComCoClass](../../atl/reference/ccomcoclass-class.md)から派生することによってクラスファクトリを取得します。 このクラスには、既定のクラスファクトリ`CComClassFactory`として宣言するマクロ [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) が含まれています。 この既定値をオーバーライドするには、 `DECLARE_CLASSFACTORY`クラス定義で*XXX*マクロのいずれかを指定します。 たとえば、 [DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex)マクロはクラスファクトリに対して指定されたクラスを使用します。

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]

上のクラス定義では`CMyClassFactory` 、がオブジェクトの既定のクラスファクトリとして使用されることを指定しています。 `CMyClassFactory`はから`CComClassFactory`派生し、 `CreateInstance`をオーバーライドする必要があります。

ATL には、クラスファクトリを宣言する次の3つのマクロが用意されています。

- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)を使用します。これはライセンスによる作成を制御します。

- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)複数のアパートメントにオブジェクトを作成する[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)を使用します。

- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton)1つの[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)オブジェクトを構築する[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)を使用します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="createinstance"></a>CComClassFactory:: CreateInstance

指定した CLSID のオブジェクトを作成し、このオブジェクトへのインターフェイスポインターを取得します。

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
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

##  <a name="lockserver"></a>  CComClassFactory::LockServer

`_Module::Lock` と`_Module::Unlock`をそれぞれ呼び出して、モジュールのロックカウントをインクリメントおよびデクリメントします。

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>パラメーター

*fLock*<br/>
からTRUE の場合、ロック数がインクリメントされます。それ以外の場合は、ロック数が減少します。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

`_Module`[CComModule](../../atl/reference/ccommodule-class.md)のグローバルインスタンス、またはそれから派生したクラスを参照します。

を`LockServer`呼び出すことにより、クライアントは、複数のオブジェクトをすばやく作成できるように、クラスファクトリに保持できます。

## <a name="see-also"></a>関連項目

[CComObjectRootEx クラス](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
