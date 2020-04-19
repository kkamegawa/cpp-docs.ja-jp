---
title: CMFCPopupMenuBar クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCPopupMenuBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::AdjustSizeImmediate
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::BuildOrigItems
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::CloseDelayedSubMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::ExportToMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::FindDestintationToolBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetCurrentMenuImageSize
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetDefaultMenuId
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetLastCommandIndex
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetOffset
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::ImportFromMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsDropDownListMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsPaletteMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsRibbonPanel
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsRibbonPanelInRegularMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::LoadFromHash
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::RestoreDelayedSubMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::SetButtonStyle
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::SetOffset
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::StartPopupMenuTimer
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::m_bDisableSideBarInXPMode
helpviewer_keywords:
- CMFCPopupMenuBar [MFC], AdjustSizeImmediate
- CMFCPopupMenuBar [MFC], BuildOrigItems
- CMFCPopupMenuBar [MFC], CloseDelayedSubMenu
- CMFCPopupMenuBar [MFC], ExportToMenu
- CMFCPopupMenuBar [MFC], FindDestintationToolBar
- CMFCPopupMenuBar [MFC], GetCurrentMenuImageSize
- CMFCPopupMenuBar [MFC], GetDefaultMenuId
- CMFCPopupMenuBar [MFC], GetLastCommandIndex
- CMFCPopupMenuBar [MFC], GetOffset
- CMFCPopupMenuBar [MFC], ImportFromMenu
- CMFCPopupMenuBar [MFC], IsDropDownListMode
- CMFCPopupMenuBar [MFC], IsPaletteMode
- CMFCPopupMenuBar [MFC], IsRibbonPanel
- CMFCPopupMenuBar [MFC], IsRibbonPanelInRegularMode
- CMFCPopupMenuBar [MFC], LoadFromHash
- CMFCPopupMenuBar [MFC], RestoreDelayedSubMenu
- CMFCPopupMenuBar [MFC], SetButtonStyle
- CMFCPopupMenuBar [MFC], SetOffset
- CMFCPopupMenuBar [MFC], StartPopupMenuTimer
- CMFCPopupMenuBar [MFC], m_bDisableSideBarInXPMode
ms.assetid: 4c93c459-7f70-4240-8c63-280bb811e374
ms.openlocfilehash: acb1e2be7d40e5e0c569fffcc92c57c750be8f91
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374026"
---
# <a name="cmfcpopupmenubar-class"></a>CMFCPopupMenuBar クラス

ポップアップ メニューに埋め込まれたメニュー バーです。

## <a name="syntax"></a>構文

