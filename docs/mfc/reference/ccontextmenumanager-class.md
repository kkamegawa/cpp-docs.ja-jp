---
title: CContextMenuManager クラス
ms.date: 11/04/2016
f1_keywords:
- CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::AddMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuById
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuByName
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuNames
- AFXCONTEXTMENUMANAGER/CContextMenuManager::LoadState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ResetState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SaveState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SetDontCloseActiveMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ShowPopupMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::TrackPopupMenu
helpviewer_keywords:
- CContextMenuManager [MFC], CContextMenuManager
- CContextMenuManager [MFC], AddMenu
- CContextMenuManager [MFC], GetMenuById
- CContextMenuManager [MFC], GetMenuByName
- CContextMenuManager [MFC], GetMenuNames
- CContextMenuManager [MFC], LoadState
- CContextMenuManager [MFC], ResetState
- CContextMenuManager [MFC], SaveState
- CContextMenuManager [MFC], SetDontCloseActiveMenu
- CContextMenuManager [MFC], ShowPopupMenu
- CContextMenuManager [MFC], TrackPopupMenu
ms.assetid: 1de20640-243c-47e1-85de-1baa4153bc83
ms.openlocfilehash: c8a51a33c69b09d0ecd61520b5f1c9ff18c290a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182226"
---
# <a name="ccontextmenumanager-class"></a>CContextMenuManager クラス

`CContextMenuManager`オブジェクト管理ショートカット メニュー、コンテキスト メニューとも呼ばれます。

## <a name="syntax"></a>構文

```
class CContextMenuManager : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CContextMenuManager::CContextMenuManager](#ccontextmenumanager)|`CContextMenuManager` オブジェクトを構築します。|
|`CContextMenuManager::~CContextMenuManager`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CContextMenuManager::AddMenu](#addmenu)|新しいショートカット メニューを追加します。|
|[CContextMenuManager::GetMenuById](#getmenubyid)|指定されたリソース ID に関連付けられたメニューへのハンドルを返します|
|[CContextMenuManager::GetMenuByName](#getmenubyname)|指定されたメニュー名に一致するメニューにハンドルを返します。|
|[CContextMenuManager::GetMenuNames](#getmenunames)|メニュー名の一覧を返します。|
|[CContextMenuManager::LoadState](#loadstate)|Windows レジストリに格納されているショートカット メニューを読み込みます。|
|[CContextMenuManager::ResetState](#resetstate)|コンテキスト メニュー マネージャーからショートカット メニューをクリアします。|
|[CContextMenuManager::SaveState](#savestate)|ショートカット メニューを Windows レジストリに保存します。|
|[CContextMenuManager::SetDontCloseActiveMenu](#setdontcloseactivemenu)|コントロールかどうか、`CContextMenuManager`新しいショートカット メニューを表示するときに、active のショートカット メニューを閉じます。|
|[CContextMenuManager::ShowPopupMenu](#showpopupmenu)|指定したショートカット メニューを表示します。|
|[CContextMenuManager::TrackPopupMenu](#trackpopupmenu)|指定したショートカット メニューを表示します。 選択されたメニュー コマンドのインデックスを返します。|

## <a name="remarks"></a>Remarks

`CContextMenuManager` ショートカット メニューを管理、一貫した外観であることを確認します。

作成しないようにする、`CContextMenuManager`手動でのオブジェクトします。 アプリケーションのフレームワークを作成、`CContextMenuManager`オブジェクト。 ただし、呼び出す必要があります[CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager)アプリケーションが初期化されます。 コンテキスト マネージャーを初期化した後、メソッドを使用して、 [CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager)アプリケーションのコンテキスト マネージャーへのポインターを取得します。

実行時のショートカット メニューを作成するには呼び出すことによって`AddMenu`します。 最初の受信側のユーザー入力なしのメニューを表示する場合は、呼び出す`ShowPopupMenu`します。 `TrackPopupMenu` メニューを作成し、ユーザー入力を待機する場合に使用されます。 `TrackPopupMenu` ユーザーが何も選択せずに終了した場合は、選択したコマンドまたは 0 のインデックスを返します。

`CContextMenuManager`も保存して、Windows レジストリにその状態を読み込むことができます。

## <a name="example"></a>例

次の例では、メニューを追加する方法、`CContextMenuManager`オブジェクト、およびアクティブなポップアップ メニューを閉じる方法と、`CContextMenuManager`オブジェクトには、新しいポップアップ メニューが表示されます。 このコード スニペットの一部、[カスタム ページ サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CContextMenuManager`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcontextmenumanager.h

##  <a name="addmenu"></a>  CContextMenuManager::AddMenu

新しいショートカット メニューを追加、 [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)します。

```
BOOL AddMenu(
    UINT uiMenuNameResId,
    UINT uiMenuResId);

BOOL AddMenu(
    LPCTSTR lpszName,
    UINT uiMenuResId);
```

### <a name="parameters"></a>パラメーター

