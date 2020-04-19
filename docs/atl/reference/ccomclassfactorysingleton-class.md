---
title: CComClassFactorySingleton クラス
ms.date: 11/04/2016
f1_keywords:
- CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton::CreateInstance
- ATLCOM/ATL::CComClassFactorySingleton::m_spObj
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
ms.openlocfilehash: 71705d02140f0392a9ce023c64e7b4125c14443f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497403"
---
# <a name="ccomclassfactorysingleton-class"></a>CComClassFactorySingleton クラス

このクラスは、 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)から派生し、 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)を使用して1つのオブジェクトを構築します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
クラス。

`CComClassFactorySingleton`[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)から派生し、 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)を使用して1つのオブジェクトを構築します。 メソッドを呼び出す`CreateInstance`たびに、このオブジェクトに対してインターフェイスポインターがクエリされます。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComClassFactorySingleton:: CreateInstance](#createinstance)|インターフェイス`m_spObj`ポインターを照会します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CComClassFactorySingleton::m_spObj](#m_spobj)|によって`CComClassFactorySingleton`構築された [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) オブジェクト。|

## <a name="remarks"></a>Remarks

ATL オブジェクトは通常、 [CComCoClass](../../atl/reference/ccomcoclass-class.md)から派生することによってクラスファクトリを取得します。 このクラスには、既定のクラスファクトリ`CComClassFactory`として宣言するマクロ [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) が含まれています。 を使用`CComClassFactorySingleton`するには、オブジェクトのクラス定義で[DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton)マクロを指定します。 例えば:

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]

## <a name="inheritance-hierarchy"></a>継承階層

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)

`CComClassFactorySingleton`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="createinstance"></a>  CComClassFactorySingleton::CreateInstance

`QueryInterface` [M_spObj](#m_spobj)を通じてインターフェイスポインターを取得します。

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

##  <a name="m_spobj"></a>CComClassFactorySingleton::m_spObj

によって`CComClassFactorySingleton`構築された [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) オブジェクト。

```
CComPtr<IUnknown> m_spObj;
```

### <a name="remarks"></a>Remarks

[CreateInstance](#createinstance)メソッドを呼び出すたびに、このオブジェクトに対してインターフェイスポインターがクエリされます。

の現在の`m_spObj`形式は、以前のバージョンの ATL で動作し`CComClassFactorySingleton`ていた互換性に影響する変更点を示しています。 以前のバージョンで`CComClassFactorySingleton`は、サーバーの初期化時に、オブジェクトがクラスファクトリと同時に作成されていました。 Visual C++.net 2003 以降では、最初の要求でオブジェクトが遅延して作成されます。 この変更により、初期初期化に依存するプログラムでエラーが発生する可能性があります。

## <a name="see-also"></a>関連項目

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2 クラス](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComClassFactoryAutoThread クラス](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComObjectRootEx クラス](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