```
class CMFCPopupMenuBar : public CMFCToolBar
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCPopupMenuBar::AdjustSizeImmediate](#adjustsizeimmediate)|ウィンドウのレイアウトをすぐに再計算します。 (上書き[CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate))。|
|[CMFCPopupMenuBar::BuildOrigItems](#buildorigitems)|指定したメニュー リソースからのポップアップ メニュー項目を読み込みます。|
|[CMFCPopupMenuBar::CloseDelayedSubMenu](#closedelayedsubmenu)|遅延のポップアップ メニュー ボタンを閉じます。|
|[CMFCPopupMenuBar::ExportToMenu](#exporttomenu)|ポップアップ メニュー ボタンからメニューを作成します。|
|[CMFCPopupMenuBar::FindDestintationToolBar](#finddestintationtoolbar)|指定した点がどこにあるツールバーを検索します。|
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](#getcurrentmenuimagesize)|メニュー ボタンのイメージのサイズを示します。|
|[CMFCPopupMenuBar::GetDefaultMenuId](#getdefaultmenuid)|既定のメニュー項目の識別子を返します。|
|[CMFCPopupMenuBar::GetLastCommandIndex](#getlastcommandindex)|最後に呼び出したメニュー コマンドのインデックスを取得します。|
|[CMFCPopupMenuBar::GetOffset](#getoffset)|ポップアップ メニュー バーの行オフセットを取得します。|
|[CMFCPopupMenuBar::ImportFromMenu](#importfrommenu)|指定したメニューからポップアップ メニュー ボタンをインポートします。|
|[CMFCPopupMenuBar::IsDropDownListMode](#isdropdownlistmode)|ポップアップ メニューがドロップ ダウン リスト モードかどうかを示します。|
|[CMFCPopupMenuBar::IsPaletteMode](#ispalettemode)|ポップアップ メニュー バーがパレット モードかどうかを示します。|
|[CMFCPopupMenuBar::IsRibbonPanel](#isribbonpanel)|これは、リボン パネル (既定で FALSE) かどうかを示します。|
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](#isribbonpanelinregularmode)|通常モード (既定で FALSE) であるかどうかリボン パネルを示します。|
|[CMFCPopupMenuBar::LoadFromHash](#loadfromhash)|アーカイブ済みのメニューを読み込みます。|
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](#restoredelayedsubmenu)|ポップアップ メニュー バーを閉じるための遅延のメニュー ボタンを復元します。|
|[CMFCPopupMenuBar::SetButtonStyle](#setbuttonstyle)|指定したインデックス位置にあるツールバーのボタンのスタイルを設定します。 (上書き[CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle))。|
|[CMFCPopupMenuBar::SetOffset](#setoffset)|ポップアップ メニュー バーの行オフセットを設定します。|
|[CMFCPopupMenuBar::StartPopupMenuTimer](#startpopupmenutimer)|指定された遅延のポップアップ メニュー ボタンのタイマーを開始します。|

### <a name="data-members"></a>データ メンバー

|名前|説明|
|----------|-----------------|
|[CMFCPopupMenuBar::m_bDisableSideBarInXPMode](#m_bdisablesidebarinxpmode)|アプリケーションがある Windows XP の外観とグレーのサイドバーが表示されるかどうかを指定します。|

## <a name="remarks"></a>Remarks

`CMFCPopupMenuBar`と同時に作成、 [CMFCPopupMenu クラス](../../mfc/reference/cmfcpopupmenu-class.md)その内部に埋め込まれたとします。 `CMFCPopupMenuBar`の全体のクライアント領域を覆う、`CMFCPopupMenu`オブジェクト。 キーボードとマウス入力をサポートします。 入力するとも通信、`CMFCPopupMenu`と最上位レベルのフレーム ウィンドウにします。

## <a name="example"></a>例

次の例では、初期化する方法、`CMFCPopupMenuBar`オブジェクトから、`CMFCPopupMenu`オブジェクト。 このコード スニペットは、「 [クライアント サンプルの描画](../../overview/visual-cpp-samples.md)」の一部です。

[!code-cpp[NVC_MFC_DrawClient#7](../../mfc/reference/codesnippet/cpp/cmfcpopupmenubar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxpopupmenubar.h

##  <a name="adjustsizeimmediate"></a>  CMFCPopupMenuBar::AdjustSizeImmediate

すぐに、ポップアップ メニュー バーのウィンドウのレイアウトを再計算します。 (上書き[CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate)します。

```
virtual void AdjustSizeImmediate(BOOL bRecalcLayout);
```

### <a name="parameters"></a>パラメーター

*bRecalcLayout*<br/>
[in]ポップアップ メニュー バー ペインのレイアウトを自動的に再計算する場合は TRUEそれ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

##  <a name="buildorigitems"></a>  CMFCPopupMenuBar::BuildOrigItems

指定したメニュー リソースからのポップアップ メニュー項目を読み込みます。

```
BOOL BuildOrigItems(UINT uiMenuResID);
```

### <a name="parameters"></a>パラメーター

*uiMenuResID*<br/>
[in]読み込むメニュー リソースのメニュー ID を指定します。

### <a name="return-value"></a>戻り値

成功した場合は TRUE またはしない場合は FALSE を返します。

### <a name="remarks"></a>Remarks

##  <a name="closedelayedsubmenu"></a>  CMFCPopupMenuBar::CloseDelayedSubMenu

実行が遅れているポップアップ メニュー ボタンを閉じます。

```
virtual void CloseDelayedSubMenu();
```

### <a name="remarks"></a>Remarks

##  <a name="exporttomenu"></a>  CMFCPopupMenuBar::ExportToMenu

ポップアップ メニュー ボタンからメニューを作成します。

```
virtual HMENU ExportToMenu() const;
```

### <a name="return-value"></a>戻り値

新しいメニューにハンドルを返します。

### <a name="remarks"></a>Remarks

##  <a name="finddestintationtoolbar"></a>  CMFCPopupMenuBar::FindDestintationToolBar

指定した点がどこにあるツールバーを検索します。

```
CMFCToolBar* FindDestintationToolBar(CPoint point);
```

### <a name="parameters"></a>パラメーター

*ポイント*<br/>
[in]画面上のポイント。

### <a name="return-value"></a>戻り値

ハンドルを返します、ツールバーにポイントにある、1 つを使用する必要がある場合やない場合は NULL です。

### <a name="remarks"></a>Remarks

##  <a name="getcurrentmenuimagesize"></a>  CMFCPopupMenuBar::GetCurrentMenuImageSize

メニュー ボタンのイメージのサイズを示します。

```
virtual CSize GetCurrentMenuImageSize() const;
```

### <a name="return-value"></a>戻り値

ツールバーのメニュー ボタンのイメージのサイズを返します。

### <a name="remarks"></a>Remarks

##  <a name="getdefaultmenuid"></a>  CMFCPopupMenuBar::GetDefaultMenuId

既定のメニュー項目の識別子を返します。

```
UINT GetDefaultMenuId() const;
```

### <a name="return-value"></a>戻り値

ポップアップ メニュー バーで、既定のメニュー項目の識別子を返します。

### <a name="remarks"></a>Remarks

##  <a name="getlastcommandindex"></a>  CMFCPopupMenuBar::GetLastCommandIndex

最後に呼び出したメニュー コマンドのインデックスを取得します。

```
static int __stdcall GetLastCommandIndex();
```

### <a name="return-value"></a>戻り値

呼び出された最後のメニュー コマンドのインデックスを返します。

### <a name="remarks"></a>Remarks

##  <a name="getoffset"></a>  CMFCPopupMenuBar::GetOffset

ポップアップ メニュー バーの行オフセットを取得します。

```
int GetOffset() const;
```

### <a name="return-value"></a>戻り値

ポップアップ メニュー バーの行オフセットを返します。

### <a name="remarks"></a>Remarks

使用してこの値を設定[CMFCPopupMenuBar::SetOffset](#setoffset)します。

##  <a name="importfrommenu"></a>  CMFCPopupMenuBar::ImportFromMenu

指定したメニューからポップアップ メニュー ボタンをインポートします。

```
virtual BOOL ImportFromMenu(
    HMENU hMenu,
    BOOL bShowAllCommands = FALSE);
