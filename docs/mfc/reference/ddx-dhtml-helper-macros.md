---
title: DDX_DHtml Helper マクロ
ms.date: 11/04/2016
f1_keywords:
- AFXDHTML/DDX_DHtml_ElementValue
- AFXDHTML/DDX_DHtml_ElementInnerText
- AFXDHTML/DDX_DHtml_ElementInnerHtml
- AFXDHTML/DDX_DHtml_Anchor_Href
- AFXDHTML/DDX_DHtml_Anchor_Target
- AFXDHTML/DDX_DHtml_Img_Src
- AFXDHTML/DDX_DHtml_Frame_Src
- AFXDHTML/DDX_DHtml_IFrame_Src
helpviewer_keywords:
- macros [MFC], exchanging data with HMTL pages
- DDX macros [MFC]
- HTML pages [MFC], helper macros
- DDX (dialog data exchange), DHtml helper macros
- macros [MFC], DDX_DHtml helpers
ms.assetid: c46302d2-ea43-4fea-bfc2-6f590d99f267
ms.openlocfilehash: 90c80dbc5c8b6788f3afad3cf77d796139fbd946
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323035"
---
# <a name="ddxdhtml-helper-macros"></a>DDX_DHtml Helper マクロ

DDX_DHtml helper マクロでは、一般的に使用される HTML ページ上のコントロールのプロパティに簡単にアクセスできるようにします。

### <a name="data-exchange-macros"></a>データ エクス チェンジに関するマクロ

|||
|-|-|
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|設定または選択したコントロールの Value プロパティを取得します。|
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|設定または現在の要素の開始と終了タグの間のテキストを取得します。|
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|設定または現在の要素の開始と終了タグの間での HTML を取得します。|
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|設定または変換先の URL またはアンカー ポイントを取得します。|
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|設定またはターゲット ウィンドウまたはフレームを取得します。|
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|設定またはイメージまたはドキュメント内のビデオ クリップの名前を取得します。|
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|設定または関連付けられているフレームの URL を取得します。|
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|設定または関連付けられているフレームの URL を取得します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdhtml.h

## <a name="ddx_dhtml_anchor_href"></a> DDX_DHtml_Anchor_Href

設定または変換先の URL またはアンカー ポイントを取得します。

```
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>パラメーター

*dx*<br/>
ポインターを[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクト。

*name*<br/>
HTML コントロールの ID パラメーターに指定した値。

*var*<br/>
交換する値。

## <a name="remarks"></a>Remarks

このマクロを呼び出す、 [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) DISPID_IHTMLANCHORELEMENT_HREF を使用して関数のディスパッチ id。

## <a name="ddx_dhtml_anchor_target"></a>  DDX_DHtml_Anchor_Target

設定またはターゲット ウィンドウまたはフレームを取得します。

```
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>パラメーター

*dx*<br/>
ポインターを[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクト。

*name*<br/>
HTML コントロールの ID パラメーターに指定した値。

*var*<br/>
交換する値。

## <a name="remarks"></a>Remarks

このマクロを呼び出す、 [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) DISPID_IHTMLANCHORELEMENT_TARGET を使用して関数のディスパッチ id。

## <a name="ddx_dhtml_elementinnerhtml"></a>  DDX_DHtml_ElementInnerHtml

設定または現在の要素の開始と終了タグの間での HTML を取得します。

```
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>パラメーター

*dx*<br/>
ポインターを[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクト。

*name*<br/>
HTML コントロールの ID パラメーターに指定した値。

*var*<br/>
交換する値。

## <a name="remarks"></a>Remarks

このマクロを呼び出す、 [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) DISPID_IHTMLELEMENT_INNERHTML を使用して関数のディスパッチ id。

## <a name="ddx_dhtml_elementinnertext"></a>  DDX_DHtml_ElementInnerText

設定または現在の要素の開始と終了タグの間のテキストを取得します。

```
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>パラメーター

*dx*<br/>
ポインターを[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクト。

*name*<br/>
HTML コントロールの ID パラメーターに指定した値。

*var*<br/>
交換する値。

## <a name="remarks"></a>Remarks

このマクロを呼び出す、 [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) DISPID_IHTMLELEMENT_INNERTEXT を使用して関数のディスパッチ id。

## <a name="ddx_dhtml_elementvalue"></a> DDX_DHtml_ElementValue

設定または選択したコントロールの Value プロパティを取得します。

```
DDX_DHtml_ElementValue(
    CDataExchange* dx,
    LPCTSTR name,
    var)
```

#### <a name="parameters"></a>パラメーター

*dx*<br/>
ポインターを[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクト。

*name*<br/>
HTML コントロールの ID パラメーターに指定した値。

*var*<br/>
交換する値。 参照してください*値*で[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)します。

## <a name="remarks"></a>Remarks

このマクロは、値プロパティを持つコントロール上で実行時にのみ成功します。 値プロパティを持つコントロールには、エディット ボックスやリスト ボックス、コンボ ボックスが含まれます。

このマクロを呼び出す、 [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) DISPID_A_VALUE を使用して関数のディスパッチ id。

## <a name="ddx_dhtml_frame_src"></a> DDX_DHtml_Frame_Src

設定または関連付けられているフレームの URL を取得します。

```
DDX_DHtml_Frame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>パラメーター

*dx*<br/>
ポインターを[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクト。

*name*<br/>
HTML コントロールの ID パラメーターに指定した値。

*var*<br/>
交換する値。

## <a name="remarks"></a>Remarks

このマクロを呼び出す、 [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) DISPID_IHTMLFRAMEBASE_SRC を使用して関数のディスパッチ id。

## <a name="ddx_dhtml_iframe_src"></a> DDX_DHtml_IFrame_Src

設定または関連付けられているフレームの URL を取得します。

```
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>パラメーター

*dx*<br/>
ポインターを[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクト。

*name*<br/>
HTML コントロールの ID パラメーターに指定した値。

*var*<br/>
交換する値。

## <a name="remarks"></a>Remarks

このマクロを呼び出す、 [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) DISPID_IHTMLFRAMEBASE_SRC を使用して関数のディスパッチ id。

## <a name="ddx_dhtml_img_src"></a>DDX_DHtml_Img_Src

取得またはイメージまたはドキュメント内のビデオ クリップの名前を取得します。

```
DDX_DHtml_Img_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>パラメーター

*dx*<br/>
ポインターを[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクト。

*name*<br/>
HTML コントロールの ID パラメーターに指定した値。

*var*<br/>
交換する値。

## <a name="remarks"></a>Remarks

DDX_DHtml_Img_Src マクロを使用して、イメージ要素の src プロパティを取得する、Internet Explorer のイメージ オブジェクトは、イメージ ソースの完全にエスケープされた URL を返します。 たとえば、「いくつかの興味深い像」を文字列に画像の要素の src プロパティを設定する DDX_DHtml_Img_Src マクロを使用する場合 Internet Explorer、そのプロパティを取得する場合は文字列を返します、res://d:\myapplication\myapp.exe/some%"20interesting %20picture。"

このマクロを呼び出す、 [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) DISPID_IHTMLIMGELEMENT_SRC を使用して関数のディスパッチ id。

## <a name="see-also"></a>関連項目

[CDHtmlDialog クラス](../../mfc/reference/cdhtmldialog-class.md)
