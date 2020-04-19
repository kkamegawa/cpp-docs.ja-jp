---
title: IPropertyPage2Impl クラス
ms.date: 11/04/2016
f1_keywords:
- IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl::EditProperty
helpviewer_keywords:
- property pages
- IPropertyPage2 ATL implementation
- IPropertyPage2Impl class
ms.assetid: e89fbe90-203a-47f0-a5de-23616697e1ce
ms.openlocfilehash: 5ec6cb2f4fc6931a1bec429068b558bf7ac1906e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495608"
---
# <a name="ipropertypage2impl-class"></a>IPropertyPage2Impl クラス

このクラスは`IUnknown`を実装し、 [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)の既定の実装を継承します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template<class T>
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
から`IPropertyPage2Impl`派生したクラス。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[IPropertyPage2Impl:: EditProperty](#editproperty)|プロパティページがアクティブになったときにフォーカスを受け取るプロパティコントロールを指定します。 ATL 実装は E_NOTIMPL を返します。|

## <a name="remarks"></a>Remarks

[IPropertyPage2](/windows/win32/api/ocidl/nn-ocidl-ipropertypage2) インターフェイスは、`EditProperty` メソッドを追加して [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) を拡張します。 このメソッドを使用すると、クライアントは、プロパティページオブジェクト内の特定のプロパティを選択できます。

クラス`IPropertyPage2Impl`は、の E_NOTIMPL `IPropertyPage2::EditProperty`を単純に返します。 ただし、 [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)の既定の実装を継承し、 `IUnknown`デバッグビルドでダンプデバイスに情報を送信することによってを実装します。

プロパティページを作成する場合、通常、クラスはから`IPropertyPageImpl`派生します。 の`IPropertyPage2`追加サポートを提供するには、クラス定義を変更し`EditProperty` 、メソッドをオーバーライドします。

**関連記事**Atl[チュートリアル](../../atl/active-template-library-atl-tutorial.md)、 [atl プロジェクトの作成](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>継承階層

`IPropertyPage`

[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)

`IPropertyPage2Impl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlctl. h

##  <a name="editproperty"></a>  IPropertyPage2Impl::EditProperty

プロパティページがアクティブになったときにフォーカスを受け取るプロパティコントロールを指定します。

```
HRESULT EditProperty(DISPID dispID);
```

### <a name="return-value"></a>戻り値

E_NOTIMPL を返します。

### <a name="remarks"></a>Remarks

Windows SDK の「 [IPropertyPage2:: EditProperty](/windows/win32/api/ocidl/nf-ocidl-ipropertypage2-editproperty) 」を参照してください。

## <a name="see-also"></a>関連項目

[IPerPropertyBrowsingImpl クラス](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl クラス](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
