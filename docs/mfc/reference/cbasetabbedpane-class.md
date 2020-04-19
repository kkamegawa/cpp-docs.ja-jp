---
title: CBaseTabbedPane クラス
ms.date: 11/04/2016
f1_keywords:
- CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::AddTab
- AFXBASETABBEDPANE/CBaseTabbedPane::AllowDestroyEmptyTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::ApplyRestoredTabInfo
- AFXBASETABBEDPANE/CBaseTabbedPane::CanFloat
- AFXBASETABBEDPANE/CBaseTabbedPane::CanSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::ConvertToTabbedDocument
- AFXBASETABBEDPANE/CBaseTabbedPane::DetachPane
- AFXBASETABBEDPANE/CBaseTabbedPane::EnableSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::FillDefaultTabsOrderArray
- AFXBASETABBEDPANE/CBaseTabbedPane::FindBarByTabNumber
- AFXBASETABBEDPANE/CBaseTabbedPane::FindPaneByID
- AFXBASETABBEDPANE/CBaseTabbedPane::FloatTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetDefaultTabsOrder
- AFXBASETABBEDPANE/CBaseTabbedPane::GetFirstVisibleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetMinSize
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneIcon
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneList
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabArea
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::GetUnderlyingWindow
- AFXBASETABBEDPANE/CBaseTabbedPane::GetVisibleTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::HasAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::IsHideSingleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::RecalcLayout
- AFXBASETABBEDPANE/CBaseTabbedPane::RemovePane
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoDestroy
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::ShowTab
helpviewer_keywords:
- CBaseTabbedPane [MFC], AddTab
- CBaseTabbedPane [MFC], AllowDestroyEmptyTabbedPane
- CBaseTabbedPane [MFC], ApplyRestoredTabInfo
- CBaseTabbedPane [MFC], CanFloat
- CBaseTabbedPane [MFC], CanSetCaptionTextToTabName
- CBaseTabbedPane [MFC], ConvertToTabbedDocument
- CBaseTabbedPane [MFC], DetachPane
- CBaseTabbedPane [MFC], EnableSetCaptionTextToTabName
- CBaseTabbedPane [MFC], FillDefaultTabsOrderArray
- CBaseTabbedPane [MFC], FindBarByTabNumber
- CBaseTabbedPane [MFC], FindPaneByID
- CBaseTabbedPane [MFC], FloatTab
- CBaseTabbedPane [MFC], GetDefaultTabsOrder
- CBaseTabbedPane [MFC], GetFirstVisibleTab
- CBaseTabbedPane [MFC], GetMinSize
- CBaseTabbedPane [MFC], GetPaneIcon
- CBaseTabbedPane [MFC], GetPaneList
- CBaseTabbedPane [MFC], GetTabArea
- CBaseTabbedPane [MFC], GetTabsNum
- CBaseTabbedPane [MFC], GetUnderlyingWindow
- CBaseTabbedPane [MFC], GetVisibleTabsNum
- CBaseTabbedPane [MFC], HasAutoHideMode
- CBaseTabbedPane [MFC], IsHideSingleTab
- CBaseTabbedPane [MFC], RecalcLayout
- CBaseTabbedPane [MFC], RemovePane
- CBaseTabbedPane [MFC], SetAutoDestroy
- CBaseTabbedPane [MFC], SetAutoHideMode
- CBaseTabbedPane [MFC], ShowTab
ms.assetid: f22c0080-5b29-4a0a-8f74-8f0a4cd2dbcf
ms.openlocfilehash: d7ffaa7274a8ed12944cdbc5dcbbdcb8fd3fd2b9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388593"
---
# <a name="cbasetabbedpane-class"></a>CBaseTabbedPane クラス

[CDockablePane Class](../../mfc/reference/cdockablepane-class.md) の機能を拡張して、タブ付きウィンドウの作成をサポートします。

## <a name="syntax"></a>構文