*uiMenuNameResId*<br/>
[in]新しいメニューの名前を含む文字列のリソース ID。

*uiMenuResId*<br/>
[in]メニューのリソース id です。

*lpszName*<br/>
[in]新しいメニューの名前を含む文字列。

### <a name="return-value"></a>戻り値

メソッドが成功した場合、0 以外の場合メソッドが失敗した場合は 0。

### <a name="remarks"></a>Remarks

このメソッドは失敗*uiMenuResId*が無効か、同じ名前の別のメニューに既に存在するかどうか、`CContextMenuManager`します。

##  <a name="ccontextmenumanager"></a>  CContextMenuManager::CContextMenuManager

構築、 [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)オブジェクト。

```
CContextMenuManager();
```

### <a name="remarks"></a>Remarks

ほとんどの場合、作成しないようにする、`CContextMenuManager`手動でします。 アプリケーションのフレームワークを作成、`CContextMenuManager`オブジェクト。 呼び出す必要があります[CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager)アプリケーションの初期化中にします。 コンテキスト マネージャーへのポインターを取得する[CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager)します。

##  <a name="getmenubyid"></a>  CContextMenuManager::GetMenuById

特定のリソース ID に関連付けられたメニューへのハンドルを返します

```
HMENU GetMenuById(UINT nMenuResId) const;
```

### <a name="parameters"></a>パラメーター

*nMenuResId*<br/>
[in]メニューのリソース ID。

### <a name="return-value"></a>戻り値

関連付けられているメニューへのハンドルまたは`NULL`メニューが見つからない場合。

##  <a name="getmenubyname"></a>  CContextMenuManager::GetMenuByName

特定のメニューのハンドルを返します。

```
HMENU GetMenuByName(
    LPCTSTR lpszName,
    UINT* puiOrigResID = NULL) const;
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
[in]取得するメニューの名前を含む文字列。

*puiOrigResID*<br/>
[out]UINT へのポインター。 このパラメーターには、指定されたメニューのリソース ID が含まれる場合が見つかりました。

### <a name="return-value"></a>戻り値

指定した名前に一致するメニューへのハンドルを*lpszName*します。 というメニューがない場合は NULL *lpszName*します。

### <a name="remarks"></a>Remarks

このメソッドに一致するメニューが検出されると*lpszName*、`GetMenuByName`パラメーターでメニュー リソース ID が格納されます*puiOrigResID*します。

##  <a name="getmenunames"></a>  CContextMenuManager::GetMenuNames

追加されたメニュー名の一覧を返します、 [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)します。

```
void GetMenuNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>パラメーター

*listOfNames*<br/>
[out]参照を[CStringList](../../mfc/reference/cstringlist-class.md)パラメーター。 このメソッドは、このパラメーターにメニュー名のリストを書き込みます。

##  <a name="loadstate"></a>  CContextMenuManager::LoadState

関連付けられている情報を読み込み、 [CContextMenuManager クラス](../../mfc/reference/ccontextmenumanager-class.md)Windows レジストリから。

```
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszProfileName*<br/>
[in]レジストリ キーの相対パスを含む文字列。

### <a name="return-value"></a>戻り値

メソッドが成功した場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

*LpszProfileName*パラメーターは、レジストリ エントリの絶対パスではありません。 アプリケーションの既定のレジストリ キーの末尾に追加する相対パスです。 取得または設定の既定のレジストリ キー、メソッドを使用して、 [CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase)と[CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase)それぞれします。

メソッドを使用して[CContextMenuManager::SaveState](#savestate)ショートカット メニューをレジストリに保存します。

##  <a name="resetstate"></a>  CContextMenuManager::ResetState

すべての項目に関連付けられているショートカット メニューから消去、 [CContextMenuManager クラス](../../mfc/reference/ccontextmenumanager-class.md)します。

```
virtual BOOL ResetState();
```

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。障害が発生した場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、ポップアップ メニューをクリアし、削除してから、`CContextMenuManager`します。

##  <a name="savestate"></a>  CContextMenuManager::SaveState

関連付けられている情報を保存、 [CContextMenuManager クラス](../../mfc/reference/ccontextmenumanager-class.md)Windows レジストリにします。

```
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszProfileName*<br/>
[in]レジストリ キーの相対パスを含む文字列。

### <a name="return-value"></a>戻り値

メソッドが成功した場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

*LpszProfileName*パラメーターは、レジストリ エントリの絶対パスではありません。 アプリケーションの既定のレジストリ キーの末尾に追加する相対パスです。 取得または設定の既定のレジストリ キー、メソッドを使用して、 [CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase)と[CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase)それぞれします。

