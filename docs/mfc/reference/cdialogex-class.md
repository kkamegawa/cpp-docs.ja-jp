---
title: CDialogEx クラス
ms.date: 11/04/2016
f1_keywords:
- CDialogEx
- AFXDIALOGEX/CDialogEx
- AFXDIALOGEX/CDialogEx::CDialogEx
- AFXDIALOGEX/CDialogEx::SetBackgroundColor
- AFXDIALOGEX/CDialogEx::SetBackgroundImage
helpviewer_keywords:
- CDialogEx [MFC], CDialogEx
- CDialogEx [MFC], SetBackgroundColor
- CDialogEx [MFC], SetBackgroundImage
ms.assetid: a6ed3b1f-aef8-4b66-ac78-2160faf63c13
ms.openlocfilehash: f92058d1aa0dabccf6623d20a248fed8eb99ab26
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62168051"
---
# <a name="cdialogex-class"></a>CDialogEx クラス

`CDialogEx` クラスは、ダイアログ ボックスの背景色と背景イメージを指定します。 

## <a name="syntax"></a>構文

```
class CDialogEx : public CDialog
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CDialogEx::CDialogEx](#cdialogex)|`CDialogEx` オブジェクトを構築します。|
|`CDialogEx::~CDialogEx`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDialogEx::SetBackgroundColor](#setbackgroundcolor)|ダイアログ ボックスの背景色を設定します。|
|[CDialogEx::SetBackgroundImage](#setbackgroundimage)|ダイアログ ボックスの背景イメージを設定します。|

## <a name="remarks"></a>Remarks

`CDialogEx` クラスを使用するには、ダイアログ ボックス クラスを `CDialogEx` クラスではなく `CDialog` クラスから派生させます。

ダイアログ ボックス イメージは、リソース ファイルに格納されます。 フレームワークは、リソース ファイルから読み込まれたイメージを自動的に削除します。 現在の背景イメージをプログラムで削除する、 [CDialogEx::SetBackgroundImage](#setbackgroundimage)メソッドまたは実装、`OnDestroy`イベント ハンドラー。 呼び出すと、 [CDialogEx::SetBackgroundImage](#setbackgroundimage)メソッドでパスを`HBITMAP`イメージ ハンドルとしてパラメーター。 `CDialogEx` オブジェクトがイメージの所有権を取得し、`m_bAutoDestroyBmp` フラグが `TRUE` である場合は、そのイメージを削除します。

A`CDialogEx`オブジェクトの親になることができます、 [CMFCPopupMenu クラス](../../mfc/reference/cmfcpopupmenu-class.md)オブジェクト。 [CMFCPopupMenu クラス](../../mfc/reference/cmfcpopupmenu-class.md)オブジェクトの呼び出し、`CDialogEx::SetActiveMenu`メソッドと、 [CMFCPopupMenu クラス](../../mfc/reference/cmfcpopupmenu-class.md)オブジェクトが表示されます。 その後、`CDialogEx`まで、あらゆるメニュー イベントを処理するオブジェクト、 [CMFCPopupMenu クラス](../../mfc/reference/cmfcpopupmenu-class.md)オブジェクトが閉じられます。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdialogex.h

##  <a name="cdialogex"></a>  CDialogEx::CDialogEx

`CDialogEx` オブジェクトを構築します。

```
CDialogEx(
    UINT nIDTemplate,
    CWnd* pParent=NULL);

CDialogEx(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd=NULL);
```

### <a name="parameters"></a>パラメーター

*nIDTemplate*<br/>
[in]ダイアログ ボックス テンプレートのリソース ID。

*lpszTemplateName*<br/>
[in]ダイアログ ボックス テンプレートのリソースの名前。

*pParent*<br/>
[in]親ウィンドウへのポインター。 既定値は、NULL です。

*pParentWnd*<br/>
[in]親ウィンドウへのポインター。 既定値は、NULL です。

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="setbackgroundcolor"></a>  CDialogEx::SetBackgroundColor

ダイアログ ボックスの背景色を設定します。

```
void SetBackgroundColor(
    COLORREF color,
    BOOL bRepaint=TRUE);
```

### <a name="parameters"></a>パラメーター

*色*<br/>
[in]RGB 色の値。

*bRepaint*<br/>
[in]画面をすぐに更新する場合は TRUEそれ以外の場合、FALSE です。 既定値は TRUE です。

### <a name="remarks"></a>Remarks

##  <a name="setbackgroundimage"></a>  CDialogEx::SetBackgroundImage

ダイアログ ボックスの背景イメージを設定します。

```
void SetBackgroundImage(
    HBITMAP hBitmap,
    BackgroundLocation location=BACKGR_TILE,
    BOOL bAutoDestroy=TRUE,
    BOOL bRepaint=TRUE);

BOOL SetBackgroundImage(
    UINT uiBmpResId,
    BackgroundLocation location=BACKGR_TILE,
    BOOL bRepaint=TRUE);
```

### <a name="parameters"></a>パラメーター

*hBitmap*<br/>
[in]背景イメージへのハンドル。

*uiBmpResId*<br/>
[in]背景イメージのリソース ID。

*location*<br/>
[in]1 つ、`CDialogEx::BackgroundLocation`イメージの場所を指定する値。 有効な値には、BACKGR_TILE、BACKGR_TOPLEFT、BACKGR_TOPRIGHT、BACKGR_BOTTOMLEFT、および BACKGR_BOTTOMRIGHT が含まれます。 既定値は、BACKGR_TILE です。

*bAutoDestroy*<br/>
[in]背景イメージを自動的に破棄する場合は TRUEそれ以外の場合、FALSE です。

*bRepaint*<br/>
[in]ダイアログ ボックスがすぐに再描画する場合は TRUEそれ以外の場合、FALSE です。

### <a name="return-value"></a>戻り値

2 番目のメソッドでオーバー ロードの構文、true の場合、メソッドが成功した場合それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

指定されたイメージは、ダイアログ ボックスのクライアント領域に合わせて引き伸ばされません。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu クラス](../../mfc/reference/cmfcpopupmenu-class.md)<br/>
[CContextMenuManager クラス](../../mfc/reference/ccontextmenumanager-class.md)