```
class CBaseTabbedPane : public CDockablePane
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|`CBaseTabbedPane::CBaseTabbedPane`|既定のコンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CBaseTabbedPane::AddTab](#addtab)|タブ付きペインに新しいタブを追加します。|
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|空のタブ付きペインを破棄するかどうかを指定します。|
|[CBaseTabbedPane::ApplyRestoredTabInfo](#applyrestoredtabinfo)|タブ付きペインに、レジストリから読み込まれるタブの設定を適用します。|
|[CBaseTabbedPane::CanFloat](#canfloat)|ペインをフローティングできるかどうかを判断します。 (上書き[CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat))。|
|[CBaseTabbedPane::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|タブ付きペインのキャプションがアクティブなタブとして、同じテキストを表示する必要があるかどうかを判断します。|
|[CBaseTabbedPane::ConvertToTabbedDocument](#converttotabbeddocument)|(上書き[CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument))。|
|[CBaseTabbedPane::DetachPane](#detachpane)|1 つまたは複数のドッキング可能ペインをタブ付き MDI ドキュメントに変換します。|
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|有効またはアクティブなタブにラベルのテキストとキャプション テキストを同期するタブ付きペインの機能を無効にします。|
|[CBaseTabbedPane::FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|内部のタブ オーダーは、既定の状態に復元します。|
|[CBaseTabbedPane::FindBarByTabNumber](#findbarbytabnumber)|タブの 0 から始まるインデックスを使用して、タブが識別されるタブにあるペインを返します。|
|||
|[CBaseTabbedPane::FindPaneByID](#findpanebyid)|ペインの ID によって識別されるペインを返します|
|[CBaseTabbedPane::FloatTab](#floattab)|現在ペインが切り離し可能なタブに存在する場合のみ、そのペインを切り離して表示します。|
|[CBaseTabbedPane::GetDefaultTabsOrder](#getdefaulttabsorder)|ウィンドウでタブの既定の順序を返します。|
|[CBaseTabbedPane::GetFirstVisibleTab](#getfirstvisibletab)|最初に表示されているタブへのポインターを取得します。|
|[CBaseTabbedPane::GetMinSize](#getminsize)|ウィンドウのサイズが許容される最小を取得します。 (上書き[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize))。|
|[CBaseTabbedPane::GetPaneIcon](#getpaneicon)|ウィンドウ アイコンへのハンドルを返します。 (上書き[CBasePane::GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon))。|
|[CBaseTabbedPane::GetPaneList](#getpanelist)|タブ付きペインの含まれるペインの一覧を返します。|
|[CBaseTabbedPane::GetTabArea](#gettabarea)|上部と下部のタブ領域に外接する四角形を返します。|
|[CBaseTabbedPane::GetTabsNum](#gettabsnum)|タブのウィンドウでタブの数を返します。|
|[CBaseTabbedPane::GetUnderlyingWindow](#getunderlyingwindow)|基になる (ラップされた) タブ ウィンドウを取得します。|
|[CBaseTabbedPane::GetVisibleTabsNum](#getvisibletabsnum)|表示されるタブの数を返します。|
|[CBaseTabbedPane::HasAutoHideMode](#hasautohidemode)|タブ付きウィンドウが自動的に隠すモードに切り替えられるかどうかを判断します。|
|[CBaseTabbedPane::IsHideSingleTab](#ishidesingletab)|1 つのタブが表示されている場合のみ、タブ付きウィンドウが非表示かどうかを判断します。|
|`CBaseTabbedPane::LoadSiblingPaneIDs`|シリアル化中に内部的に使用します。|
|[CBaseTabbedPane::RecalcLayout](#recalclayout)|ウィンドウのレイアウト情報を再計算します。 (上書き[cpane::recalclayout](../../mfc/reference/cpane-class.md#recalclayout))。|
|[CBaseTabbedPane::RemovePane](#removepane)|タブ付きペインから、ウィンドウを削除します。|
|`CBaseTabbedPane::SaveSiblingBarIDs`|シリアル化中に内部的に使用します。|
|`CBaseTabbedPane::Serialize`|(上書き[cdockablepane::serialize](cdockablepane-class.md))。|
|`CBaseTabbedPane::SerializeTabWindow`|シリアル化中に内部的に使用します。|
|[CBaseTabbedPane::SetAutoDestroy](#setautodestroy)|タブ形式のコントロール バーを自動的に破棄されるかどうかを判断します。|
|[CBaseTabbedPane::SetAutoHideMode](#setautohidemode)|ドッキング ペインの間の表示の切り替えと自動非表示モード。 (上書き[CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode))。|
|[CBaseTabbedPane::ShowTab](#showtab)|タブの表示と非表示を切り替えます。|

## <a name="remarks"></a>Remarks

このクラスは抽象クラスであり、インスタンス化することはできません。 タブ付きペインのすべての種類に共通するサービスを実装します。

現時点では、ライブラリには、2 つのタブ付きペインを派生クラスが含まれています。[CTabbedPane クラス](../../mfc/reference/ctabbedpane-class.md)と[CMFCOutlookBar クラス](../../mfc/reference/cmfcoutlookbar-class.md)します。

A`CBaseTabbedPane`オブジェクトへのポインターをラップする、 [CMFCBaseTabCtrl クラス](../../mfc/reference/cmfcbasetabctrl-class.md)オブジェクト。 [CMFCBaseTabCtrl クラス](../../mfc/reference/cmfcbasetabctrl-class.md)タブ付きウィンドウの子ウィンドウになります。

タブ付きペインを作成する方法の詳細については、次を参照してください。 [CDockablePane クラス](../../mfc/reference/cdockablepane-class.md)、 [CTabbedPane クラス](../../mfc/reference/ctabbedpane-class.md)、および[CMFCOutlookBar クラス](../../mfc/reference/cmfcoutlookbar-class.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

`CBaseTabbedPane`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxBaseTabbedPane.h

##  <a name="addtab"></a>  CBaseTabbedPane::AddTab

タブ付きペインに新しいタブを追加します。

```
virtual BOOL AddTab(
    CWnd* pNewBar,
    BOOL bVisible = TRUE,
    BOOL bSetActive = TRUE,
    BOOL bDetachable = TRUE);
