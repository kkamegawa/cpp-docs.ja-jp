---
title: IAxWinAmbientDispatch インターフェイス
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatch
- ATLIFACE/ATL::IAxWinAmbientDispatch
- ATLIFACE/ATL::get_AllowContextMenu
- ATLIFACE/ATL::get_AllowShowUI
- ATLIFACE/ATL::get_AllowWindowlessActivation
- ATLIFACE/ATL::get_BackColor
- ATLIFACE/ATL::get_DisplayAsDefault
- ATLIFACE/ATL::get_DocHostDoubleClickFlags
- ATLIFACE/ATL::get_DocHostFlags
- ATLIFACE/ATL::get_Font
- ATLIFACE/ATL::get_ForeColor
- ATLIFACE/ATL::get_LocaleID
- ATLIFACE/ATL::get_MessageReflect
- ATLIFACE/ATL::get_OptionKeyPath
- ATLIFACE/ATL::get_ShowGrabHandles
- ATLIFACE/ATL::get_ShowHatching
- ATLIFACE/ATL::get_UserMode
- ATLIFACE/ATL::put_AllowContextMenu
- ATLIFACE/ATL::put_AllowShowUI
- ATLIFACE/ATL::put_AllowWindowlessActivation
- ATLIFACE/ATL::put_BackColor
- ATLIFACE/ATL::put_DisplayAsDefault
- ATLIFACE/ATL::put_DocHostDoubleClickFlags
- ATLIFACE/ATL::put_DocHostFlags
- ATLIFACE/ATL::put_Font
- ATLIFACE/ATL::put_ForeColor
- ATLIFACE/ATL::put_LocaleID
- ATLIFACE/ATL::put_MessageReflect
- ATLIFACE/ATL::put_OptionKeyPath
- ATLIFACE/ATL::put_UserMode
helpviewer_keywords:
- IAxWinAmbientDispatch interface
ms.assetid: 55ba6f7b-7a3c-4792-ae47-c8a84b683ca9
ms.openlocfilehash: 85a8f1d41c6c54f94b500807a1e4ca504206f56a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276160"
---
# <a name="iaxwinambientdispatch-interface"></a>IAxWinAmbientDispatch インターフェイス

