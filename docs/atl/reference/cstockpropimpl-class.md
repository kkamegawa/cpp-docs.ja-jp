---
title: CStockPropImpl クラス
ms.date: 05/06/2019
f1_keywords:
- CStockPropImpl
- ATLCTL/ATL::CStockPropImpl
- ATLCTL/ATL::get_Appearance
- ATLCTL/ATL::get_AutoSize
- ATLCTL/ATL::get_BackColor
- ATLCTL/ATL::get_BackStyle
- ATLCTL/ATL::get_BorderColor
- ATLCTL/ATL::get_BorderStyle
- ATLCTL/ATL::get_BorderVisible
- ATLCTL/ATL::get_BorderWidth
- ATLCTL/ATL::get_Caption
- ATLCTL/ATL::get_DrawMode
- ATLCTL/ATL::get_DrawStyle
- ATLCTL/ATL::get_DrawWidth
- ATLCTL/ATL::get_Enabled
- ATLCTL/ATL::get_FillColor
- ATLCTL/ATL::get_FillStyle
- ATLCTL/ATL::get_Font
- ATLCTL/ATL::get_ForeColor
- ATLCTL/ATL::get_HWND
- ATLCTL/ATL::get_MouseIcon
- ATLCTL/ATL::get_MousePointer
- ATLCTL/ATL::get_Picture
- ATLCTL/ATL::get_ReadyState
- ATLCTL/ATL::get_TabStop
- ATLCTL/ATL::get_Text
- ATLCTL/ATL::getvalid
- ATLCTL/ATL::get_Window
- ATLCTL/ATL::put_Appearance
- ATLCTL/ATL::put_AutoSize
- ATLCTL/ATL::put_BackColor
- ATLCTL/ATL::put_BackStyle
- ATLCTL/ATL::put_BorderColor
- ATLCTL/ATL::put_BorderStyle
- ATLCTL/ATL::put_BorderVisible
- ATLCTL/ATL::put_BorderWidth
- ATLCTL/ATL::put_Caption
- ATLCTL/ATL::put_DrawMode
- ATLCTL/ATL::put_DrawStyle
- ATLCTL/ATL::put_DrawWidth
- ATLCTL/ATL::put_Enabled
- ATLCTL/ATL::put_FillColor
- ATLCTL/ATL::put_FillStyle
- ATLCTL/ATL::put_Font
- ATLCTL/ATL::put_ForeColor
- ATLCTL/ATL::put_HWND
- ATLCTL/ATL::put_MouseIcon
- ATLCTL/ATL::put_MousePointer
- ATLCTL/ATL::put_Picture
- ATLCTL/ATL::put_ReadyState
- ATLCTL/ATL::put_TabStop
- ATLCTL/ATL::put_Text
- ATLCTL/ATL::putvalid
- ATLCTL/ATL::put_Window
- ATLCTL/ATL::putref_Font
- ATLCTL/ATL::putref_MouseIcon
- ATLCTL/ATL::putref_Picture
helpviewer_keywords:
- CStockPropImpl class
- controls [ATL], stock properties
- stock properties, ATL controls
ms.assetid: 45f11d7d-6580-4a0e-872d-3bc8b836cfda
ms.openlocfilehash: 29b4337679f05d780d3d6cd5de6bf6f889a6ea30
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496328"
---
# <a name="cstockpropimpl-class"></a>CStockPropImpl クラス

このクラスには、ストックプロパティ値をサポートするためのメソッドが用意されています。

> [!IMPORTANT]
> このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <
    class T, 
    class InterfaceName,
    const IID* piid = &_ATL_IIDOF(InterfaceName),
    const GUID* plibid = &CComModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0, 
    class tihclass = CcomTypeInfoHolder>
class ATL_NO_VTABLE CStockPropImpl :
    public IDispatchImpl<InterfaceName, piid, plibid, wMajor, wMinor, tihclass>
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
コントロールを実装し、から`CStockPropImpl`派生するクラス。

*InterfaceName*<br/>
ストックプロパティを公開するデュアルインターフェイス。

*piid*<br/>
の IID への`InterfaceName`ポインター。

*plibid*<br/>
の`InterfaceName`定義を格納しているタイプライブラリの LIBID へのポインター。