```

### <a name="parameters"></a>パラメーター

*pNewBar*<br/>
[入力、出力]追加するウィンドウへのポインター。 このメソッドを呼び出した後、このポインターが無効になる可能性があります。 詳細については、「解説」を参照してください。

*bVisible*<br/>
[in]タブが表示されるようにする場合は TRUEそれ以外の場合、FALSE です。

*bSetActive*<br/>
[in]アクティブなタブ、タブを作成する場合は TRUEそれ以外の場合、FALSE です。

*bDetachable*<br/>
[in]タブをデタッチできるようにする場合は TRUEそれ以外の場合、FALSE です。

### <a name="return-value"></a>戻り値

TRUE の場合、ウィンドウのタブとして正常に追加され、プロセスが破棄されません。 追加されるウィンドウが型のオブジェクトである場合は FALSE`CBaseTabbedPane`します。 詳細については、「解説」を参照してください。

### <a name="remarks"></a>Remarks

ペインをタブ付きペインに新しいタブとして追加するには、このメソッドを呼び出します。 場合*pNewBar*型のオブジェクトを指す`CBaseTabbedPane`、そのすべてのタブはタブ付きペインにコピーし、 *pNewBar*が破棄されます。 したがって、 *pNewBar*に無効なポインターになり、使用する必要があります。

##  <a name="allowdestroyemptytabbedpane"></a>  CBaseTabbedPane::AllowDestroyEmptyTabbedPane

空のタブ付きペインを破棄するかどうかを指定します。

```
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>戻り値

TRUE の場合、空のタブ付きペインを破棄することができます。それ以外の場合、FALSE です。 既定の実装を常に TRUE を返します。

### <a name="remarks"></a>Remarks

空のタブ付きウィンドウが破棄されるを許可されていない場合、フレームワークは、ウィンドウを代わりに表示されません。

##  <a name="applyrestoredtabinfo"></a>  CBaseTabbedPane::ApplyRestoredTabInfo

タブの設定をレジストリから読み込むし、タブ付きウィンドウに適用します。

