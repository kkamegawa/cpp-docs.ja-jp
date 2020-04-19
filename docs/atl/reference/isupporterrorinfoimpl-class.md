---
title: ISupportErrorInfoImpl クラス
ms.date: 06/13/2019
f1_keywords:
- ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl::InterfaceSupportsErrorInfo
helpviewer_keywords:
- ISupportErrorInfo ATL implementation
- ISupportErrorInfoImpl class
- error information, ATL
ms.assetid: e33a4b11-a123-41cf-bcea-7b19743902af
ms.openlocfilehash: d5e7f087f6646940777ae8b2d2a4ea888fdd3593
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495375"
---
# <a name="isupporterrorinfoimpl-class"></a>ISupportErrorInfoImpl クラス

このクラスは、 [ISupportErrorInfo インターフェイス](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo)の既定の実装を提供し、1つのインターフェイスだけがオブジェクトに対してエラーを生成する場合に使用できます。

> [!IMPORTANT]
> このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```cpp
template<const IID* piid>
class ATL_NO_VTABLE ISupportErrorInfoImpl
   : public ISupportErrorInfo
```

### <a name="parameters"></a>パラメーター

*piid*<br/>
[IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)をサポートするインターフェイスの IID へのポインター。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|によって`riid`識別されるインターフェイスが[IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)インターフェイスをサポートするかどうかを示します。|

## <a name="remarks"></a>Remarks

[ISupportErrorInfo インターフェイス](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo)により、エラー情報をクライアントに返すことができます。 を使用`IErrorInfo`するオブジェクトは`ISupportErrorInfo`、を実装する必要があります。

クラス`ISupportErrorInfoImpl`は、の既定の`ISupportErrorInfo`実装を提供し、1つのインターフェイスだけがオブジェクトに対してエラーを生成する場合に使用できます。 例えば:

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>継承階層

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="interfacesupportserrorinfo"></a>  ISupportErrorInfoImpl::InterfaceSupportsErrorInfo

によって`riid`識別されるインターフェイスが[IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)インターフェイスをサポートするかどうかを示します。

```cpp
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [ISupportErrorInfo:: InterfaceSupportsErrorInfo](/windows/win32/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) 」を参照してください。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
