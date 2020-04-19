---
title: IPerPropertyBrowsingImpl クラス
ms.date: 11/04/2016
f1_keywords:
- IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetDisplayString
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedStrings
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedValue
- ATLCTL/ATL::IPerPropertyBrowsingImpl::MapPropertyToPage
helpviewer_keywords:
- IPerPropertyBrowsingImpl class
- property pages, accessing information
- IPerPropertyBrowsing, ATL implementation
ms.assetid: 0b1a9be3-d242-4767-be69-663a21e4b728
ms.openlocfilehash: 263f6826ac921d864dee646ef063c8b456b00af1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495725"
---
# <a name="iperpropertybrowsingimpl-class"></a>IPerPropertyBrowsingImpl クラス

このクラスは`IUnknown`を実装し、クライアントがオブジェクトのプロパティページ内の情報にアクセスできるようにします。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```

template <class T>
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :
    public IPerPropertyBrowsing
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
から`IPerPropertyBrowsingImpl`派生したクラス。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[IPerPropertyBrowsingImpl::GetDisplayString](#getdisplaystring)|指定されたプロパティを記述する文字列を取得します。|
|[IPerPropertyBrowsingImpl:: Getpre未定義の文字列](#getpredefinedstrings)|指定したプロパティが受け入れることができる値に対応する文字列の配列を取得します。|
|[IPerPropertyBrowsingImpl:: Getpresettings 値](#getpredefinedvalue)|指定した DISPID によって識別されるプロパティの値を格納しているバリアント型を取得します。 DISPID は、から`GetPredefinedStrings`取得した文字列名に関連付けられています。 ATL 実装は E_NOTIMPL を返します。|
|[IPerPropertyBrowsingImpl::MapPropertyToPage](#mappropertytopage)|指定したプロパティに関連付けられているプロパティページの CLSID を取得します。|

## <a name="remarks"></a>Remarks

[Iperpropertybrowsing](/windows/win32/api/ocidl/nn-ocidl-iperpropertybrowsing)インターフェイスを使用すると、クライアントは、オブジェクトのプロパティページ内の情報にアクセスできます。 クラス`IPerPropertyBrowsingImpl`は、このインターフェイスの既定の実装を`IUnknown`提供し、デバッグビルドでダンプデバイスに情報を送信することによってを実装します。

> [!NOTE]
>  コンテナーアプリケーションとして Microsoft Access を使用している場合は、から`IPerPropertyBrowsingImpl`クラスを派生させる必要があります。 それ以外の場合、アクセスはコントロールを読み込みません。

**関連記事**Atl[チュートリアル](../../atl/active-template-library-atl-tutorial.md)、 [atl プロジェクトの作成](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>継承階層

`IPerPropertyBrowsing`

`IPerPropertyBrowsingImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlctl. h

##  <a name="getdisplaystring"></a>  IPerPropertyBrowsingImpl::GetDisplayString

指定されたプロパティを記述する文字列を取得します。

```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [Iperpropertybrowsing:: GetDisplayString](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getdisplaystring) 」を参照してください。

##  <a name="getpredefinedstrings"></a>IPerPropertyBrowsingImpl:: Getpre未定義の文字列

各配列に項目0を格納します。

```
STDMETHOD(GetPredefinedStrings)(
    DISPID dispID,
    CALPOLESTR* pCaStringsOut,
    CADWORD* pCaCookiesOut);
```

### <a name="return-value"></a>戻り値

ATL の[Getpre持つ値](#getpredefinedvalue)の実装では、E_NOTIMPL が返されます。

### <a name="remarks"></a>Remarks

Windows SDK の「 [Iperpropertybrowsing:: Getpreの文字列](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedstrings)」を参照してください。

##  <a name="getpredefinedvalue"></a>IPerPropertyBrowsingImpl:: Getpresettings 値

指定した DISPID によって識別されるプロパティの値を格納しているバリアント型を取得します。 DISPID は、から`GetPredefinedStrings`取得した文字列名に関連付けられています。

```
STDMETHOD(GetPredefinedValue)(
    DISPID dispID,
    DWORD dwCookie,
    VARIANT* pVarOut);
```

### <a name="return-value"></a>戻り値

E_NOTIMPL を返します。

### <a name="remarks"></a>Remarks

ATL による[Getprestrings](#getpredefinedstrings)の実装では、対応する文字列は取得されません。

Windows SDK の「 [Iperpropertybrowsing:: Getpreの値](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedvalue)」を参照してください。

##  <a name="mappropertytopage"></a>  IPerPropertyBrowsingImpl::MapPropertyToPage

指定したプロパティに関連付けられているプロパティページの CLSID を取得します。

```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```

### <a name="remarks"></a>Remarks

ATL では、オブジェクトのプロパティマップを使用してこの情報を取得します。

Windows SDK の「 [Iperpropertybrowsing:: MapPropertyToPage](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-mappropertytopage) 」を参照してください。

## <a name="see-also"></a>関連項目

[IPropertyPageImpl クラス](../../atl/reference/ipropertypageimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl クラス](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