```
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```

### <a name="parameters"></a>パラメーター

*bUseTabIndexes*<br/>
[in]このパラメーターは、フレームワークによって内部的に使用されます。

### <a name="remarks"></a>Remarks

レジストリからドッキング状態情報を再読み込み時に、このメソッドは、フレームワークによって呼び出されます。 メソッドは、タブ オーダーとタブ付きウィンドウのタブ名に関する情報を取得します。

##  <a name="canfloat"></a>  CBaseTabbedPane::CanFloat

タブ付きペインをフローティングできるかどうかを指定します。

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>戻り値

ペインをフローティングできる場合は TRUE。それ以外の場合、FALSE です。

##  <a name="cansetcaptiontexttotabname"></a>  CBaseTabbedPane::CanSetCaptionTextToTabName

タブ付きペインのキャプションがアクティブなタブとして、同じテキストを表示する必要があるかどうかを判断します。

```
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>戻り値

アクティブなタブのテキストにタブ付きペインのキャプションのテキストが設定されている場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

タブ付きペインのキャプションで表示されるテキストが、アクティブなタブのラベルを使用するかどうかを判断するメソッドが使用されます。有効にするまたは呼び出すことによってこの機能を無効にすることができます[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)します。

##  <a name="converttotabbeddocument"></a>  CBaseTabbedPane::ConvertToTabbedDocument

1 つまたは複数のドッキング可能ペインをタブ付き MDI ドキュメントに変換します。

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>パラメーター

*bActiveTabOnly*<br/>
[in]タブ付きペインを変換するときに、アクティブなタブのみを変換する場合は TRUE を指定します。ペイン内のすべてのタブに変換する場合は FALSE を指定します。

##  <a name="detachpane"></a>  CBaseTabbedPane::DetachPane

タブ付きウィンドウから、ウィンドウをデタッチします。

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>パラメーター

*pBar*<br/>
[in]デタッチするウィンドウへのポインター。

*bHide*<br/>
[in]フレームワークに、ウィンドウが非表示にデタッチされる後かどうかを指定するブール型パラメーター。

### <a name="return-value"></a>戻り値

フレームワークが正常にウィンドウ; をデタッチする場合は TRUE。場合は FALSE *pBar*が NULL またはタブ付きペインになっているペインを参照します。

### <a name="remarks"></a>Remarks

フレームワークは、可能であれば、デタッチされたウィンドウをフローティングします。 詳細については、次を参照してください。 [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)します。

##  <a name="enablesetcaptiontexttotabname"></a>  CBaseTabbedPane::EnableSetCaptionTextToTabName

有効またはアクティブなタブにラベルのテキストとキャプション テキストを同期するタブ付きペインの機能を無効にします。

```
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
[in]タブ付きペインのキャプションをアクティブなタブのキャプションと同期する場合は TRUEそれ以外の場合、FALSE です。

##  <a name="filldefaulttabsorderarray"></a>  CBaseTabbedPane::FillDefaultTabsOrderArray

内部のタブ オーダーは、既定の状態に復元します。

```
void FillDefaultTabsOrderArray();
```

### <a name="remarks"></a>Remarks

このメソッドは、フレームワーク Outlook バーを初期状態に復元するときに呼び出されます。

##  <a name="findpanebyid"></a>  CBaseTabbedPane::FindPaneByID

ペインの ID で識別されるペインを返します

```
virtual CWnd* FindPaneByID(UINT uBarID);
```

### <a name="parameters"></a>パラメーター

*uBarID*<br/>
[in]検索する、ウィンドウの ID を指定します。

### <a name="return-value"></a>戻り値

見つかった場合は、ウィンドウへのポインターそれ以外の場合は NULL です。

### <a name="remarks"></a>Remarks

このメソッドは、ペイン内のすべてのタブを比較しで指定された ID を持つ 1 つ返されます、 *uBarID*パラメーター。

##  <a name="findbarbytabnumber"></a>  CBaseTabbedPane::FindBarByTabNumber

タブ内にあるペインを返します。

