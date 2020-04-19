---
title: CMouseManager クラス
ms.date: 11/04/2016
f1_keywords:
- CMouseManager
- AFXMOUSEMANAGER/CMouseManager
- AFXMOUSEMANAGER/CMouseManager::AddView
- AFXMOUSEMANAGER/CMouseManager::GetViewDblClickCommand
- AFXMOUSEMANAGER/CMouseManager::GetViewIconId
- AFXMOUSEMANAGER/CMouseManager::GetViewIdByName
- AFXMOUSEMANAGER/CMouseManager::GetViewNames
- AFXMOUSEMANAGER/CMouseManager::LoadState
- AFXMOUSEMANAGER/CMouseManager::SaveState
- AFXMOUSEMANAGER/CMouseManager::SetCommandForDblClk
helpviewer_keywords:
- CMouseManager [MFC], AddView
- CMouseManager [MFC], GetViewDblClickCommand
- CMouseManager [MFC], GetViewIconId
- CMouseManager [MFC], GetViewIdByName
- CMouseManager [MFC], GetViewNames
- CMouseManager [MFC], LoadState
- CMouseManager [MFC], SaveState
- CMouseManager [MFC], SetCommandForDblClk
ms.assetid: a4d05017-4e44-4a40-8b57-4ece0de20481
ms.openlocfilehash: f92a72e36fecbb39e57cbdf9583047aca0c1ebd5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338247"
---
# <a name="cmousemanager-class"></a>CMouseManager クラス

別のコマンドを関連付ける特定のユーザーは、 [CView](../../mfc/reference/cview-class.md)ユーザーがそのビューの内側でダブルクリックしたときのオブジェクトします。

## <a name="syntax"></a>構文

```
class CMouseManager : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMouseManager::AddView](#addview)|追加、`CView`オブジェクトを**カスタマイズ** ダイアログ ボックス。 **カスタマイズ**ダイアログ ボックスで、ユーザーに表示されているビューの各コマンドを使用して、ダブルクリックを関連付けます。|
|[CMouseManager::GetViewDblClickCommand](#getviewdblclickcommand)|ユーザーが指定されたビューの内側でダブルクリックしたときに実行されるコマンドを返します。|
|[CMouseManager::GetViewIconId](#getviewiconid)|指定されたビューの ID に関連付けられているアイコンを返します|
|[CMouseManager::GetViewIdByName](#getviewidbyname)|指定されたビュー名に関連付けられたビュー ID を返します。|
|[CMouseManager::GetViewNames](#getviewnames)|すべての追加のビュー名の一覧を取得します。|
|[CMouseManager::LoadState](#loadstate)|読み込み、 `CMouseManager` Windows レジストリから状態。|
|[CMouseManager::SaveState](#savestate)|書き込み、 `CMouseManager` Windows レジストリの状態。|
|[CMouseManager::SetCommandForDblClk](#setcommandfordblclk)|指定されたコマンドと、指定されたビューに関連付けます。|

## <a name="remarks"></a>Remarks

`CMouseManager`クラスのコレクションを保持する`CView`オブジェクト。 それぞれのビューが名前と ID で識別されます。 これらのビューに表示されます、**カスタマイズ** ダイアログ ボックス。 ユーザーがを通じて任意のビューに関連付けられているコマンドを変更できる、**カスタマイズ** ダイアログ ボックス。 関連付けられているコマンドは、そのビューで、ユーザーがダブルクリックしたときに実行されます。 コーディングという観点からこれをサポートするしたメッセージと呼び出しを処理する必要があります、 [CWinAppEx::OnViewDoubleClick](../../mfc/reference/cwinappex-class.md#onviewdoubleclick)をコード内の関数`CView`オブジェクト.

作成しないようにする、`CMouseManager`手動でのオブジェクトします。 アプリケーションのフレームワークによって作成されます。 それも破棄されます自動的に、ユーザーがアプリケーションを終了するときにします。 アプリケーションのマウス マネージャーへのポインターを取得する[CWinAppEx::GetMouseManager](../../mfc/reference/cwinappex-class.md#getmousemanager)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMouseManager`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxmousemanager.h

##  <a name="addview"></a>  CMouseManager::AddView

登録、 [CView](../../mfc/reference/cview-class.md)オブジェクトを[CMouseManager クラス](../../mfc/reference/cmousemanager-class.md)カスタム マウス動作をサポートします。

```
BOOL AddView(
    int iViewId,
    UINT uiViewNameResId,
    UINT uiIconId = 0);

BOOL AddView(
    int iId,
    LPCTSTR lpszViewName,
    UINT uiIconId = 0);
```

### <a name="parameters"></a>パラメーター

*iViewId*<br/>
[in]ビューの id。

*uiViewNameResId*<br/>
[in]ビュー名を参照するリソースの文字列 ID。

*uiIconId*<br/>
[in]ビューのアイコンの id。

*iId*<br/>
[in]ビューの id。

*lpszViewName*<br/>
[in]ビューの名前。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

カスタムのマウスの動作をサポートするためにビューに登録する必要があります、`CMouseManager`オブジェクト。 派生した任意のオブジェクト、`CView`マウス マネージャー クラスに登録することができます。 文字列および、ビューに関連付けられたアイコンが表示されます、**マウス**のタブ、**カスタマイズ** ダイアログ ボックス。

作成してなどビュー Id を保守するプログラマの役目です*iViewId*と*iId*します。

マウスのカスタム動作を提供する方法の詳細については、次を参照してください。[キーボードとマウスのカスタマイズ](../../mfc/keyboard-and-mouse-customization.md)します。

