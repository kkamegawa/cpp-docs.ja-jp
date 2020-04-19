---
title: CPictureHolder クラス
ms.date: 11/04/2016
f1_keywords:
- CPictureHolder
- AFXCTL/CPictureHolder
- AFXCTL/CPictureHolder::CPictureHolder
- AFXCTL/CPictureHolder::CreateEmpty
- AFXCTL/CPictureHolder::CreateFromBitmap
- AFXCTL/CPictureHolder::CreateFromIcon
- AFXCTL/CPictureHolder::CreateFromMetafile
- AFXCTL/CPictureHolder::GetDisplayString
- AFXCTL/CPictureHolder::GetPictureDispatch
- AFXCTL/CPictureHolder::GetType
- AFXCTL/CPictureHolder::Render
- AFXCTL/CPictureHolder::SetPictureDispatch
- AFXCTL/CPictureHolder::m_pPict
helpviewer_keywords:
- CPictureHolder [MFC], CPictureHolder
- CPictureHolder [MFC], CreateEmpty
- CPictureHolder [MFC], CreateFromBitmap
- CPictureHolder [MFC], CreateFromIcon
- CPictureHolder [MFC], CreateFromMetafile
- CPictureHolder [MFC], GetDisplayString
- CPictureHolder [MFC], GetPictureDispatch
- CPictureHolder [MFC], GetType
- CPictureHolder [MFC], Render
- CPictureHolder [MFC], SetPictureDispatch
- CPictureHolder [MFC], m_pPict
ms.assetid: a4f59775-704a-41dd-b5bd-2e531c95127a
ms.openlocfilehash: 5386240114550826e4bf557b63310a91590afb55
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372882"
---
# <a name="cpictureholder-class"></a>CPictureHolder クラス

ユーザーがコントロールに画像を表示する画像のプロパティを実装します。

## <a name="syntax"></a>構文

```
class CPictureHolder
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CPictureHolder::CPictureHolder](#cpictureholder)|`CPictureHolder` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CPictureHolder::CreateEmpty](#createempty)|空の `CPictureHolder` オブジェクトを作成します。|
|[CPictureHolder::CreateFromBitmap](#createfrombitmap)|作成、`CPictureHolder`ビットマップからのオブジェクト。|
|[CPictureHolder::CreateFromIcon](#createfromicon)|作成、`CPictureHolder`アイコンからのオブジェクト。|
|[CPictureHolder::CreateFromMetafile](#createfrommetafile)|作成、`CPictureHolder`メタファイルからのオブジェクト。|
|[CPictureHolder::GetDisplayString](#getdisplaystring)|コントロール コンテナーのプロパティ ブラウザーに表示される文字列を取得します。|
|[CPictureHolder::GetPictureDispatch](#getpicturedispatch)|返します、`CPictureHolder`オブジェクトの`IDispatch`インターフェイス。|
|[CPictureHolder::GetType](#gettype)|通知するかどうか、`CPictureHolder`オブジェクトは、ビットマップ、メタファイル、またはアイコン。|
|[CPictureHolder::Render](#render)|画像を表示します。|
|[CPictureHolder::SetPictureDispatch](#setpicturedispatch)|セット、`CPictureHolder`オブジェクトの`IDispatch`インターフェイス。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CPictureHolder::m_pPict](#m_ppict)|画像オブジェクトへのポインター。|

## <a name="remarks"></a>Remarks

`CPictureHolder` 基本クラスはありません。

ストックの画像プロパティで、開発者は、ビットマップ、アイコン、または表示のメタファイルを指定できます。

カスタム picture プロパティの作成方法の詳細については、この記事を参照してください。 [MFC ActiveX コントロール。ActiveX コントロールにおけるピクチャの使用](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

`CPictureHolder`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxctl.h

##  <a name="cpictureholder"></a>  CPictureHolder::CPictureHolder

`CPictureHolder` オブジェクトを構築します。

```
CPictureHolder();
```

##  <a name="createempty"></a>  CPictureHolder::CreateEmpty

空を作成します。`CPictureHolder`オブジェクトおよびに接続し、`IPicture`インターフェイス。

```
BOOL CreateEmpty();
```

### <a name="return-value"></a>戻り値

オブジェクトが正常に作成された場合、0 以外の場合それ以外の場合 0 を返します。

##  <a name="createfrombitmap"></a>  CPictureHolder::CreateFromBitmap

オブジェクトを初期化するために、ビットマップを使用して、`CPictureHolder`します。

```
BOOL CreateFromBitmap(
    UINT idResource);

BOOL CreateFromBitmap(
    CBitmap* pBitmap,
    CPalette* pPal = NULL,
    BOOL bTransferOwnership = TRUE);