*wMajor*<br/>
タイプ ライブラリのメジャー バージョンです。 既定値は 1 です。

*wMinor*<br/>
タイプ ライブラリのマイナー バージョンです。 既定値は 0 です。

*tihclass*<br/>
*T*の型情報の管理に使用されるクラス。既定値は `CComTypeInfoHolder` です。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|||
|-|-|
|[get_Appearance](#get_appearance)|このメソッドを呼び出して、コントロールで使用されるペイントスタイルを取得します。たとえば、フラットまたは3D です。|
|[get_AutoSize](#get_autosize)|コントロールを他のサイズにすることができないかどうかを示すフラグの状態を取得するには、このメソッドを呼び出します。|
|[get_BackColor](#get_backcolor)|コントロールの背景色を取得するには、このメソッドを呼び出します。|
|[get_BackStyle](#get_backstyle)|コントロールの背景スタイル (透明または不透明) を取得するには、このメソッドを呼び出します。|
|[get_BorderColor](#get_bordercolor)|コントロールの境界線の色を取得するには、このメソッドを呼び出します。|
|[get_BorderStyle](#get_borderstyle)|このメソッドを呼び出して、コントロールの境界線スタイルを取得します。|
|[get_BorderVisible](#get_bordervisible)|コントロールの境界線が表示されているかどうかを示すフラグの状態を取得するには、このメソッドを呼び出します。|
|[get_BorderWidth](#get_borderwidth)|コントロールの境界線の幅 (ピクセル単位) を取得するには、このメソッドを呼び出します。|
|[get_Caption](#get_caption)|オブジェクトのキャプションに指定されたテキストを取得するには、このメソッドを呼び出します。|
|[get_DrawMode](#get_drawmode)|このメソッドを呼び出して、コントロールの描画モードを取得します。たとえば、[ペンの XOR] や [色の反転] などです。|
|[get_DrawStyle](#get_drawstyle)|このメソッドを呼び出して、コントロールの描画スタイル (実線、破線、点線など) を取得します。|
|[get_DrawWidth](#get_drawwidth)|このメソッドを呼び出して、コントロールの描画メソッドで使用される描画の幅 (ピクセル単位) を取得します。|
|[get_Enabled](#get_enabled)|コントロールが有効になっているかどうかを示すフラグの状態を取得するには、このメソッドを呼び出します。|
|[get_FillColor](#get_fillcolor)|コントロールの塗りつぶしの色を取得するには、このメソッドを呼び出します。|
|[get_FillStyle](#get_fillstyle)|このメソッドを呼び出して、コントロールの塗りつぶしのスタイル (実線、透明、クロスハッチなど) を取得します。|
|[get_Font](#get_font)|コントロールのフォントプロパティへのポインターを取得するには、このメソッドを呼び出します。|
|[get_ForeColor](#get_forecolor)|コントロールの前景色を取得するには、このメソッドを呼び出します。|
|[get_HWND](#get_hwnd)|コントロールに関連付けられているウィンドウハンドルを取得するには、このメソッドを呼び出します。|
|[get_MouseIcon](#get_mouseicon)|マウスがコントロールの上にあるときに表示されるグラフィック (アイコン、ビットマップ、またはメタファイル) の画像のプロパティを取得するには、このメソッドを呼び出します。|
|[get_MousePointer](#get_mousepointer)|マウスがコントロールの上にあるときに表示されるマウスポインターの種類 (矢印、十字、砂時計など) を取得するには、このメソッドを呼び出します。|
|[get_Picture](#get_picture)|表示するグラフィック (アイコン、ビットマップ、またはメタファイル) の picture プロパティへのポインターを取得するには、このメソッドを呼び出します。|
|[get_ReadyState](#get_readystate)|読み込みや読み込みなど、コントロールの準備完了状態を取得するには、このメソッドを呼び出します。|
|[get_TabStop](#get_tabstop)|コントロールがタブストップであるかどうかを示すフラグを取得するには、このメソッドを呼び出します。|
|[get_Text](#get_text)|コントロールで表示されるテキストを取得するには、このメソッドを呼び出します。|
|[getvalid](#get_valid)|コントロールが有効かどうかを示すフラグの状態を取得するには、このメソッドを呼び出します。|
|[get_Window](#get_window)|コントロールに関連付けられているウィンドウハンドルを取得するには、このメソッドを呼び出します。 [Cstockpropimpl:: get_HWND](#get_hwnd)と同じです。|
|[put_Appearance](#put_appearance)|このメソッドを呼び出して、コントロールで使用されるペイントスタイルを設定します (たとえば、フラットまたは 3D)。|
|[put_AutoSize](#put_autosize)|コントロールを他のサイズにすることができないかどうかを示すフラグの値を設定するには、このメソッドを呼び出します。|
|[put_BackColor](#put_backcolor)|コントロールの背景色を設定するには、このメソッドを呼び出します。|
|[put_BackStyle](#put_backstyle)|コントロールの背景スタイルを設定するには、このメソッドを呼び出します。|
|[put_BorderColor](#put_bordercolor)|コントロールの境界線の色を設定するには、このメソッドを呼び出します。|
|[put_BorderStyle](#put_borderstyle)|コントロールの境界線スタイルを設定するには、このメソッドを呼び出します。|
|[put_BorderVisible](#put_bordervisible)|コントロールの境界線が表示されているかどうかを示すフラグの値を設定するには、このメソッドを呼び出します。|
|[put_BorderWidth](#put_borderwidth)|コントロールの境界線の幅を設定するには、このメソッドを呼び出します。|
|[put_Caption](#put_caption)|コントロールと共に表示されるテキストを設定するには、このメソッドを呼び出します。|
|[put_DrawMode](#put_drawmode)|コントロールの描画モードを設定するには、このメソッドを呼び出します。たとえば、ペンや色の反転などです。|
|[put_DrawStyle](#put_drawstyle)|このメソッドを呼び出して、コントロールの描画スタイル (実線、破線、点線など) を設定します。|
|[put_DrawWidth](#put_drawwidth)|コントロールの描画メソッドによって使用される幅 (ピクセル単位) を設定するには、このメソッドを呼び出します。|
|[put_Enabled](#put_enabled)|コントロールが有効かどうかを示すフラグを設定するには、このメソッドを呼び出します。|
|[put_FillColor](#put_fillcolor)|コントロールの塗りつぶしの色を設定するには、このメソッドを呼び出します。|
|[put_FillStyle](#put_fillstyle)|このメソッドを呼び出して、コントロールの塗りつぶしのスタイル (実線、透明、クロスハッチなど) を設定します。|
|[put_Font](#put_font)|コントロールのフォントプロパティを設定するには、このメソッドを呼び出します。|
|[put_ForeColor](#put_forecolor)|コントロールの前景色を設定するには、このメソッドを呼び出します。|
|[put_HWND](#put_hwnd)|このメソッドは E_FAIL を返します。|
|[put_MouseIcon](#put_mouseicon)|マウスがコントロールの上にあるときに表示されるグラフィック (アイコン、ビットマップ、またはメタファイル) の画像のプロパティを設定するには、このメソッドを呼び出します。|
|[put_MousePointer](#put_mousepointer)|マウスがコントロールの上にあるときに表示されるマウスポインターの種類 (矢印、十字、砂時計など) を設定するには、このメソッドを呼び出します。|
|[put_Picture](#put_picture)|表示するグラフィック (アイコン、ビットマップ、またはメタファイル) の画像のプロパティを設定するには、このメソッドを呼び出します。|
|[put_ReadyState](#put_readystate)|このメソッドを呼び出して、読み込みや読み込みなど、コントロールの準備完了状態を設定します。|
|[put_TabStop](#put_tabstop)|コントロールがタブストップであるかどうかを示すフラグの値を設定するには、このメソッドを呼び出します。|
|[put_Text](#put_text)|コントロールで表示されるテキストを設定するには、このメソッドを呼び出します。|
|[putvalid](#put_valid)|コントロールが有効かどうかを示すフラグを設定するには、このメソッドを呼び出します。|
|[put_Window](#put_window)|このメソッド[:p は、ut_hwnd](#put_hwnd)を呼び出します。これは E_FAIL を返します。|
|[putref_Font](#putref_font)|このメソッドを呼び出して、参照カウントを使用してコントロールのフォントプロパティを設定します。|
|[putref_MouseIcon](#putref_mouseicon)|マウスがコントロールの上にあるときに表示されるグラフィック (アイコン、ビットマップ、またはメタファイル) の画像のプロパティを設定するには、このメソッドを呼び出します。|
|[putref_Picture](#putref_picture)|参照カウントを使用して、表示するグラフィック (アイコン、ビットマップ、またはメタファイル) の画像のプロパティを設定するには、このメソッドを呼び出します。|

## <a name="remarks"></a>Remarks

`CStockPropImpl`各ストックプロパティの**put**メソッドと**get**メソッドを提供します。 これらのメソッドは、各プロパティに関連付けられているデータメンバーを設定または取得するために必要なコードを提供し、任意のプロパティが変更されたときに、コンテナーとの通知および同期を行います。

Visual Studio では、ウィザードを使用してストックプロパティをサポートしています。 ストックプロパティをコントロールに追加する方法の詳細については、 [ATL チュートリアル](../../atl/active-template-library-atl-tutorial.md)を参照してください。

旧バージョンとの`CStockPropImpl`互換性のため`put_Window`に、はとを`put_HWND`それぞれ呼び出す`get_HWND`だけのメソッドとメソッドを公開`get_Window`します。 HWND は読み取り専用`put_HWND`プロパティであるため、の既定の実装では E_FAIL が返されます。

次のプロパティには、 **putref**実装もあります。

- フォント

- MouseIcon

- 画像

同じ3つのストックプロパティで、対応するデータメンバーが型`CComPtr`であるか、代入演算子によって正しいインターフェイス参照カウントを提供するその他のクラスである必要があります。

## <a name="inheritance-hierarchy"></a>継承階層

`T`

[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)

`CStockPropImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlctl. h

##  <a name="get_appearance"></a>  CStockPropImpl::get_Appearance

このメソッドを呼び出して、コントロールで使用されるペイントスタイルを取得します。たとえば、フラットまたは3D です。

```
HRESULT STDMETHODCALLTYPE get_Appearance(SHORT pnAppearance);
```

### <a name="parameters"></a>パラメーター

*pnAppearance*<br/>
コントロールの描画スタイルを受け取る変数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_autosize"></a>  CStockPropImpl::get_AutoSize

コントロールを他のサイズにすることができないかどうかを示すフラグの状態を取得するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE get_Autosize(VARIANT_BOOL* pbAutoSize);
```

### <a name="parameters"></a>パラメーター

*pbAutoSize*<br/>
フラグの状態を受け取る変数。 TRUE は、コントロールを他のサイズにすることはできないことを示します。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_backcolor"></a>  CStockPropImpl::get_BackColor

コントロールの背景色を取得するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE get_BackColor(OLE_COLOR* pclrBackColor);
```

### <a name="parameters"></a>パラメーター

*pclrBackColor*<br/>
コントロールの背景色を受け取る変数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_backstyle"></a>  CStockPropImpl::get_BackStyle

コントロールの背景スタイル (透明または不透明) を取得するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE get_BackStyle(LONG* pnBackStyle);
```

### <a name="parameters"></a>パラメーター

*pnBackStyle*<br/>
コントロールの背景スタイルを受け取る変数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_bordercolor"></a>  CStockPropImpl::get_BorderColor

コントロールの境界線の色を取得するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE get_BorderColor(OLE_COLOR* pclrBorderColor);
```

### <a name="parameters"></a>パラメーター

*pclrBorderColor*<br/>
コントロールの境界線の色を受け取る変数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_borderstyle"></a>  CStockPropImpl::get_BorderStyle

このメソッドを呼び出して、コントロールの境界線スタイルを取得します。

```
HRESULT STDMETHODCALLTYPE get_BorderStyle(LONG* pnBorderStyle);
```

### <a name="parameters"></a>パラメーター

*pnBorderStyle*<br/>
コントロールの境界線スタイルを受け取る変数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_bordervisible"></a>  CStockPropImpl::get_BorderVisible

コントロールの境界線が表示されているかどうかを示すフラグの状態を取得するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE get_BorderVisible(VARIANT_BOOL* pbBorderVisible);
```

### <a name="parameters"></a>パラメーター

*pbBorderVisible*<br/>
フラグの状態を受け取る変数。 TRUE は、コントロールの境界線が表示されることを示します。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_borderwidth"></a>  CStockPropImpl::get_BorderWidth

コントロールの境界線の幅を取得するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE get_BorderWidth(LONG* pnBorderWidth);
```

### <a name="parameters"></a>パラメーター

*pnBorderWidth*<br/>
コントロールの境界線の幅を受け取る変数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_caption"></a>  CStockPropImpl::get_Caption

オブジェクトのキャプションに指定されたテキストを取得するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE get_Caption(BSTR* pbstrCaption);
```

### <a name="parameters"></a>パラメーター

*pbstrCaption*<br/>
コントロールと共に表示されるテキスト。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_drawmode"></a>  CStockPropImpl::get_DrawMode

このメソッドを呼び出して、コントロールの描画モードを取得します。たとえば、[ペンの XOR] や [色の反転] などです。

```
HRESULT STDMETHODCALLTYPE get_DrawMode(LONG* pnDrawMode);
```

### <a name="parameters"></a>パラメーター

*pnDrawMode*<br/>
コントロールの描画モードを受け取る変数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_drawstyle"></a>  CStockPropImpl::get_DrawStyle

このメソッドを呼び出して、コントロールの描画スタイル (実線、破線、点線など) を取得します。

```
HRESULT STDMETHODCALLTYPE get_DrawStyle(LONG* pnDrawStyle);
```

### <a name="parameters"></a>パラメーター

*pnDrawStyle*<br/>
コントロールの描画スタイルを受け取る変数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_drawwidth"></a>  CStockPropImpl::get_DrawWidth

このメソッドを呼び出して、コントロールの描画メソッドで使用される描画の幅 (ピクセル単位) を取得します。

```
HRESULT STDMETHODCALLTYPE get_DrawWidth(LONG* pnDrawWidth);
```

### <a name="parameters"></a>パラメーター

*pnDrawWidth*<br/>
コントロールの幅の値をピクセル単位で受け取る変数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_enabled"></a>  CStockPropImpl::get_Enabled

コントロールが有効になっているかどうかを示すフラグの状態を取得するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE get_Enabled(VARIANT_BOOL* pbEnabled);
```

### <a name="parameters"></a>パラメーター

*pbEnabled*<br/>
フラグの状態を受け取る変数。 TRUE は、コントロールが有効であることを示します。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_fillcolor"></a>  CStockPropImpl::get_FillColor

コントロールの塗りつぶしの色を取得するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE get_FillColor(OLE_COLOR* pclrFillColor);
```

### <a name="parameters"></a>パラメーター

*pclrFillColor*<br/>
コントロールの塗りつぶしの色を受け取る変数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_fillstyle"></a>  CStockPropImpl::get_FillStyle

このメソッドを呼び出して、コントロールの塗りつぶしのスタイル (solid、transparent、crosshatched など) を取得します。

```
HRESULT STDMETHODCALLTYPE get_FillStyle(LONG* pnFillStyle);
```

### <a name="parameters"></a>パラメーター

*pnFillStyle*<br/>
コントロールの塗りつぶしスタイルを受け取る変数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_font"></a>  CStockPropImpl::get_Font

コントロールのフォントプロパティへのポインターを取得するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE get_Font(IFontDisp** ppFont);
```

### <a name="parameters"></a>パラメーター

*ppFont*<br/>
コントロールのフォントプロパティへのポインターを受け取る変数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_forecolor"></a>  CStockPropImpl::get_ForeColor

コントロールの前景色を取得するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE get_ForeColor(OLE_COLOR* pclrForeColor);
```

### <a name="parameters"></a>パラメーター

*pclrForeColor*<br/>
コントロールの前景色を受け取る変数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_hwnd"></a>CStockPropImpl:: get_HWND

コントロールに関連付けられているウィンドウハンドルを取得するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE get_HWND(LONG_PTR* phWnd);
```

### <a name="parameters"></a>パラメーター

*phWnd*<br/>
コントロールに関連付けられているウィンドウハンドル。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_mouseicon"></a>  CStockPropImpl::get_MouseIcon

マウスがコントロールの上にあるときに表示されるグラフィック (アイコン、ビットマップ、またはメタファイル) の画像のプロパティを取得するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE get_MouseIcon(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>パラメーター

*ppPicture*<br/>
グラフィックの picture プロパティへのポインターを受け取る変数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_mousepointer"></a>  CStockPropImpl::get_MousePointer

マウスがコントロールの上にあるときに表示されるマウスポインターの種類 (矢印、十字、砂時計など) を取得するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE get_MousePointer(LONG* pnMousePointer);
```

### <a name="parameters"></a>パラメーター

*pnMousePointer*<br/>
マウスポインターの種類を受け取る変数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_picture"></a>  CStockPropImpl::get_Picture

表示するグラフィック (アイコン、ビットマップ、またはメタファイル) の picture プロパティへのポインターを取得するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE get_Picture(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>パラメーター

*ppPicture*<br/>
画像のプロパティへのポインターを受け取る変数。 詳細については、「 [IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) 」を参照してください。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_readystate"></a>  CStockPropImpl::get_ReadyState

読み込みや読み込みなど、コントロールの準備完了状態を取得するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE get_ReadyState(LONG* pnReadyState);
```

### <a name="parameters"></a>パラメーター

*pnReadyState*<br/>
コントロールの準備完了状態を受け取る変数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_tabstop"></a>  CStockPropImpl::get_TabStop

コントロールがタブストップであるかどうかを示すフラグの状態を取得するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE get_TabStop(VARIANT_BOOL* pbTabStop);
```

### <a name="parameters"></a>パラメーター

*pbTabStop*<br/>
フラグの状態を受け取る変数。 TRUE は、コントロールがタブストップであることを示します。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_text"></a>  CStockPropImpl::get_Text

コントロールで表示されるテキストを取得するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE get_Text(BSTR* pbstrText);
```

### <a name="parameters"></a>パラメーター

*pbstrText*<br/>
コントロールと共に表示されるテキスト。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_valid"></a>CStockPropImpl:: getvalid

コントロールが有効かどうかを示すフラグの状態を取得するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL* pbValid);
```

### <a name="parameters"></a>パラメーター

*pbValid*<br/>
フラグの状態を受け取る変数。 TRUE は、コントロールが有効であることを示します。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="get_window"></a>  CStockPropImpl::get_Window

コントロールに関連付けられているウィンドウハンドルを取得するには、このメソッドを呼び出します。 [Cstockpropimpl:: get_HWND](#get_hwnd)と同じです。

```
HRESULT STDMETHODCALLTYPE get_Window(LONG_PTR* phWnd);
```

### <a name="parameters"></a>パラメーター

*phWnd*<br/>
コントロールに関連付けられているウィンドウハンドル。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_appearance"></a>  CStockPropImpl::put_Appearance

このメソッドを呼び出して、コントロールで使用されるペイントスタイルを設定します (たとえば、フラットまたは 3D)。

```
HRESULT STDMETHODCALLTYPE put_Appearance(SHORT nAppearance);
```

### <a name="parameters"></a>パラメーター

*nAppearance*<br/>
コントロールによって使用される新しい描画スタイル。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_autosize"></a>  CStockPropImpl::put_AutoSize

コントロールを他のサイズにすることができないかどうかを示すフラグの値を設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE put_AutoSize(VARIANT_BOOL bAutoSize,);
```

### <a name="parameters"></a>パラメーター

*bAutoSize*<br/>
コントロールを他のサイズにすることができない場合は TRUE。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_backcolor"></a>  CStockPropImpl::put_BackColor

コントロールの背景色を設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE put_BackColor(OLE_COLOR clrBackColor);
```

### <a name="parameters"></a>パラメーター

*clrBackColor*<br/>
新しいコントロールの背景色。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_backstyle"></a>  CStockPropImpl::put_BackStyle

コントロールの背景スタイルを設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE put_BackStyle(LONG nBackStyle);
```

### <a name="parameters"></a>パラメーター

*nBackStyle*<br/>
新しいコントロールの背景スタイル。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_bordercolor"></a>  CStockPropImpl::put_BorderColor

コントロールの境界線の色を設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE put_BorderColor(OLE_COLOR clrBorderColor);
```

### <a name="parameters"></a>パラメーター

*clrBorderColor*<br/>
新しい境界線の色。 OLE_COLOR データ型は、内部的には32ビット長整数として表現されます。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_borderstyle"></a>  CStockPropImpl::put_BorderStyle

コントロールの境界線スタイルを設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE put_BorderStyle(LONG nBorderStyle);
```

### <a name="parameters"></a>パラメーター

*nBorderStyle*<br/>
新しい罫線のスタイル。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_bordervisible"></a>  CStockPropImpl::put_BorderVisible

コントロールの境界線が表示されているかどうかを示すフラグの値を設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE put_BorderVisible(VARIANT_BOOL bBorderVisible);
```

### <a name="parameters"></a>パラメーター

*bBorderVisible*<br/>
境界線が表示される場合は TRUE。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_borderwidth"></a>  CStockPropImpl::put_BorderWidth

コントロールの境界線の幅を設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE put_BorderWidth(LONG nBorderWidth);
```

### <a name="parameters"></a>パラメーター

*nBorderWidth*<br/>
コントロールの境界線の新しい幅。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_caption"></a>  CStockPropImpl::put_Caption

コントロールと共に表示されるテキストを設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE put_Caption(BSTR bstrCaption);
```

### <a name="parameters"></a>パラメーター

*bstrCaption*<br/>
コントロールと共に表示されるテキスト。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_drawmode"></a>CStockPropImpl::p ut_DrawMode

コントロールの描画モードを設定するには、このメソッドを呼び出します。たとえば、ペンや色の反転などです。

```
HRESULT STDMETHODCALLTYPE put_DrawMode(LONG nDrawMode);
```

### <a name="parameters"></a>パラメーター

*nDrawMode*<br/>
コントロールの新しい描画モード。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_drawstyle"></a>CStockPropImpl::p ut_DrawStyle

このメソッドを呼び出して、コントロールの描画スタイル (実線、破線、点線など) を設定します。

```
HRESULT STDMETHODCALLTYPE put_DrawStyle(LONG pnDrawStyle);
```

### <a name="parameters"></a>パラメーター

*nDrawStyle*<br/>
コントロールの新しい描画スタイル。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_drawwidth"></a>  CStockPropImpl::put_DrawWidth

コントロールの描画メソッドによって使用される幅 (ピクセル単位) を設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE put_DrawWidth(LONG nDrawWidth);
```

### <a name="parameters"></a>パラメーター

*nDrawWidth*<br/>
コントロールの描画メソッドによって使用される新しい幅。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_enabled"></a>  CStockPropImpl::put_Enabled

コントロールが有効かどうかを示すフラグの値を設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE put_Enabled(VARIANT_BOOL bEnabled);
```

### <a name="parameters"></a>パラメーター

*bEnabled*<br/>
コントロールが有効な場合は TRUE。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_fillcolor"></a>  CStockPropImpl::put_FillColor

コントロールの塗りつぶしの色を設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE put_FillColor(OLE_COLOR clrFillColor);
```

### <a name="parameters"></a>パラメーター

*clrFillColor*<br/>
コントロールの新しい塗りつぶしの色。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_fillstyle"></a>CStockPropImpl::p ut_FillStyle

このメソッドを呼び出して、コントロールの塗りつぶしのスタイル (実線、透明、クロスハッチなど) を設定します。

```
HRESULT STDMETHODCALLTYPE put_FillStyle(LONG nFillStyle);
```

### <a name="parameters"></a>パラメーター

*nFillStyle*<br/>
コントロールの新しい塗りつぶしスタイル。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_font"></a>  CStockPropImpl::put_Font

コントロールのフォントプロパティを設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE put_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>パラメーター

*pFont*<br/>
コントロールのフォントプロパティへのポインター。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_forecolor"></a>  CStockPropImpl::put_ForeColor

コントロールの前景色を設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE put_ForeColor(OLE_COLOR clrForeColor);
```

### <a name="parameters"></a>パラメーター

*clrForeColor*<br/>
コントロールの新しい前景色。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_hwnd"></a>CStockPropImpl::p ut_HWND

このメソッドは E_FAIL を返します。

```
HRESULT STDMETHODCALLTYPE put_HWND(LONG_PTR /* hWnd */);
```

### <a name="parameters"></a>パラメーター

*hWnd*<br/>
予約済み。

### <a name="return-value"></a>戻り値

E_FAIL を返します。

### <a name="remarks"></a>Remarks

ウィンドウハンドルは読み取り専用の値です。

##  <a name="put_mouseicon"></a>  CStockPropImpl::put_MouseIcon

マウスがコントロールの上にあるときに表示されるグラフィック (アイコン、ビットマップ、またはメタファイル) の画像のプロパティを設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE put_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>パラメーター

*pPicture*<br/>
グラフィックのピクチャプロパティへのポインター。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_mousepointer"></a>  CStockPropImpl::put_MousePointer

マウスがコントロールの上にあるときに表示されるマウスポインターの種類 (矢印、十字、砂時計など) を設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE put_MousePointer(LONG nMousePointer);
```

### <a name="parameters"></a>パラメーター

*nMousePointer*<br/>
マウスポインターの種類。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_picture"></a>  CStockPropImpl::put_Picture

表示するグラフィック (アイコン、ビットマップ、またはメタファイル) の画像のプロパティを設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE put_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>パラメーター

*pPicture*<br/>
画像のプロパティへのポインター。 詳細については、「 [IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) 」を参照してください。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_readystate"></a>  CStockPropImpl::put_ReadyState

このメソッドを呼び出して、読み込みや読み込みなど、コントロールの準備完了状態を設定します。

```
HRESULT STDMETHODCALLTYPE put_ReadyState(LONG nReadyState);
```

### <a name="parameters"></a>パラメーター

*nReadyState*<br/>
コントロールの準備完了状態。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_tabstop"></a>  CStockPropImpl::put_TabStop

コントロールがタブストップであるかどうかを示すフラグを設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE put_TabStop(VARIANT_BOOL bTabStop);
```

### <a name="parameters"></a>パラメーター

*bTabStop*<br/>
コントロールがタブストップの場合は TRUE。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_text"></a>  CStockPropImpl::put_Text

コントロールで表示されるテキストを設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE put_Text(BSTR bstrText);
```

### <a name="parameters"></a>パラメーター

*bstrText*<br/>
コントロールと共に表示されるテキスト。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_valid"></a>CStockPropImpl::p utvalid

コントロールが有効かどうかを示すフラグを設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL bValid);
```

### <a name="parameters"></a>パラメーター

*bValid*<br/>
コントロールが有効な場合は TRUE。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="put_window"></a>  CStockPropImpl::put_Window

このメソッド[:p は、ut_hwnd](#put_hwnd)を呼び出します。これは E_FAIL を返します。

```
HRESULT STDMETHODCALLTYPE put_Window(LONG_PTR hWnd);
```

### <a name="parameters"></a>パラメーター

*hWnd*<br/>
ウィンドウ ハンドル。

### <a name="return-value"></a>戻り値

E_FAIL を返します。

### <a name="remarks"></a>Remarks

ウィンドウハンドルは読み取り専用の値です。

##  <a name="putref_font"></a>  CStockPropImpl::putref_Font

このメソッドを呼び出して、参照カウントを使用してコントロールのフォントプロパティを設定します。

```
HRESULT STDMETHODCALLTYPE putref_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>パラメーター

*pFont*<br/>
コントロールのフォントプロパティへのポインター。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

[Cstockpropimpl::P ut_font](#put_font)と同じですが、参照カウントが使用されています。

##  <a name="putref_mouseicon"></a>  CStockPropImpl::putref_MouseIcon

マウスがコントロールの上にあるときに表示されるグラフィック (アイコン、ビットマップ、またはメタファイル) の画像のプロパティを設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE putref_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>パラメーター

*pPicture*<br/>
グラフィックのピクチャプロパティへのポインター。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

[Cstockpropimpl::P ut_mouseicon](#put_mouseicon)と同じですが、参照カウントが使用されています。

##  <a name="putref_picture"></a>  CStockPropImpl::putref_Picture

参照カウントを使用して、表示するグラフィック (アイコン、ビットマップ、またはメタファイル) の画像のプロパティを設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE putref_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>パラメーター

*pPicture*<br/>
画像のプロパティへのポインター。 詳細については、「 [IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) 」を参照してください。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

[Cstockpropimpl::P ut_picture](#put_picture)と同じですが、参照カウントが使用されています。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)<br/>
[IDispatchImpl クラス](../../atl/reference/idispatchimpl-class.md)