### <a name="example"></a>例

次の例へのポインターを取得する方法を示します、`CMouseManager`オブジェクトを使用して、`CWinAppEx::GetMouseManager`メソッドと`AddView`メソッドで、`CMouseManager`クラス。 このコード スニペットの一部、[状態コレクション サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_StateCollection#4](../../mfc/reference/codesnippet/cpp/cmousemanager-class_1.cpp)]

##  <a name="getviewdblclickcommand"></a>  CMouseManager::GetViewDblClickCommand

ユーザーが指定されたビューの内側でダブルクリックしたときに実行されるコマンドを返します。

```
UINT GetViewDblClickCommand(int iId) const;
```

### <a name="parameters"></a>パラメーター

*iId*<br/>
[in]ビューの id。

### <a name="return-value"></a>戻り値

ビューが; コマンドを使用して関連付けられている場合は、コマンド識別子それ以外の場合 0 を返します。

##  <a name="getviewiconid"></a>  CMouseManager::GetViewIconId

ビューの ID に関連付けられたアイコンを取得します

```
UINT GetViewIconId(int iViewId) const;
```

### <a name="parameters"></a>パラメーター

*iViewId*<br/>
[in]ビューの id。

### <a name="return-value"></a>戻り値

成功した場合は、アイコン リソースの識別子それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

使用して、ビューが最初に登録されていない場合、このメソッドは失敗[CMouseManager::AddView](#addview)します。

##  <a name="getviewidbyname"></a>  CMouseManager::GetViewIdByName

ビュー名に関連付けられたビュー ID を取得します。

```
int GetViewIdByName(LPCTSTR lpszName) const;
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
[in]ビューの名前。

### <a name="return-value"></a>戻り値

成功した場合は、ビュー IDそれ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

このメソッドを使用して登録されているビューを検索[CMouseManager::AddView](#addview)します。

##  <a name="getviewnames"></a>  CMouseManager::GetViewNames

すべての登録済みのビュー名の一覧を取得します。

```
void GetViewNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>パラメーター

*listOfNames*<br/>
[out]参照を`CStringList`オブジェクト。

### <a name="remarks"></a>Remarks

このメソッドによって、パラメーター`listOfNames`を使用して登録されているすべてのビューの名前を持つ[CMouseManager::AddView](#addview)します。

##  <a name="loadstate"></a>  CMouseManager::LoadState

状態を読み込みます、 [CMouseManager クラス](../../mfc/reference/cmousemanager-class.md)レジストリから。

```
BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszProfileName*<br/>
[in]レジストリ キーのパス。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

レジストリから読み込まれた状態の情報には、登録済みのビュー、ビューの識別子、および関連するコマンドが含まれています。 場合、パラメーター *lpszProfileName*が null の場合、この関数の読み込み、`CMouseManager`によって制御される既定のレジストリの場所からデータを[CWinAppEx クラス](../../mfc/reference/cwinappex-class.md)します。

ほとんどの場合、この関数を直接呼び出すにはありません。 ワークスペースの初期化プロセスの一部として呼び出されます。 ワークスペースの初期化プロセスの詳細については、次を参照してください。 [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate)します。

##  <a name="savestate"></a>  CMouseManager::SaveState

状態を書き込み、 [CMouseManager クラス](../../mfc/reference/cmousemanager-class.md)をレジストリにします。

```
BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszProfileName*<br/>
[in]レジストリ キーのパス。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

レジストリに書き込まれた状態の情報には、登録されているすべてのビュー、ビューの識別子、および関連するコマンドが含まれています。 場合、パラメーター *lpszProfileName* NULL の場合は、この関数を書き込みます、`CMouseManager`によって制御される既定のレジストリの場所にデータ、 [CWinAppEx クラス](../../mfc/reference/cwinappex-class.md)します。

ほとんどの場合、この関数を直接呼び出すにはありません。 ワークスペースのシリアル化プロセスの一部として呼び出されます。 ワークスペースのシリアル化プロセスの詳細については、次を参照してください。 [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate)します。

##  <a name="setcommandfordblclk"></a>  CMouseManager::SetCommandForDblClk

カスタム コマンドをマウス manager に最初に登録されているビューに関連付けます。

```
void SetCommandForDblClk(
    int iViewId,
    UINT uiCmd);
```

### <a name="parameters"></a>パラメーター

*iViewId*<br/>
[in]ビューの識別子です。

*uiCmd*<br/>
[in]コマンドの識別子です。

### <a name="remarks"></a>Remarks

ビューを使用してカスタム コマンドを関連付けるためにする必要があります最初、ビューを使用して登録[CMouseManager::AddView](#addview)します。 `AddView`メソッドには、入力パラメーターとしてビュー識別子が必要です。 ビューを登録すると呼び出す`CMouseManager::SetCommandForDblClk`を同じビュー識別子入力パラメーターに指定した`AddView`します。 その後、ユーザーが登録されているビューでマウスをダブルクリックしたときに、アプリケーションはコマンドを実行、によって示される*uiCmd します。* カスタムのマウスの動作をサポートするためには、マウスのマネージャーに登録されているビューをカスタマイズする必要があります。 カスタムのマウスの動作の詳細については、次を参照してください。[キーボードとマウスのカスタマイズ](../keyboard-and-mouse-customization.md)します。

場合*uiCmd*設定は 0 に指定されたビューは、コマンドに関連付けられて不要になった。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx クラス](../../mfc/reference/cwinappex-class.md)<br/>
[キーボードとマウスのカスタマイズ](../../mfc/keyboard-and-mouse-customization.md)
