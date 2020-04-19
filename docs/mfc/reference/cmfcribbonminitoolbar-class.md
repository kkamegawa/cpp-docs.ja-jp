---
title: CMFCRibbonMiniToolBar クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsContextMenuMode
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::SetCommands
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::Show
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::ShowWithContextMenu
helpviewer_keywords:
- CMFCRibbonMiniToolBar [MFC], IsContextMenuMode
- CMFCRibbonMiniToolBar [MFC], IsRibbonMiniToolBar
- CMFCRibbonMiniToolBar [MFC], SetCommands
- CMFCRibbonMiniToolBar [MFC], Show
- CMFCRibbonMiniToolBar [MFC], ShowWithContextMenu
ms.assetid: 7017e963-aeaf-4fe9-b540-e15a7ed41e94
ms.openlocfilehash: 394182aa0f9c967524ed0db510d0b9cc0739118e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151891"
---
# <a name="cmfcribbonminitoolbar-class"></a>CMFCRibbonMiniToolBar クラス

コンテキスト ポップアップ ツール バーを実装します。

## <a name="syntax"></a>構文

```
class CMFCRibbonMiniToolBar : public CMFCRibbonPanelMenu
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|`CMFCRibbonMiniToolBar::CMFCRibbonMiniToolBar`|既定のコンストラクターです。|
|`CMFCRibbonMiniToolBar::~CMFCRibbonMiniToolBar`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|`CMFCRibbonMiniToolBar::CreateObject`|このクラス型の動的インスタンスを作成するために、フレームワークで使用されます。|
|`CMFCRibbonMiniToolBar::GetThisClass`|ポインターを取得する、framework によって使用される、 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)このクラス型に関連付けられているオブジェクト。|
|[CMFCRibbonMiniToolBar::IsContextMenuMode](#iscontextmenumode)||
|[CMFCRibbonMiniToolBar::IsRibbonMiniToolBar](#isribbonminitoolbar)|( `CMFCPopupMenu::IsRibbonMiniToolBar`をオーバーライドします)。|
|[CMFCRibbonMiniToolBar::SetCommands](#setcommands)|ツール バーに表示するコマンドのリストを設定します。|
|[CMFCRibbonMiniToolBar::Show](#show)|指定した画面座標に、ミニ ツール バーを表示します。|
|[CMFCRibbonMiniToolBar::ShowWithContextMenu](#showwithcontextmenu)|コンテキスト メニューとミニ ツール バーが表示されます。|

## <a name="remarks"></a>Remarks

ミニ ツール バーは、通常、ユーザーがドキュメント内のオブジェクトを選択した後に表示されます。 たとえば、ユーザーがワード プロセッサ プログラム内のテキストを選択すると、アプリケーションでテキストの書式設定コマンドを含むミニ ツール バーが表示されます。

マウス ポインターがミニ ツール バーの境界外にあるときは、ミニ ツール バーは透明になります。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

`CMFCRibbonPanelMenu`

[CMFCRibbonMiniToolBar](../../mfc/reference/cmfcribbonminitoolbar-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxRibbonMiniToolBar.h

##  <a name="setcommands"></a>  CMFCRibbonMiniToolBar::SetCommands

ツール バーに表示するコマンドのリストを設定します。

```
void SetCommands(
    CMFCRibbonBar* pRibbonBar,
    const CList<UINT,UINT>& lstCommands);
```

### <a name="parameters"></a>パラメーター

*pRibbonBar*<br/>
[in]リボン バー、ミニ ツールバーを表示するボタンを検索します。

*lstCommands*<br/>
[in]ミニ ツールバーに表示するコマンドの一覧。 関連付けられたボタンを検索するには、すべてのリボン カテゴリが検索されます。

### <a name="remarks"></a>Remarks

この関数を使用すると、ミニ ツールバーに表示されるコマンドの一覧を設定できます。

### <a name="example"></a>例

次の例では、使用する方法、`SetCommands`のメソッド、`CMFCRibbonMiniToolBar`クラス。 このコード スニペットの一部、 [MS Office 2007 のデモ サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_MSOffice2007Demo#9](../../mfc/reference/codesnippet/cpp/cmfcribbonminitoolbar-class_1.cpp)]

##  <a name="show"></a>  CMFCRibbonMiniToolBar::Show

指定した画面座標に、ミニ ツール バーを表示します。

```
BOOL Show(
    int x,
    int y);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
[in]画面座標では、ミニ ツールバーの水平方向の位置を指定します。

*y*<br/>
[in]画面座標では、ミニ ツールバーの垂直位置を指定します。

### <a name="return-value"></a>戻り値

ミニ ツールバーが正常に表示されている場合は TRUE。それ以外の場合、FALSE です。

##  <a name="showwithcontextmenu"></a>  CMFCRibbonMiniToolBar::ShowWithContextMenu

コンテキスト メニューとミニ ツール バーが表示されます。

```
BOOL ShowWithContextMenu(
    int x,
    int y,
    UINT uiMenuResID,
    CWnd* pWndOwner);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
[in]画面座標では、コンテキスト メニューの水平方向の位置を指定します。

*y*<br/>
[in]画面座標で、コンテキスト メニューの垂直位置を指定します。

*uiMenuResID*<br/>
[in]表示するコンテキスト メニューのリソース ID を指定します。

*pWndOwner*<br/>
[in]コンテキスト メニューからメッセージを受信するウィンドウを識別します。

### <a name="return-value"></a>戻り値

コンテキスト メニューが正常に表示されている場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

コンテキスト メニューを含むミニ ツールバーを表示するのにには、この関数を使用します。 コンテキスト メニューは、ミニ ツールバーの下の位置指定の 15 ピクセルです。

##  <a name="iscontextmenumode"></a>  CMFCRibbonMiniToolBar::IsContextMenuMode

詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。

```
BOOL IsContextMenuMode() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="isribbonminitoolbar"></a>  CMFCRibbonMiniToolBar::IsRibbonMiniToolBar

詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。

```
virtual BOOL IsRibbonMiniToolBar() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)