このインターフェイスは、ホストされるコントロールまたはコンテナーの特性を指定するためのメソッドを提供します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
interface IAxWinAmbientDispatch : IDispatch
```

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[get_AllowContextMenu](#get_allowcontextmenu)|`AllowContextMenu`プロパティは、ホストされるコントロールが、独自のコンテキスト メニューを表示できるかどうかを指定します。|
|[get_AllowShowUI](#get_allowshowui)|`AllowShowUI`プロパティは、ホストされるコントロールが、独自のユーザー インターフェイスを表示できるかどうかを指定します。|
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|`AllowWindowlessActivation`プロパティは、コンテナーでウィンドウなしのアクティベーションを許可するかどうかを指定します。|
|[get_BackColor](#get_backcolor)|`BackColor`プロパティをコンテナーのアンビエント背景色を指定します。|
|[get_DisplayAsDefault](#get_displayasdefault)|`DisplayAsDefault` アンビエント プロパティを調べるかどうかは、既定のコントロールのコントロールを許可します。|
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|`DocHostDoubleClickFlags`プロパティは、ダブルクリックに応答で実行される操作を指定します。|
|[get_DocHostFlags](#get_dochostflags)|`DocHostFlags`プロパティが、そのホスト オブジェクトのユーザー インターフェイス機能を指定します。|
|[get_Font](#get_font)|`Font`プロパティは、コンテナーのアンビエント フォントを指定します。|
|[get_ForeColor](#get_forecolor)|`ForeColor`プロパティをコンテナーのアンビエント前景色を指定します。|
|[get_LocaleID](#get_localeid)|`LocaleID`プロパティをコンテナーのアンビエント ロケール ID を指定します。|
|[get_MessageReflect](#get_messagereflect)|`MessageReflect`アンビエント プロパティは、コンテナーがホストされているコントロールへのメッセージを反映するかどうかを指定します。|
|[get_OptionKeyPath](#get_optionkeypath)|`OptionKeyPath`プロパティをユーザー設定をレジストリ キーのパスを指定します。|
|[get_ShowGrabHandles](#get_showgrabhandles)|`ShowGrabHandles`アンビエント プロパティでは、コントロールを調べるかどうかは、グラブ ハンドルを描画、自体する必要があります。|
|[get_ShowHatching](#get_showhatching)|`ShowHatching`アンビエント プロパティでは、コントロールを調べるかどうかハッチ自体を描画する必要があります。|
|[get_UserMode](#get_usermode)|`UserMode`プロパティをコンテナーのアンビエント ユーザー モードを指定します。|
|[put_AllowContextMenu](#put_allowcontextmenu)|`AllowContextMenu`プロパティは、ホストされるコントロールが、独自のコンテキスト メニューを表示できるかどうかを指定します。|
|[put_AllowShowUI](#put_allowshowui)|`AllowShowUI`プロパティは、ホストされるコントロールが、独自のユーザー インターフェイスを表示できるかどうかを指定します。|
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|`AllowWindowlessActivation`プロパティは、コンテナーでウィンドウなしのアクティベーションを許可するかどうかを指定します。|
|[put_BackColor](#put_backcolor)|`BackColor`プロパティをコンテナーのアンビエント背景色を指定します。|
|[put_DisplayAsDefault](#put_displayasdefault)|`DisplayAsDefault` アンビエント プロパティを調べるかどうかは、既定のコントロールのコントロールを許可します。|
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|`DocHostDoubleClickFlags`プロパティは、ダブルクリックに応答で実行される操作を指定します。|
|[put_DocHostFlags](#put_dochostflags)|`DocHostFlags`プロパティが、そのホスト オブジェクトのユーザー インターフェイス機能を指定します。|
|[put_Font](#put_font)|`Font`プロパティは、コンテナーのアンビエント フォントを指定します。|
|[put_ForeColor](#put_forecolor)|`ForeColor`プロパティをコンテナーのアンビエント前景色を指定します。|
|[put_LocaleID](#put_localeid)|`LocaleID`プロパティをコンテナーのアンビエント ロケール ID を指定します。|
|[put_MessageReflect](#put_messagereflect)|`MessageReflect`アンビエント プロパティは、コンテナーがホストされているコントロールへのメッセージを反映するかどうかを指定します。|
|[put_OptionKeyPath](#put_optionkeypath)|`OptionKeyPath`プロパティをユーザー設定をレジストリ キーのパスを指定します。|
|[put_UserMode](#put_usermode)|`UserMode`プロパティをコンテナーのアンビエント ユーザー モードを指定します。|

## <a name="remarks"></a>Remarks

このインターフェイスは、オブジェクトのホスト、ATL の ActiveX コントロールによって公開されます。 ホストされるコントロールに使用可能なアンビエント プロパティを設定するか、コンテナーの動作の他の側面を指定するこのインターフェイスでメソッドを呼び出します。 によって提供されるプロパティを補足する`IAxWinAmbientDispatch`を使用して、 [IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)します。

<xref:System.Windows.Forms.AxHost> に関する型情報を読み込んでみます`IAxWinAmbientDispatch`と`IAxWinAmbientDispatchEx`コードを含むタイプ ライブラリから。

ATL90.dll にリンクしている場合**AXHost**は DLL にタイプ ライブラリから型情報を読み込みます。

参照してください[ActiveX コントロール ATL を使用しての AXHost をホストしている](../../atl/hosting-activex-controls-using-atl-axhost.md)の詳細。

## <a name="requirements"></a>必要条件

このインターフェイスの定義は、次の表に示すようにさまざまな形式で使用できます。

|定義の種類|ファイル|
|---------------------|----------|
|IDL|atliface.idl|
|タイプ ライブラリ|ATL.dll|
|C++|atliface.h (ATLBase.h にも含まれています)|

##  <a name="get_allowcontextmenu"></a>  IAxWinAmbientDispatch::get_AllowContextMenu

`AllowContextMenu`プロパティは、ホストされるコントロールが、独自のコンテキスト メニューを表示できるかどうかを指定します。

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>パラメーター

*pbAllowContextMenu*<br/>
[out]このプロパティの現在の値を受け取る変数のアドレス。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、このプロパティの既定値に VARIANT_TRUE を使用します。

##  <a name="get_allowshowui"></a>  IAxWinAmbientDispatch::get_AllowShowUI

`AllowShowUI`プロパティは、ホストされるコントロールが、独自のユーザー インターフェイスを表示できるかどうかを指定します。

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>パラメーター

*pbAllowShowUI*<br/>
[out]このプロパティの現在の値を受け取る変数のアドレス。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、このプロパティの既定値として VARIANT_FALSE を使用します。

##  <a name="get_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::get_AllowWindowlessActivation

`AllowWindowlessActivation`プロパティは、コンテナーでウィンドウなしのアクティベーションを許可するかどうかを指定します。

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>パラメーター

*pbAllowWindowless*<br/>
[out]このプロパティの現在の値を受け取る変数のアドレス。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、このプロパティの既定値に VARIANT_TRUE を使用します。

##  <a name="get_backcolor"></a>  IAxWinAmbientDispatch::get_BackColor

`BackColor`プロパティをコンテナーのアンビエント背景色を指定します。

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>パラメーター

*pclrBackground*<br/>
[out]このプロパティの現在の値を受け取る変数のアドレス。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、COLOR_BTNFACE または COLOR_WINDOW を (ホスト ウィンドウの親がダイアログ ボックスかどうか) に応じて、このプロパティの既定値として使用します。

##  <a name="get_displayasdefault"></a>  IAxWinAmbientDispatch::get_DisplayAsDefault

`DisplayAsDefault` アンビエント プロパティを調べるかどうかは、既定のコントロールのコントロールを許可します。

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>パラメーター

*pbDisplayAsDefault*<br/>
[out]このプロパティの現在の値を受け取る変数のアドレス。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、このプロパティの既定値として VARIANT_FALSE を使用します。

##  <a name="get_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::get_DocHostDoubleClickFlags

`DocHostDoubleClickFlags`プロパティは、ダブルクリックに応答で実行される操作を指定します。

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>パラメーター

*pdwDocHostDoubleClickFlags*<br/>
[out]このプロパティの現在の値を受け取る変数のアドレス。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、このプロパティの既定値として DOCHOSTUIDBLCLK_DEFAULT を使用します。

##  <a name="get_dochostflags"></a>  IAxWinAmbientDispatch::get_DocHostFlags

`DocHostFlags`プロパティが、そのホスト オブジェクトのユーザー インターフェイス機能を指定します。

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>パラメーター

*pdwDocHostFlags*<br/>
[out]このプロパティの現在の値を受け取る変数のアドレス。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、このプロパティの既定値として DOCHOSTUIFLAG_NO3DBORDER を使用します。

##  <a name="get_font"></a>  IAxWinAmbientDispatch::get_Font

`Font`プロパティは、コンテナーのアンビエント フォントを指定します。

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>パラメーター

*pFont*<br/>
[out]アドレス、`IFontDisp`インターフェイス ポインターがこのプロパティの現在の値を受信するために使用します。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、このプロパティの既定値として既定の GUI フォントまたはシステム フォントを使用します。

##  <a name="get_forecolor"></a>  IAxWinAmbientDispatch::get_ForeColor

`ForeColor`プロパティをコンテナーのアンビエント前景色を指定します。

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>パラメーター

*pclrForeground*<br/>
[out]このプロパティの現在の値を受け取る変数のアドレス。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、このプロパティの既定値としてシステム ウィンドウのテキストの色を使用します。

##  <a name="get_localeid"></a>  IAxWinAmbientDispatch::get_LocaleID

`LocaleID`プロパティをコンテナーのアンビエント ロケール ID を指定します。

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>パラメーター

*plcidLocaleID*<br/>
[out]このプロパティの現在の値を受け取る変数のアドレス。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、このプロパティの既定値として、ユーザーの既定のロケールを使用します。

この方法では、アンビエント LocalID を見つけることができます、つまり、プログラムの LocaleID コントロールで使用されています。 ロケール Id がわかれば、リソース ファイルまたはサテライト DLL からなどロケール固有のキャプションを読み込むためのコード、エラー メッセージのテキストを呼び出すことができます。

##  <a name="get_messagereflect"></a>  IAxWinAmbientDispatch::get_MessageReflect

`MessageReflect`アンビエント プロパティは、コンテナーがホストされているコントロールへのメッセージを反映するかどうかを指定します。

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>パラメーター

*pbMessageReflect*<br/>
[out]このプロパティの現在の値を受け取る変数のアドレス。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、このプロパティの既定値に VARIANT_TRUE を使用します。

##  <a name="get_optionkeypath"></a>  IAxWinAmbientDispatch::get_OptionKeyPath

`OptionKeyPath`プロパティをユーザー設定をレジストリ キーのパスを指定します。

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>パラメーター

*pbstrOptionKeyPath*<br/>
[out]このプロパティの現在の値を受け取る変数のアドレス。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

##  <a name="get_showgrabhandles"></a>  IAxWinAmbientDispatch::get_ShowGrabHandles

`ShowGrabHandles`アンビエント プロパティでは、コントロールを調べるかどうかは、グラブ ハンドルを描画、自体する必要があります。

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>パラメーター

*pbShowGrabHandles*<br/>
[out]このプロパティの現在の値を受け取る変数のアドレス。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

常に ATL ホスト オブジェクト実装では、このプロパティの値として VARIANT_FALSE を返します。

##  <a name="get_showhatching"></a>  IAxWinAmbientDispatch::get_ShowHatching

`ShowHatching`アンビエント プロパティでは、コントロールを調べるかどうかハッチ自体を描画する必要があります。

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>パラメーター

*pbShowHatching*<br/>
[out]このプロパティの現在の値を受け取る変数のアドレス。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

常に ATL ホスト オブジェクト実装では、このプロパティの値として VARIANT_FALSE を返します。

##  <a name="get_usermode"></a>  IAxWinAmbientDispatch::get_UserMode

`UserMode`プロパティをコンテナーのアンビエント ユーザー モードを指定します。

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>パラメーター

*pbUserMode*<br/>
[out]このプロパティの現在の値を受け取る変数のアドレス。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、このプロパティの既定値に VARIANT_TRUE を使用します。

##  <a name="put_allowcontextmenu"></a>  IAxWinAmbientDispatch::put_AllowContextMenu

`AllowContextMenu`プロパティは、ホストされるコントロールが、独自のコンテキスト メニューを表示できるかどうかを指定します。

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>パラメーター

*bAllowContextMenu*<br/>
[in]このプロパティの新しい値。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、このプロパティの既定値に VARIANT_TRUE を使用します。

##  <a name="put_allowshowui"></a>  IAxWinAmbientDispatch::put_AllowShowUI

`AllowShowUI`プロパティは、ホストされるコントロールが、独自のユーザー インターフェイスを表示できるかどうかを指定します。

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>パラメーター

*bAllowShowUI*<br/>
[in]このプロパティの新しい値。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、このプロパティの既定値として VARIANT_FALSE を使用します。

##  <a name="put_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::put_AllowWindowlessActivation

`AllowWindowlessActivation`プロパティは、コンテナーでウィンドウなしのアクティベーションを許可するかどうかを指定します。

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>パラメーター

*bAllowWindowless*<br/>
[in]このプロパティの新しい値。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、このプロパティの既定値に VARIANT_TRUE を使用します。

##  <a name="put_backcolor"></a>  IAxWinAmbientDispatch::put_BackColor

`BackColor`プロパティをコンテナーのアンビエント背景色を指定します。

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>パラメーター

*clrBackground*<br/>
[in]このプロパティの新しい値。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、COLOR_BTNFACE または COLOR_WINDOW を (ホスト ウィンドウの親がダイアログ ボックスかどうか) に応じて、このプロパティの既定値として使用します。

##  <a name="put_displayasdefault"></a>  IAxWinAmbientDispatch::put_DisplayAsDefault

`DisplayAsDefault` アンビエント プロパティを調べるかどうかは、既定のコントロールのコントロールを許可します。

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>パラメーター

*bDisplayAsDefault*<br/>
[in]このプロパティの新しい値。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、このプロパティの既定値として VARIANT_FALSE を使用します。

##  <a name="put_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::put_DocHostDoubleClickFlags

`DocHostDoubleClickFlags`プロパティは、ダブルクリックに応答で実行される操作を指定します。

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>パラメーター

*dwDocHostDoubleClickFlags*<br/>
[in]このプロパティの新しい値。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、このプロパティの既定値として DOCHOSTUIDBLCLK_DEFAULT を使用します。

##  <a name="put_dochostflags"></a>  IAxWinAmbientDispatch::put_DocHostFlags

`DocHostFlags`プロパティが、そのホスト オブジェクトのユーザー インターフェイス機能を指定します。

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>パラメーター

*dwDocHostFlags*<br/>
[in]このプロパティの新しい値。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、このプロパティの既定値として DOCHOSTUIFLAG_NO3DBORDER を使用します。

##  <a name="put_font"></a>  IAxWinAmbientDispatch::put_Font

`Font`プロパティは、コンテナーのアンビエント フォントを指定します。

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>パラメーター

*pFont*<br/>
[in]このプロパティの新しい値。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、このプロパティの既定値として既定の GUI フォントまたはシステム フォントを使用します。

##  <a name="put_forecolor"></a>  IAxWinAmbientDispatch::put_ForeColor

`ForeColor`プロパティをコンテナーのアンビエント前景色を指定します。

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>パラメーター

*clrForeground*<br/>
[in]このプロパティの新しい値。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、このプロパティの既定値としてシステム ウィンドウのテキストの色を使用します。

##  <a name="put_localeid"></a>  IAxWinAmbientDispatch::put_LocaleID

`LocaleID`プロパティをコンテナーのアンビエント ロケール ID を指定します。

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>パラメーター

*lcidLocaleID*<br/>
[in]このプロパティの新しい値。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、このプロパティの既定値として、ユーザーの既定のロケールを使用します。

##  <a name="put_messagereflect"></a>  IAxWinAmbientDispatch::put_MessageReflect

`MessageReflect`アンビエント プロパティは、コンテナーがホストされているコントロールへのメッセージを反映するかどうかを指定します。

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>パラメーター

*bMessageReflect*<br/>
[in]このプロパティの新しい値。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、このプロパティの既定値に VARIANT_TRUE を使用します。

##  <a name="put_optionkeypath"></a>  IAxWinAmbientDispatch::put_OptionKeyPath

`OptionKeyPath`プロパティをユーザー設定をレジストリ キーのパスを指定します。

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>パラメーター

*bstrOptionKeyPath*<br/>
[in]このプロパティの新しい値。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

##  <a name="put_usermode"></a>  IAxWinAmbientDispatch::put_UserMode

`UserMode`プロパティをコンテナーのアンビエント ユーザー モードを指定します。

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>パラメーター

*bUserMode*<br/>
[in]このプロパティの新しい値。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

ATL のホスト オブジェクトの実装では、このプロパティの既定値に VARIANT_TRUE を使用します。

## <a name="see-also"></a>関連項目

[IAxWinAmbientDispatchEx インターフェイス](../../atl/reference/iaxwinambientdispatchex-interface.md)<br/>
[IAxWinHostWindow インターフェイス](../../atl/reference/iaxwinhostwindow-interface.md)<br/>
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
