---
title: IPropertyPageImpl クラス
ms.date: 11/04/2016
f1_keywords:
- IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::Activate
- ATLCTL/ATL::IPropertyPageImpl::Apply
- ATLCTL/ATL::IPropertyPageImpl::Deactivate
- ATLCTL/ATL::IPropertyPageImpl::GetPageInfo
- ATLCTL/ATL::IPropertyPageImpl::Help
- ATLCTL/ATL::IPropertyPageImpl::IsPageDirty
- ATLCTL/ATL::IPropertyPageImpl::Move
- ATLCTL/ATL::IPropertyPageImpl::SetDirty
- ATLCTL/ATL::IPropertyPageImpl::SetObjects
- ATLCTL/ATL::IPropertyPageImpl::SetPageSite
- ATLCTL/ATL::IPropertyPageImpl::Show
- ATLCTL/ATL::IPropertyPageImpl::TranslateAccelerator
- ATLCTL/ATL::IPropertyPageImpl::m_bDirty
- ATLCTL/ATL::IPropertyPageImpl::m_dwDocString
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpContext
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpFile
- ATLCTL/ATL::IPropertyPageImpl::m_dwTitle
- ATLCTL/ATL::IPropertyPageImpl::m_nObjects
- ATLCTL/ATL::IPropertyPageImpl::m_pPageSite
- ATLCTL/ATL::IPropertyPageImpl::m_ppUnk
- ATLCTL/ATL::IPropertyPageImpl::m_size
helpviewer_keywords:
- property pages
- IPropertyPage ATL implementation
- IPropertyPageImpl class
ms.assetid: f9b7c8b1-7a04-4eab-aa63-63efddb740fa
ms.openlocfilehash: 69842e77aecaa94be66432e5fbba437a6fa3c5a4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495576"
---
# <a name="ipropertypageimpl-class"></a>IPropertyPageImpl クラス

