---
title: CTooltipManager クラス
ms.date: 11/04/2016
f1_keywords:
- CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager::CreateToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::DeleteToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipParams
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipText
- AFXTOOLTIPMANAGER/CTooltipManager::UpdateTooltips
helpviewer_keywords:
- CTooltipManager [MFC], CreateToolTip
- CTooltipManager [MFC], DeleteToolTip
- CTooltipManager [MFC], SetTooltipParams
- CTooltipManager [MFC], SetTooltipText
- CTooltipManager [MFC], UpdateTooltips
ms.assetid: c71779d7-8b6e-47ef-8500-d4552731fe86
ms.openlocfilehash: e8b88f2722f5a4379276f13c2ef159aa4d120533
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323753"
---
# <a name="ctooltipmanager-class"></a>CTooltipManager クラス

ツールヒントに関するランタイム情報を保持します。 `CTooltipManager` クラスのインスタンスは、アプリケーションごとに 1 回作成されます。

## <a name="syntax"></a>構文

```
class CTooltipManager : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CTooltipManager::CreateToolTip](#createtooltip)|指定された Windows コントロールの種類のツールヒント コントロールを作成します。|
|[CTooltipManager::DeleteToolTip](#deletetooltip)|ツールヒント コントロールを削除します。|
|[:Settooltipparams](#settooltipparams)|指定された Windows コントロールの種類のツールヒント コントロールの外観をカスタマイズします。|
|[CTooltipManager::SetTooltipText](#settooltiptext)|ツールヒント コントロールのテキストと説明を設定します。|
|[CTooltipManager::UpdateTooltips](#updatetooltips)||

## <a name="remarks"></a>Remarks

使用[CMFCToolTipCtrl クラス](../../mfc/reference/cmfctooltipctrl-class.md)、 `CMFCToolTipInfo`、および`CTooltipManager`アプリケーションでカスタマイズされたツールヒントを実装するためにします。 これらのツールヒントのクラスを使用する方法の例は、次を参照してください。、 [CMFCToolTipCtrl クラス](../../mfc/reference/cmfctooltipctrl-class.md)トピック。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxtooltipmanager.h

##  <a name="createtooltip"></a>  CTooltipManager::CreateToolTip

ツール ヒント コントロールを作成します。

```
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,
    CWnd* pWndParent,
    UINT nType);
```

### <a name="parameters"></a>パラメーター

*pToolTip*<br/>
[out]ツールヒントのポインターへの参照。 新しく作成されたツールヒントを指すように、関数が返されるときに設定されます。

*pWndParent*<br/>
[in]ツールヒントの親です。

*nType*<br/>
[in]ツールヒントの型。

### <a name="return-value"></a>戻り値

0 以外の場合、ツールヒントが正常に作成されました。

### <a name="remarks"></a>Remarks

呼び出す必要があります[CTooltipManager::DeleteToolTip](#deletetooltip)に渡されるツールヒント コントロールを削除する*pToolTip*します。

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)作成各ツールヒントのビジュアル表示パラメーターがツールヒントに基づくセットの種類を *%n タイプ*を指定します。 ツールヒントの種類を 1 つまたは複数のパラメーターを変更するには、呼び出す[:settooltipparams](#settooltipparams)します。

ツールヒントが有効な型は、次の表のとおりです。

|ツールヒントの種類|コントロールのカテゴリ|型の例|
|------------------|----------------------|-------------------|
|AFX_TOOLTIP_TYPE_BUTTON|ボタンをクリックします。|CMFCButton|
|AFX_TOOLTIP_TYPE_CAPTIONBAR|キャプション バー。|CMFCCaptionBar|
|AFX_TOOLTIP_TYPE_DEFAULT|別のカテゴリに適合しない任意のコントロール。|なし。|
|AFX_TOOLTIP_TYPE_DOCKBAR|ドッキング可能ペイン。|CDockablePane|
|AFX_TOOLTIP_TYPE_EDIT|テキスト ボックスです。|なし。|
|AFX_TOOLTIP_TYPE_MINIFRAME|ミニフレームします。|CPaneFrameWnd|
|AFX_TOOLTIP_TYPE_PLANNER|プランナー|なし。|
|AFX_TOOLTIP_TYPE_RIBBON|リボン バー。|CMFCRibbonBar、CMFCRibbonPanelMenuBar|
|AFX_TOOLTIP_TYPE_TAB|タブ コントロール。|CMFCTabCtrl|
|AFX_TOOLTIP_TYPE_TOOLBAR|ツールバー。|CMFCToolBar、CMFCPopupMenuBar|
|AFX_TOOLTIP_TYPE_TOOLBOX|ツールボックスです。|なし。|

##  <a name="deletetooltip"></a>  CTooltipManager::DeleteToolTip

ツールヒント コントロールを削除します。

```
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```

### <a name="parameters"></a>パラメーター

*pToolTip*<br/>
[入力、出力]破棄するツールヒントへのポインターへの参照。

### <a name="remarks"></a>Remarks

このメソッドの各呼び出し[CToolTipCtrl クラス](../../mfc/reference/ctooltipctrl-class.md)によって作成された[CTooltipManager::CreateToolTip](#createtooltip)します。 親コントロールからこのメソッドを呼び出す必要があります、`OnDestroy`ハンドラー。 これは、framework からヒントを正しく削除に必要です。 このメソッドは、設定*pToolTip*を返す前に NULL にします。

##  <a name="settooltipparams"></a>  CTooltipManager::SetTooltipParams

指定した種類の Windows コントロールのツールヒント コントロールの外観をカスタマイズします。

```
void SetTooltipParams(
    UINT nTypes,
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),
    CMFCToolTipInfo* pParams=NULL);