```

### <a name="parameters"></a>パラメーター

*hMenu*<br/>
[in]ポップアップ メニュー ボタンのインポート元のメニュー。

*bShowAllCommands*<br/>
[in]メニューの TRUE の場合は、すべてのコマンドでは、インポート、または FALSE の場合、使用頻度の低いものが非表示にします。

### <a name="return-value"></a>戻り値

メニュー ボタンが正常にインポートされた場合は FALSE またはメニューからない場合は、TRUE を返します。

### <a name="remarks"></a>Remarks

##  <a name="isdropdownlistmode"></a>  CMFCPopupMenuBar::IsDropDownListMode

ポップアップ メニューがドロップ ダウン リスト モードかどうかを示します。

```
BOOL IsDropDownListMode() const;
```

### <a name="return-value"></a>戻り値

ポップアップ メニュー バーでないドロップ ダウン リスト モード、または場合は FALSE の場合は、TRUE を返します。

### <a name="remarks"></a>Remarks

##  <a name="ispalettemode"></a>  CMFCPopupMenuBar::IsPaletteMode

ポップアップ メニュー バーがパレット モードかどうかを示します。

```
BOOL IsPaletteMode() const;
```

### <a name="return-value"></a>戻り値

パレットのモードが有効になっている場合は TRUE またはしない場合は FALSE を返します。

### <a name="remarks"></a>Remarks

メニュー バーがパレット モードに設定されている場合は、複数の列と行の制限数にメニュー項目が表示されます。

##  <a name="isribbonpanel"></a>  CMFCPopupMenuBar::IsRibbonPanel

これは、リボン パネル (既定で FALSE) かどうかを示します。

```
virtual BOOL IsRibbonPanel() const;
```

### <a name="return-value"></a>戻り値

既定では、リボン パネルではないことを示す FALSE を返します。

### <a name="remarks"></a>Remarks

##  <a name="isribbonpanelinregularmode"></a>  CMFCPopupMenuBar::IsRibbonPanelInRegularMode

通常モード (既定で FALSE) であるかどうかリボン パネルを示します。

```
virtual BOOL IsRibbonPanelInRegularMode() const;
```

### <a name="return-value"></a>戻り値

既定ではないことを示すこのリボン パネルの通常モードでは、FALSE を返します。

### <a name="remarks"></a>Remarks

##  <a name="loadfromhash"></a>  CMFCPopupMenuBar::LoadFromHash

アーカイブ済みのメニューを読み込みます。

```
BOOL LoadFromHash(HMENU hMenu);
```

### <a name="parameters"></a>パラメーター

*hMenu*<br/>
[in]読み込みにアーカイブされたメニューへのハンドル。

### <a name="return-value"></a>戻り値

メニューが正常に読み込まれたまたはしない場合は FALSE の場合は、TRUE を返します。

### <a name="remarks"></a>Remarks

##  <a name="m_bdisablesidebarinxpmode"></a>  CMFCPopupMenuBar::m_bDisableSideBarInXPMode

Windows XP の外観があるときに、アプリケーションがグレーのサイドバーを持つかどうかを示すブール値パラメーター。

```
BOOL m_bDisableSideBarInXPMode;
```

### <a name="remarks"></a>Remarks

このメンバー変数が FALSE に設定して、アプリケーションが Windows XP の外観を場合、フレームワークは、アプリケーションで灰色のサイドバーを描画します。

既定値は FALSE です。

##  <a name="restoredelayedsubmenu"></a>  CMFCPopupMenuBar::RestoreDelayedSubMenu

ポップアップ メニュー バーを閉じるための遅延のメニュー ボタンを復元します。

```
virtual void RestoreDelayedSubMenu();
```

### <a name="remarks"></a>Remarks

##  <a name="setbuttonstyle"></a>  CMFCPopupMenuBar::SetButtonStyle

指定したインデックス位置にあるツールバーのボタンのスタイルを設定します。 (上書き[CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle))。

```
virtual void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
[in]スタイルを設定するが、ツール バー ボタンの 0 から始まるインデックス。

