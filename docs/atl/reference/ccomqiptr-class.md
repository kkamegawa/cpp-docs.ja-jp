---
title: CComQIPtr クラス
ms.date: 11/04/2016
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
ms.openlocfilehash: 64716d945ffbc6802ec23fb47523464246065192
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258911"
---
# <a name="ccomqiptr-class"></a>CComQIPtr クラス

COM インターフェイス ポインターを管理するためのスマート ポインター クラスです。

## <a name="syntax"></a>構文

```
template<class T, const IID* piid= &__uuidof(T)>
class CComQIPtr: public CComPtr<T>
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
COM インターフェイスを格納するポインターの種類を指定します。

*piid*<br/>
ポインターの IID を*T*します。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CComQIPtr::CComQIPtr](#ccomqiptr)|コンストラクターです。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CComQIPtr::operator =](#operator_eq)|メンバーのポインターにポインターを割り当てます。|

## <a name="remarks"></a>Remarks

ATL を使用して`CComQIPtr`と[CComPtr](../../atl/reference/ccomptr-class.md)から派生する COM インターフェイス ポインターを管理する[CComPtrBase](../../atl/reference/ccomptrbase-class.md)します。 両方のクラスの呼び出しを通じてカウント自動参照を実行する`AddRef`と`Release`します。 オーバー ロードされた演算子は、ポインター演算を処理します。

## <a name="inheritance-hierarchy"></a>継承階層

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

[CComPtr](../../atl/reference/ccomptr-class.md)

`CComQIPtr`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcomcli.h

##  <a name="ccomqiptr"></a>  CComQIPtr::CComQIPtr

コンストラクターです。

```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```

### <a name="parameters"></a>パラメーター

*lp*<br/>
インターフェイス ポインターを初期化するために使用されます。

*T*<br/>
COM インターフェイスです。

*piid*<br/>
ポインターの IID を*T*します。

##  <a name="operator_eq"></a>  CComQIPtr::operator =

代入演算子です。

```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```

### <a name="parameters"></a>パラメーター

*lp*<br/>
インターフェイス ポインターを初期化するために使用されます。

*T*<br/>
COM インターフェイスです。

*piid*<br/>
ポインターの IID を*T*します。

### <a name="return-value"></a>戻り値

更新されたポインターを返します`CComQIPtr`オブジェクト。

## <a name="see-also"></a>関連項目

[CComPtr::CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)<br/>
[CComQIPtr::CComQIPtr](#ccomqiptr)<br/>
[CComPtrBase クラス](../../atl/reference/ccomptrbase-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)<br/>
[CComQIPtrElementTraits クラス](../../atl/reference/ccomqiptrelementtraits-class.md)