```

### <a name="parameters"></a>パラメーター

*nTypes*<br/>
[in]コントロールの種類を指定します。

*pRTC*<br/>
[in]カスタム ツールヒントのランタイム クラスです。

*pParams*<br/>
[in]ツールヒントのパラメーターです。

### <a name="remarks"></a>Remarks

このメソッドを設定、ランタイム クラスと最初のパラメーターを[CToolTipManager](../../mfc/reference/ctooltipmanager-class.md)ツールヒントを作成するときに使用します。 コントロールを呼び出すと[CTooltipManager::CreateToolTip](#createtooltip)ツールヒント内のパスである型で示される型のいずれかと*nTypes*、ツールヒント マネージャーのインスタンスであるツールヒント コントロールを作成する、指定されたランタイム クラス*pRTC*で指定されたパラメーターを渡す*pParams*新しいヒントにします。

このメソッドを呼び出すし、既存のすべてのツールヒントの所有者には、AFX_WM_UPDATETOOLTIPS メッセージが表示される、ツールヒントを使用して再作成する必要があります[CTooltipManager::CreateToolTip](#createtooltip)します。

*nTypes*する有効なツールヒントの任意の組み合わせの種類は、 [CTooltipManager::CreateToolTip](#createtooltip)使用方法、またはその AFX_TOOLTIP_TYPE_ALL をすることができます。 AFX_TOOLTIP_TYPE_ALL を渡すと、すべてのツール ヒントの種類に影響します。

### <a name="example"></a>例

次の例では、使用する方法、`SetTooltipParams`のメソッド、`CTooltipManager`クラス。 このコード スニペットは、「 [クライアント サンプルの描画](../../overview/visual-cpp-samples.md)」の一部です。

[!code-cpp[NVC_MFC_DrawClient#11](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]

##  <a name="settooltiptext"></a>  CTooltipManager::SetTooltipText

ツールヒントの説明テキストを設定します。

```
static void SetTooltipText(
    TOOLINFO* pTI,
    CToolTipCtrl* pToolTip,
    UINT nType,
    const CString strText,
    LPCTSTR lpszDescr=NULL);
```

### <a name="parameters"></a>パラメーター

*PTI*<br/>
[in]TOOLINFO オブジェクトへのポインター。

*pToolTip*<br/>
[入力、出力]テキストと説明を設定する対象のツールヒント コントロールへのポインター。

*nType*<br/>
[in]このツールヒントが関連付けられているコントロールの種類を指定します。

*strText*<br/>
[in]ツールヒントのテキストとして設定するテキスト。

*lpszDescr*<br/>
[in]ツールヒントの説明へのポインター。 NULL にすることができます。

### <a name="remarks"></a>Remarks

値 *%n タイプ*と同じ値である必要があります、 *%n タイプ*パラメーターの[CTooltipManager::CreateToolTip](#createtooltip)ツールヒントを作成するときにします。

##  <a name="updatetooltips"></a>  CTooltipManager::UpdateTooltips

詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。

```
void UpdateTooltips();
```

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolTipCtrl クラス](../../mfc/reference/cmfctooltipctrl-class.md)<br/>
[CMFCToolTipInfo クラス](../../mfc/reference/cmfctooltipinfo-class.md)