*nStyle*<br/>
[in]ボタンのスタイル。 参照してください[ツール バー コントロールのスタイル](../../mfc/reference/toolbar-control-styles.md)利用できるツール バー ボタンのスタイルの一覧についてはします。

### <a name="remarks"></a>Remarks

##  <a name="setoffset"></a>  CMFCPopupMenuBar::SetOffset

ポップアップ メニュー バーの行オフセットを設定します。

```
void SetOffset(int iOffset);
```

### <a name="parameters"></a>パラメーター

*iOffset*<br/>
[in]ポップアップ メニュー バーをオフセットするか行の数。

### <a name="remarks"></a>Remarks

##  <a name="startpopupmenutimer"></a>  CMFCPopupMenuBar::StartPopupMenuTimer

指定された遅延のポップアップ メニュー ボタンのタイマーを開始します。

```
void StartPopupMenuTimer(
    CMFCToolBarMenuButton* pMenuButton,
    int nDelayFactor = 1);
```

### <a name="parameters"></a>パラメーター

*pMenuButton*<br/>
[in]遅延タイマーを設定する対象のメニュー ボタンへのポインター。

*nDelayFactor*<br/>
[in]遅延係数、標準のメニューの遅延時間 (0.5 秒間一般に、5 秒) に乗算する 1 以上に等しい。

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar クラス](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCPopupMenu クラス](../../mfc/reference/cmfcpopupmenu-class.md)