メソッドを使用して[CContextMenuManager::LoadState](#loadstate)ショートカット メニューをレジストリから読み込めません。

##  <a name="setdontcloseactivemenu"></a>  CContextMenuManager::SetDontCloseActiveMenu

コントロールかどうか、 [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)新しいポップアップ メニューを表示するときに、アクティブなポップアップ メニューを閉じます。

```
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```

### <a name="parameters"></a>パラメーター

*bSet*<br/>
[in]アクティブなポップアップ メニューを閉じるかどうかを制御するブール型パラメーター。 TRUE の値は、アクティブなポップアップ メニューが閉じられていないことを示します。 FALSE は、アクティブなポップアップ メニューが閉じられたことを示します。

### <a name="remarks"></a>Remarks

既定で、`CContextMenuManager`アクティブなポップアップ メニューを閉じます。

##  <a name="showpopupmenu"></a>  CContextMenuManager::ShowPopupMenu

指定したショートカット メニューを表示します。

```
virtual BOOL ShowPopupMenu(
    UINT uiMenuResId,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bOwnMessage = FALSE,
    BOOL bRightAlign = FALSE);

virtual CMFCPopupMenu* ShowPopupMenu(
    HMENU hmenuPopup,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bOwnMessage = FALSE,
    BOOL bAutoDestroy = TRUE,
    BOOL bRightAlign = FALSE);
```

### <a name="parameters"></a>パラメーター

*uiMenuResId*<br/>
[in]このメソッドが表示されるメニューのリソース ID。

*x*<br/>
[in]水平方向のショートカット メニューのクライアント座標でのオフセットします。

*y*<br/>
[in]ショートカット メニューのクライアント座標の垂直方向のオフセット

*pWndOwner*<br/>
[in]ショートカット メニューの親ウィンドウへのポインター。

*bOwnMessage*<br/>
[in]メッセージのルーティング方法を示すブール値パラメーター。 場合*bOwnMessage* FALSE、標準の MFC は、ルーティングが使用されます。 それ以外の場合、 *pWndOwner*メッセージを受信します。

*hmenuPopup*<br/>
[in]このメソッドが表示されるメニューのハンドル。

*bAutoDestroy*<br/>
[in]メニューが自動的に破棄されるかどうかを示すブール値パラメーター。

*bRightAlign*<br/>
[in]メニュー項目を配置する方法を示すブール値パラメーター。 場合*bRightAlign*が true の場合、メニューが右から左への読み取り順序の右側に配置します。

### <a name="return-value"></a>戻り値

最初のメソッドのオーバー ロードは、メソッドが正常にメニューを表示する場合は 0 以外を返しますそれ以外の場合 0 を返します。 2 番目のメソッドのオーバー ロードへのポインターを返します[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)ショートカット メニューを表示は正しくそれ以外の場合は NULL です。

### <a name="remarks"></a>Remarks

このメソッドがメソッドに似ています[CContextMenuManager::TrackPopupMenu](#trackpopupmenu)ことで、両方の方法は、ショートカット メニューを表示します。 ただし、`TrackPopupMenu`選択されたメニュー コマンドのインデックスを返します。

場合、パラメーター *bAutoDestroy* false で、手動で呼び出す必要があります、継承された`DestroyMenu`メモリ リソースを解放します。 既定の実装`ShowPopupMenu`パラメーターを使用しない*bAutoDestroy*します。 派生したカスタム クラスの将来使用するために提供されている、`CContextMenuManager`クラス。

##  <a name="trackpopupmenu"></a>  CContextMenuManager::TrackPopupMenu

指定したショートカット メニューを表示し、選択したショートカット メニューのコマンドのインデックスを返します。

```
virtual UINT TrackPopupMenu(
    HMENU hmenuPopup,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bRightAlign = FALSE);
```

### <a name="parameters"></a>パラメーター

*hmenuPopup*<br/>
[in]このメソッドは、表示されるショートカット メニューのハンドル。

*x*<br/>
[in]水平方向のショートカット メニューのクライアント座標でのオフセットします。

*y*<br/>
[in]縦方向のショートカット メニューのクライアント座標のオフセットします。

*pWndOwner*<br/>
[in]ショートカット メニューの親ウィンドウへのポインター。

*bRightAlign*<br/>
[in]メニュー項目を配置する方法を示すブール値パラメーター。 場合*bRightAlign*が true の場合、メニューが右から左への読み取り順序の右側に配置します。 場合*bRightAlign* false で、メニューが左から右の読み取り順序の左側に配置します。

### <a name="return-value"></a>戻り値

ユーザーが選択したコマンドのメニュー コマンド IDユーザーがメニュー コマンドを選択することがなく、ショートカット メニューを閉じる場合は 0。

### <a name="remarks"></a>Remarks

このメソッドは、ショートカット メニューを表示するモーダル呼び出しとして機能します。 アプリケーションは、ユーザーは、ショートカット メニューを閉じるか、コマンドを選択したまでコード内の次の行には続行されません。 ショートカット メニューを表示する際、別のメソッドは[CContextMenuManager::ShowPopupMenu](#showpopupmenu)します。 メソッドは、モーダルの呼び出しではありませんし、選択したコマンドの ID は返されません。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx クラス](../../mfc/reference/cwinappex-class.md)
