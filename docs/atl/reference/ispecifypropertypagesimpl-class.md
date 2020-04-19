---
title: ISpecifyPropertyPagesImpl クラス
ms.date: 11/04/2016
f1_keywords:
- ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl::GetPages
helpviewer_keywords:
- property pages, CLSIDs associated with
- ISpecifyPropertyPages
- ISpecifyPropertyPagesImpl class
ms.assetid: 4e4b9795-b656-4d56-9b8c-85941e7731f9
ms.openlocfilehash: c201cf6d9d89ab1a6a8e888deee1be79e5770490
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495406"
---
# <a name="ispecifypropertypagesimpl-class"></a>ISpecifyPropertyPagesImpl クラス

このクラスは`IUnknown`を実装し、 [ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages)インターフェイスの既定の実装を提供します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template<class T>
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl
   : public ISpecifyPropertyPages
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
から`ISpecifyPropertyPagesImpl`派生したクラス。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[ISpecifyPropertyPagesImpl:: GetPages](#getpages)|UUID 値のカウントされた配列を塗りつぶします。 各 UUID は、オブジェクトのプロパティシートに表示できるいずれかのプロパティページの CLSID に対応します。|

## <a name="remarks"></a>Remarks

[ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages)インターフェイスを使用すると、クライアントは、オブジェクトでサポートされているプロパティページの clsid の一覧を取得できます。 クラス`ISpecifyPropertyPagesImpl`は、このインターフェイスの既定の実装を`IUnknown`提供し、デバッグビルドでダンプデバイスに情報を送信することによってを実装します。

> [!NOTE]
>  オブジェクトがプロパティページ`ISpecifyPropertyPages`をサポートしていない場合は、インターフェイスを公開しないでください。

**関連記事**Atl[チュートリアル](../../atl/active-template-library-atl-tutorial.md)、 [atl プロジェクトの作成](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>継承階層

`ISpecifyPropertyPages`

`ISpecifyPropertyPagesImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="getpages"></a>  ISpecifyPropertyPagesImpl::GetPages

[CAUUID](/windows/win32/api/ocidl/ns-ocidl-cauuid)構造体の配列に、オブジェクトのプロパティシートに表示できるプロパティページの clsid を設定します。

```
STDMETHOD(GetPages)(CAUUID* pPages);
```

### <a name="remarks"></a>Remarks

ATL では、オブジェクトのプロパティマップを使用して、各 CLSID を取得します。

Windows SDK の「 [ISpecifyPropertyPages:: GetPages](/windows/win32/api/ocidl/nf-ocidl-ispecifypropertypages-getpages) 」を参照してください。

## <a name="see-also"></a>関連項目

[IPropertyPageImpl クラス](../../atl/reference/ipropertypageimpl-class.md)<br/>
[IPerPropertyBrowsingImpl クラス](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