```
virtual CWnd* FindBarByTabNumber(
    int nTabNum,
    BOOL bGetWrappedBar = FALSE);
```

### <a name="parameters"></a>パラメーター

*nTabNum*<br/>
[in]取得するタブの 0 から始まるインデックスを指定します。

*bGetWrappedBar*<br/>
[in]ペイン自体ではなく、ウィンドウの基になる (ラップされた) ウィンドウを取得する場合は TRUEそれ以外の場合は FALSE です。 派生したペインにのみ適用されますこの[CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)します。

### <a name="return-value"></a>戻り値

検索対象 ペインに有効なポインターが返されます。 その後、ウィンドウが見つかった場合それ以外の場合は NULL です。

### <a name="remarks"></a>Remarks

指定されたタブ内に存在するウィンドウを取得するには、このメソッドを呼び出して、 *nTabNum*パラメーター。

##  <a name="floattab"></a>  CBaseTabbedPane::FloatTab

現在ペインが切り離し可能なタブに存在する場合のみ、そのペインを切り離して表示します。

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>パラメーター

*pBar*<br/>
[入力、出力]Float 型に、ウィンドウへのポインター。

*nTabID*<br/>
[in]Float 型に、タブの 0 から始まるインデックスを指定します。

*dockMethod*<br/>
[in]使用して、ペインをフローティングするメソッドを指定します。 詳細については、「解説」を参照してください。

*bHide*<br/>
[in]フローティングする前に、ウィンドウを非表示にする場合は TRUEそれ以外の場合、FALSE です。

### <a name="return-value"></a>戻り値

ウィンドウをフローティング状態の場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

切り離し可能なタブに現在あるペインをフローティングするには、このメソッドを呼び出します。

ウィンドウをプログラムからデタッチする場合は、指定の DM_SHOW、 *dockMethod*パラメーター。 ここにフロート以前と同じ位置にウィンドウをフローティングする場合は、指定として DM_DBL_CLICK、 *dockMethod*パラメーター。

##  <a name="getdefaulttabsorder"></a>  CBaseTabbedPane::GetDefaultTabsOrder

ウィンドウでタブの既定の順序を返します。

```
const CArray<int,int>& GetDefaultTabsOrder();
```

### <a name="return-value"></a>戻り値

A`CArray`のウィンドウでタブの既定の順序を指定するオブジェクト。

### <a name="remarks"></a>Remarks

フレームワークは、Outlook バーが初期状態にリセットされると、このメソッドを呼び出します。

##  <a name="getfirstvisibletab"></a>  CBaseTabbedPane::GetFirstVisibleTab

最初に表示されているタブへのポインターを取得します。

```
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```

### <a name="parameters"></a>パラメーター

*iTabNum*<br/>
[in]整数への参照。 このメソッド最初に表示されているタブの 0 から始まるインデックスをこのパラメーターは、または書き込みます-1 表示されていない場合 タブが見つかった。

### <a name="return-value"></a>戻り値

成功した場合、最初に表示されているタブへのポインターそれ以外の場合は NULL です。

##  <a name="getminsize"></a>  CBaseTabbedPane::GetMinSize

ウィンドウのサイズが許容される最小を取得します。

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>パラメーター

*size*<br/>
[out]A`CSize`サイズが許容される最小で塗りつぶされているオブジェクト。

### <a name="remarks"></a>Remarks

ウィンドウの最小サイズの一貫性のある処理がアクティブな場合 ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize))、*サイズ*はアクティブなタブのサイズが許容される最小で塗りつぶされます。それ以外の場合、*サイズ*の戻り値が入力[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)します。

##  <a name="getpaneicon"></a>  CBaseTabbedPane::GetPaneIcon

ウィンドウのサイズが許容される最小を取得します。

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>パラメーター

*size*<br/>
[out]A`CSize`サイズが許容される最小で塗りつぶされているオブジェクト。

### <a name="remarks"></a>Remarks

ウィンドウの最小サイズの一貫性のある処理がアクティブな場合 ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize))、*サイズ*はアクティブなタブのサイズが許容される最小で塗りつぶされます。それ以外の場合、*サイズ*の戻り値が入力[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)します。