BOOL CreateFromBitmap(
    HBITMAP hbm,
    HPALETTE hpal = NULL,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>パラメーター

*idResource*<br/>
ビットマップ リソースのリソース ID。

*pBitmap*<br/>
ポインターを[CBitmap](../../mfc/reference/cbitmap-class.md)オブジェクト。

*pPal*<br/>
ポインターを[CPalette](../../mfc/reference/cpalette-class.md)オブジェクト。

*bTransferOwnership*<br/>
画像オブジェクトが、ビットマップ、およびパレット オブジェクトの所有権を持つかどうかを示します。

*hbm*<br/>
元のビットマップへのハンドル、`CPictureHolder`オブジェクトが作成されます。

*hpal*<br/>
ビットマップの描画に使用するパレットへのハンドルします。

### <a name="return-value"></a>戻り値

オブジェクトが正常に作成された場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

場合*bTransferOwnership*は TRUE、呼び出し元は、ビットマップを使用する必要がありますか、この呼び出しの後の任意の方法でパレット オブジェクトを返します。 場合*bTransferOwnership* false で、呼び出し元は、ビットマップ、およびパレット オブジェクトがオブジェクトの有効期間にわたって有効であることを確認します。

##  <a name="createfromicon"></a>  CPictureHolder::CreateFromIcon

画像内のオブジェクトを初期化するために、アイコンを使用して、`CPictureHolder`します。

```
BOOL CreateFromIcon(
    UINT idResource);

BOOL CreateFromIcon(
    HICON hIcon,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>パラメーター

*idResource*<br/>
ビットマップ リソースのリソース ID。

*hIcon*<br/>
元のアイコンへのハンドル、`CPictureHolder`オブジェクトが作成されます。

*bTransferOwnership*<br/>
画像オブジェクトが、icon オブジェクトの所有権を持つかどうかを示します。

### <a name="return-value"></a>戻り値

オブジェクトが正常に作成された場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

場合*bTransferOwnership*が true の場合、呼び出し元は、しない、この呼び出しが返された後に何らかの方法でアイコン オブジェクトを使用する必要があります。 場合*bTransferOwnership* false で、呼び出し元が責任を担う画像オブジェクトの有効期間にわたって、icon オブジェクトが有効にします。

##  <a name="createfrommetafile"></a>  CPictureHolder::CreateFromMetafile

画像内のオブジェクトを初期化するためにメタファイルを使用して、`CPictureHolder`します。

```
BOOL CreateFromMetafile(
    HMETAFILE hmf,
    int xExt,
    int yExt,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>パラメーター

*hmf*<br/>
作成するために使用するメタファイルのハンドル、`CPictureHolder`オブジェクト。

*xExt*<br/>
画像のエクステント x。

*yExt*<br/>
画像の Y の範囲。

*bTransferOwnership*<br/>
画像オブジェクトが、メタファイル オブジェクトの所有権を持つかどうかを示します。

### <a name="return-value"></a>戻り値

オブジェクトが正常に作成された場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

場合*bTransferOwnership*が true の場合、呼び出し元は、しない、この呼び出しが返された後に何らかの方法でメタファイル オブジェクトを使用する必要があります。 場合*bTransferOwnership* false で、呼び出し元が責任を担う画像オブジェクトの有効期間にわたってメタファイル オブジェクトが有効にします。

##  <a name="getdisplaystring"></a>  CPictureHolder::GetDisplayString

コンテナーのプロパティ ブラウザーに表示される文字列を取得します。

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>パラメーター

*strValue*<br/>
参照、 [CString](../../atl-mfc-shared/reference/cstringt-class.md)表示文字列を保持します。

### <a name="return-value"></a>戻り値

文字列が正常に取得される場合は 0 以外。それ以外の場合 0 を返します。

##  <a name="getpicturedispatch"></a>  CPictureHolder::GetPictureDispatch

この関数へのポインターを返します、`CPictureHolder`オブジェクトの`IPictureDisp`インターフェイス。

```
LPPICTUREDISP GetPictureDispatch();
```

### <a name="return-value"></a>戻り値

ポインター、`CPictureHolder`オブジェクトの`IPictureDisp`インターフェイス。

### <a name="remarks"></a>Remarks

呼び出し元が呼び出す必要があります`Release`を使い終わったらこのポインター。

##  <a name="gettype"></a>  CPictureHolder::GetType

図は、ビットマップ、メタファイル、またはアイコンかどうかを示します。

```
short GetType();
```

### <a name="return-value"></a>戻り値

画像の種類を示す値。 使用可能な値とその意味は次のとおりです。

|[値]|説明|
|-----------|-------------|
|PICTYPE_UNINITIALIZED|`CPictureHolder` オブジェクトが unititialized します。|
|PICTYPE_NONE|`CPictureHolder` オブジェクトが空です。|
|PICTYPE_BITMAP|画像は、ビットマップです。|
|PICTYPE_METAFILE|画像は、メタファイルです。|
|PICTYPE_ICON|画像は、アイコンです。|

##  <a name="m_ppict"></a>  CPictureHolder::m_pPict

ポインター、`CPictureHolder`オブジェクトの`IPicture`インターフェイス。

```
LPPICTURE m_pPict;
```

##  <a name="render"></a>  CPictureHolder::Render

によって参照される四角形に画像をレンダリング*rcRender*します。

```
void Render(
    CDC* pDC,
    const CRect& rcRender,
    const CRect& rcWBounds);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
画像がレンダリングされるディスプレイ コンテキストへのポインター。

*rcRender*<br/>
画像がレンダリングされる四角形。

*rcWBounds*<br/>
画像を表示するオブジェクトの外接する四角形を表す四角形。 コントロールの場合は、この四角形は、 *rcBounds*のオーバーライドに渡されるパラメーター[オーバライド](../../mfc/reference/colecontrol-class.md#ondraw)します。

##  <a name="setpicturedispatch"></a>  CPictureHolder::SetPictureDispatch

接続、`CPictureHolder`オブジェクトを`IPictureDisp`インターフェイス。

```
void SetPictureDispatch(LPPICTUREDISP pDisp);
```

### <a name="parameters"></a>パラメーター

*pDisp*<br/>
新しいポインター`IPictureDisp`インターフェイス。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[CFontHolder クラス](../../mfc/reference/cfontholder-class.md)
