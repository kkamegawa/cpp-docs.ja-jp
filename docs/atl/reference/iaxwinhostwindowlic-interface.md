---
title: IAxWinHostWindowLic インターフェイス
ms.date: 11/04/2016
f1_keywords:
- IAxWinHostWindowLic
- ATLIFACE/ATL::IAxWinHostWindowLic
- ATLIFACE/ATL::CreateControlLic
- ATLIFACE/ATL::CreateControlLicEx
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
ms.openlocfilehash: aca3970d13db53ffa04fe9582bbe9b8db78e820d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275991"
---
# <a name="iaxwinhostwindowlic-interface"></a>IAxWinHostWindowLic インターフェイス

このインターフェイスは、ライセンスされたコントロールとそのホスト オブジェクトを操作するためのメソッドを提供します。

## <a name="syntax"></a>構文

```
interface IAxWinHostWindowLic : IAxWinHostWindow
```

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[CreateControlLic](#createcontrollic)|ライセンス付きコントロールを作成し、そのホスト オブジェクトにアタッチします。|
|[CreateControlLicEx](#createcontrollicex)|ライセンス付きコントロールを作成、ホスト オブジェクトにアタッチしますおよび必要に応じて、イベント ハンドラーを設定します。|

## <a name="remarks"></a>Remarks

`IAxWinHostWindowLic` 継承[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)ライセンス付きコントロールの作成をサポートするメソッドを追加します。

参照してください[ActiveX コントロール ATL を使用しての AXHost をホストしている](../../atl/hosting-activex-controls-using-atl-axhost.md)のこのインターフェイスのメンバーを使用するサンプルです。

## <a name="requirements"></a>必要条件

このインターフェイスの定義は、次に示すように IDL または C++ では、使用可能です。

|定義の種類|ファイル|
|---------------------|----------|
|IDL|ATLIFace.idl|
|C++|ATLIFace.h (ATLBase.h にも含まれています)|

##  <a name="createcontrollic"></a>  IAxWinHostWindowLic::CreateControlLic

ライセンス付きコントロールを作成し、それを初期化しで識別されるウィンドウでホスト`hWnd`します。

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>パラメーター

*bstrLic*<br/>
[in]コントロールのライセンス キーを含む BSTR です。

### <a name="remarks"></a>Remarks

参照してください[については](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol)の残りのパラメーターと戻り値の説明。

このメソッドを呼び出すには、[呼び出し](#createcontrollicex)

### <a name="example"></a>例

参照してください[ActiveX コントロール ATL を使用しての AXHost をホストしている](../../atl/hosting-activex-controls-using-atl-axhost.md)を使用するサンプルの`IAxWinHostWindowLic::CreateControlLic`します。

##  <a name="createcontrollicex"></a>  IAxWinHostWindowLic::CreateControlLicEx

ライセンスされた ActiveX コントロールを作成し、それを初期化し、指定したウィンドウでホスト[については](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol)します。

```
STDMETHOD(CreateControlLicEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise,
    BSTR bstrLic);
```

### <a name="parameters"></a>パラメーター

*bstrLic*<br/>
[in]コントロールのライセンス キーを含む BSTR です。

### <a name="remarks"></a>Remarks

参照してください[詳細](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex)の残りのパラメーターと戻り値の説明。

### <a name="example"></a>例

参照してください[ActiveX コントロール ATL を使用しての AXHost をホストしている](../../atl/hosting-activex-controls-using-atl-axhost.md)を使用するサンプルの`IAxWinHostWindowLic::CreateControlLicEx`します。