##  <a name="getpanelist"></a>  CBaseTabbedPane::GetPaneList

タブ付きペインの含まれるペインの一覧を返します。

```
virtual void GetPaneList(
    CObList& lst,
    CRuntimeClass* pRTCFilter = NULL);
```

### <a name="parameters"></a>パラメーター

*lst*<br/>
[out]A`CObList`タブ付きペインの含まれるペインが格納されます。

*pRTCFilter*<br/>
[in]NULL でない場合、返された一覧には、指定されたランタイム クラスはウィンドウのみが含まれています。

##  <a name="gettabarea"></a>  CBaseTabbedPane::GetTabArea

上部と下部のタブ領域に外接する四角形を返します。

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const = 0;
```

### <a name="parameters"></a>パラメーター

*rectTabAreaTop*<br/>
[out]上部のタブ領域の画面座標を受け取ります。

*rectTabAreaBottom*<br/>
[out]下のタブ領域の画面座標を受け取ります。

### <a name="remarks"></a>Remarks

外接する四角形の上限と下限のタブ領域に、画面座標を判断するには、このメソッドを呼び出します。

##  <a name="gettabsnum"></a>  CBaseTabbedPane::GetTabsNum

タブのウィンドウでタブの数を返します。

```
virtual int GetTabsNum() const;
```

### <a name="return-value"></a>戻り値

タブ付きウィンドウのタブの数。

##  <a name="getunderlyingwindow"></a>  CBaseTabbedPane::GetUnderlyingWindow

基になる (ラップされた) タブ ウィンドウを取得します。

```
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```

### <a name="return-value"></a>戻り値

基になるタブ ウィンドウへのポインター。

##  <a name="getvisibletabsnum"></a>  CBaseTabbedPane::GetVisibleTabsNum

表示されるタブの数を返します。

```
virtual int GetVisibleTabsNum() const;
```

### <a name="return-value"></a>戻り値

大きいまたは 0 に等しいとなる、表示されるタブの数。

### <a name="remarks"></a>Remarks

タブ付きペインに表示されるタブの数を決定するには、このメソッドを呼び出します。

##  <a name="hasautohidemode"></a>  CBaseTabbedPane::HasAutoHideMode

タブ付きペインを AutoHide モードに切り替えられるかどうかを判断します。

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>戻り値

ウィンドウを隠すモードに切り替えることができる場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

自動非表示モードが無効になっている場合は、タブ付きペインのキャプションにピン留めする ボタンは表示されません。

##  <a name="ishidesingletab"></a>  CBaseTabbedPane::IsHideSingleTab

1 つのタブが表示されている場合のみ、タブ付きウィンドウが非表示かどうかを判断します。

```
virtual BOOL IsHideSingleTab() const;
```

### <a name="return-value"></a>戻り値

1 つだけ表示されるタブがある場合に、タブ ウィンドウが表示されない場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

1 つだけのタブが開いているため、ウィンドウが表示されない場合は、タブ付きウィンドウが正しく動作しているかどうかを判断するには、このメソッドを呼び出すことができます。

##  <a name="removepane"></a>  CBaseTabbedPane::RemovePane

タブ付きペインから、ウィンドウを削除します。

```
virtual BOOL RemovePane(CWnd* pBar);
```

### <a name="parameters"></a>パラメーター

*pBar*<br/>
[入力、出力]タブ付きウィンドウから削除するウィンドウへのポインター。

### <a name="return-value"></a>戻り値

タブ付きウィンドウがまだ有効な場合と、ウィンドウはタブ付きペインから正常に削除された場合は TRUE です。 最後のウィンドウがタブ付きペインから削除され、タブ付きウィンドウが破棄される場合は FALSE。 戻り値が FALSE の場合は、使用しないでくださいタブ付きペインかを確認します。

### <a name="remarks"></a>Remarks

指定されたウィンドウを削除するには、このメソッドを呼び出して、 *pBar*タブ付きペインからパラメーター。

##  <a name="setautodestroy"></a>  CBaseTabbedPane::SetAutoDestroy

タブ形式のコントロール バーを自動的に破棄されるかどうかを判断します。

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>パラメーター

*bAutoDestroy*<br/>
[in]タブ付きペインを動的に作成されました。 有効期間を制御していない場合は TRUEそれ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

設定の自動破棄モードを TRUE に、タブ付きペインを動的に作成する場合、およびその有効期間を制御していない場合。 場合は自動破棄モードが TRUE で、タブ付きペインは、フレームワークによって自動的に破棄します。

##  <a name="showtab"></a>  CBaseTabbedPane::ShowTab

タブの表示と非表示を切り替えます。

```
virtual BOOL ShowTab(
    CWnd* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>パラメーター

*pBar*<br/>
[in]非表示ウィンドウへのポインター。

*bShow*<br/>
[in]ウィンドウを表示する場合は TRUEウィンドウを非表示には FALSE です。

*bDelay*<br/>
[in]タブ レイアウトの調整を遅延する場合は TRUEそれ以外の場合、FALSE です。

*bActivate*<br/>
[in]アクティブなタブ、タブを作成する場合は TRUEそれ以外の場合、FALSE です。

### <a name="return-value"></a>戻り値

タブの表示または非表示に正常にされた場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

ペインが表示または非表示の値に応じて、このメソッドを呼び出すときに、 *bShow*パラメーター。 タブを非表示にして、基になるタブ ウィンドウで、最後に表示されるタブは、タブ付きペインが表示されます。 含まれていない以前のタブ表示されているときにタブを表示する場合は、タブ付きペインが表示されます。

##  <a name="recalclayout"></a>  CBaseTabbedPane::RecalcLayout

ウィンドウのレイアウト情報を再計算します。

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Remarks

ウィンドウがフローティング状態の場合、このメソッドは、ミニフレームの現在のサイズには、ウィンドウのサイズを変更するためにフレームワークを通知します。

場合は、ウィンドウがドッキングされている場合、このメソッドは何もしません。

##  <a name="setautohidemode"></a>  CBaseTabbedPane::SetAutoHideMode

タブ付きペインに切り離し可能なウィンドウの自動非表示モードを設定します。

```
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,
    DWORD dwAlignment,
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,
    BOOL bUseTimer = TRUE);
```

### <a name="parameters"></a>パラメーター

*bMode*<br/>
[in]自動非表示モードを有効にする場合は TRUE通常のドッキング モードを有効にする場合は FALSE。

*dwAlignment*<br/>
[in]作成される自動非表示ウィンドウの配置を指定します。 使用可能な値の一覧は、次を参照してください。 [CPane::MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment)します。

*pCurrAutoHideBar*<br/>
[入力、出力]現在、自動的に隠すツールバーへのポインター。 NULL にすることができます。

*bUseTimer*<br/>
[in]ユーザーが自動的に隠すモードに、ウィンドウを切り替えるときに、自動非表示の効果を使用するか、すぐに、ウィンドウを非表示にするかどうかを指定します。

### <a name="return-value"></a>戻り値

ツールバーを作成していない場合は、自動非表示モード、または NULL に切り替えるときに作成される、自動的に隠すツールバーへのポインター。

### <a name="remarks"></a>Remarks

フレームワークは、ユーザーが [ピン留めする] ボタンを自動的に隠すモードまたは標準ドッキング モードには、タブ付きペインを切り替えるには、このメソッドを呼び出します。

タブ付きペインの切り離し可能な各ペインに自動的に隠すモードが設定されています。 切り離し不可能なペインは無視されます。 詳細については、次を参照してください。 [cmfcbasetabctrl::enabletabdetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach)します。

タブ付きペインをプログラムによって自動的に隠すモードに切り替えるには、このメソッドを呼び出します。 メイン フレーム ウィンドウに、ウィンドウをドッキングする必要があります ( [CDockablePane::GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider)への有効なポインターを返す必要があります、 [CPaneDivider](../../mfc/reference/cpanedivider-class.md))。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane クラス](../../mfc/reference/cdockablepane-class.md)