このクラスは`IUnknown`を実装し、 [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage)インターフェイスの既定の実装を提供します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template<class T>
class IPropertyPageImpl
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
から`IPropertyPageImpl`派生したクラス。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[IPropertyPageImpl::IPropertyPageImpl](#ipropertypageimpl)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[IPropertyPageImpl::Activate](#activate)|プロパティページのダイアログボックスウィンドウを作成します。|
|[IPropertyPageImpl::Apply](#apply)|によって`SetObjects`指定された基になるオブジェクトに、現在のプロパティページの値を適用します。 ATL 実装は S_OK を返します。|
|[IPropertyPageImpl::D eactivate](#deactivate)|で`Activate`作成されたウィンドウを破棄します。|
|[IPropertyPageImpl::GetPageInfo](#getpageinfo)|プロパティページに関する情報を取得します。|
|[IPropertyPageImpl::Help](#help)|プロパティページの Windows ヘルプを呼び出します。|
|[IPropertyPageImpl::IsPageDirty](#ispagedirty)|プロパティページがアクティブ化されてから変更されたかどうかを示します。|
|[IPropertyPageImpl:: Move](#move)|[プロパティページ] ダイアログボックスの位置とサイズを変更します。|
|[IPropertyPageImpl:: SetDirty](#setdirty)|プロパティページの状態を変更済みまたは変更なしとしてフラグを付けます。|
|[IPropertyPageImpl::SetObjects](#setobjects)|プロパティページに関連`IUnknown`付けられているオブジェクトのポインターの配列を提供します。 これらのオブジェクトは、の呼び出し`Apply`によって、現在のプロパティページの値を受け取ります。|
|[IPropertyPageImpl:: Set Ite](#setpagesite)|プロパティページにポインターを提供します。このとき、プロパティページはプロパティフレームと通信します。 `IPropertyPageSite`|
|[IPropertyPageImpl:: Show](#show)|[プロパティページ] ダイアログボックスを表示または非表示にします。|
|[IPropertyPageImpl::TranslateAccelerator](#translateaccelerator)|指定されたキー入力を処理します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[IPropertyPageImpl::m_bDirty](#m_bdirty)|プロパティページの状態が変更されたかどうかを指定します。|
|[IPropertyPageImpl::m_dwDocString](#m_dwdocstring)|プロパティページを説明するテキスト文字列に関連付けられているリソース識別子を格納します。|
|[IPropertyPageImpl::m_dwHelpContext](#m_dwhelpcontext)|プロパティページに関連付けられているヘルプトピックのコンテキスト識別子を格納します。|
|[IPropertyPageImpl::m_dwHelpFile](#m_dwhelpfile)|プロパティページを記述するヘルプファイルの名前に関連付けられているリソース識別子を格納します。|
|[IPropertyPageImpl::m_dwTitle](#m_dwtitle)|プロパティページのタブに表示されるテキスト文字列に関連付けられているリソース識別子を格納します。|
|[IPropertyPageImpl::m_nObjects](#m_nobjects)|プロパティページに関連付けられているオブジェクトの数を格納します。|
|[IPropertyPageImpl::m_pPageSite](#m_ppagesite)|プロパティページが`IPropertyPageSite`プロパティフレームと通信するときに使用するインターフェイスをポイントします。|
|[IPropertyPageImpl::m_ppUnk](#m_ppunk)|プロパティページに関連付け`IUnknown`られているオブジェクトへのポインターの配列を指します。|
|[IPropertyPageImpl::m_size](#m_size)|プロパティページのダイアログボックスの高さと幅をピクセル単位で格納します。|

## <a name="remarks"></a>Remarks

[IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage)インターフェイスを使用すると、オブジェクトは、プロパティシート内の特定のプロパティページを管理できます。 クラス`IPropertyPageImpl`は、このインターフェイスの既定の実装を`IUnknown`提供し、デバッグビルドでダンプデバイスに情報を送信することによってを実装します。

**関連記事**Atl[チュートリアル](../../atl/active-template-library-atl-tutorial.md)、 [atl プロジェクトの作成](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>継承階層

`IPropertyPage`

`IPropertyPageImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlctl. h

##  <a name="activate"></a>  IPropertyPageImpl::Activate

プロパティページのダイアログボックスウィンドウを作成します。

```
HRESULT Activate(
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```

### <a name="remarks"></a>Remarks

既定では、ダイアログボックスは、 *Bmodal*パラメーターの値に関係なく、常にモードレスです。

Windows SDK の「 [IPropertyPage:: Activate](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-activate) 」を参照してください。

##  <a name="apply"></a>  IPropertyPageImpl::Apply

によって`SetObjects`指定された基になるオブジェクトに、現在のプロパティページの値を適用します。

```
HRESULT Apply();
```

### <a name="return-value"></a>戻り値

S_OK を返します。

### <a name="remarks"></a>Remarks

Windows SDK の「 [IPropertyPage:: Apply](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-apply) 」を参照してください。

##  <a name="deactivate"></a>IPropertyPageImpl::D eactivate

[Activate](#activate)を使用して作成されたダイアログボックスウィンドウを破棄します。

```
HRESULT Deactivate();
```

### <a name="remarks"></a>Remarks

Windows SDK については、「 [IPropertyPage::D eactivate](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-deactivate) 」を参照してください。

##  <a name="getpageinfo"></a>  IPropertyPageImpl::GetPageInfo

*PPageInfo*構造体に、データメンバーに格納されている情報を格納します。

```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Remarks

`GetPageInfo`[m_dwDocString](#m_dwdocstring)、 [M_dwHelpFile](#m_dwhelpfile)、および[m_dwTitle](#m_dwtitle)に関連付けられている文字列リソースを読み込みます。

Windows SDK の「 [IPropertyPage:: GetPageInfo](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-getpageinfo) 」を参照してください。

##  <a name="help"></a>  IPropertyPageImpl::Help

プロパティページの Windows ヘルプを呼び出します。

```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IPropertyPage:: Help](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-help) 」を参照してください。

##  <a name="ipropertypageimpl"></a>  IPropertyPageImpl::IPropertyPageImpl

コンストラクターです。

```
IPropertyPageImpl();
```

### <a name="remarks"></a>Remarks

すべてのデータメンバーを初期化します。

##  <a name="ispagedirty"></a>  IPropertyPageImpl::IsPageDirty

プロパティページがアクティブ化されてから変更されたかどうかを示します。

```
HRESULT IsPageDirty(void);
```

### <a name="remarks"></a>Remarks

`IsPageDirty`アクティブ化されてからページが変更された場合は、S_OK を返します。

##  <a name="m_bdirty"></a>  IPropertyPageImpl::m_bDirty

プロパティページの状態が変更されたかどうかを指定します。

```
BOOL m_bDirty;
```

##  <a name="m_nobjects"></a>IPropertyPageImpl::m_nObjects

プロパティページに関連付けられているオブジェクトの数を格納します。

```
ULONG m_nObjects;
```

##  <a name="m_dwhelpcontext"></a>IPropertyPageImpl::m_dwHelpContext

プロパティページに関連付けられているヘルプトピックのコンテキスト識別子を格納します。

```
DWORD m_dwHelpContext;
```

##  <a name="m_dwdocstring"></a>  IPropertyPageImpl::m_dwDocString

プロパティページを説明するテキスト文字列に関連付けられているリソース識別子を格納します。

```
UINT m_dwDocString;
```

##  <a name="m_dwhelpfile"></a>IPropertyPageImpl::m_dwHelpFile

プロパティページを記述するヘルプファイルの名前に関連付けられているリソース識別子を格納します。

```
UINT m_dwHelpFile;
```

##  <a name="m_dwtitle"></a>IPropertyPageImpl::m_dwTitle

プロパティページのタブに表示されるテキスト文字列に関連付けられているリソース識別子を格納します。

```
UINT m_dwTitle;
```

##  <a name="m_ppagesite"></a>  IPropertyPageImpl::m_pPageSite

プロパティページがプロパティフレームと通信するときに使用される[IPropertyPageSite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite)インターフェイスをポイントします。

```
IPropertyPageSite* m_pPageSite;
```

##  <a name="m_ppunk"></a>IPropertyPageImpl::m_ppUnk

プロパティページに関連付け`IUnknown`られているオブジェクトへのポインターの配列を指します。

```
IUnknown** m_ppUnk;
```

##  <a name="m_size"></a>IPropertyPageImpl::m_size

プロパティページのダイアログボックスの高さと幅をピクセル単位で格納します。

```
SIZE m_size;
```

##  <a name="move"></a>  IPropertyPageImpl::Move

[プロパティページ] ダイアログボックスの位置とサイズを変更します。

```
HRESULT Move(LPCRECT pRect);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IPropertyPage:: Move](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-move) 」を参照してください。

##  <a name="setdirty"></a>  IPropertyPageImpl::SetDirty

*Bdirty*の値に応じて、プロパティページの状態を変更済みまたは変更なしとしてフラグを付けます。

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>パラメーター

*bDirty*<br/>
からTRUE の場合、プロパティページの状態は変更済みとしてマークされます。 それ以外の場合は、変更なしとしてマークされます。

### <a name="remarks"></a>Remarks

必要に応じ`SetDirty`て、プロパティページが変更されたことをフレームに通知します。

##  <a name="setobjects"></a>  IPropertyPageImpl::SetObjects

プロパティページに関連`IUnknown`付けられているオブジェクトのポインターの配列を提供します。

```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IPropertyPage:: SetObjects](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setobjects) 」を参照してください。

##  <a name="setpagesite"></a>  IPropertyPageImpl::SetPageSite

プロパティページに[IPropertyPageSite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite)ポインターを提供します。このポインターを使用して、プロパティページがプロパティフレームと通信します。

```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IPropertyPage:: Set ite](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setpagesite) 」を参照してください。

##  <a name="show"></a>  IPropertyPageImpl::Show

[プロパティページ] ダイアログボックスを表示または非表示にします。

```
HRESULT Show(UINT nCmdShow);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IPropertyPage:: Show](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-show) 」を参照してください。

##  <a name="translateaccelerator"></a>  IPropertyPageImpl::TranslateAccelerator

で`pMsg`指定されたキーストロークを処理します。

```
HRESULT TranslateAccelerator(MSG* pMsg);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IPropertyPage:: TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-translateaccelerator) 」を参照してください。

## <a name="see-also"></a>関連項目

[IPropertyPage2Impl クラス](../../atl/reference/ipropertypage2impl-class.md)<br/>
[IPerPropertyBrowsingImpl クラス](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl クラス](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
