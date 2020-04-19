---
title: CSnapInItemImpl クラス
ms.date: 11/04/2016
f1_keywords:
- CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::AddMenuItems
- ATLSNAP/ATL::CSnapInItemImpl::Command
- ATLSNAP/ATL::CSnapInItemImpl::CreatePropertyPages
- ATLSNAP/ATL::CSnapInItemImpl::FillData
- ATLSNAP/ATL::CSnapInItemImpl::GetResultPaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::GetResultViewType
- ATLSNAP/ATL::CSnapInItemImpl::GetScopePaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::Notify
- ATLSNAP/ATL::CSnapInItemImpl::QueryPagesFor
- ATLSNAP/ATL::CSnapInItemImpl::SetMenuInsertionFlags
- ATLSNAP/ATL::CSnapInItemImpl::SetToolbarButtonInfo
- ATLSNAP/ATL::CSnapInItemImpl::UpdateMenuState
- ATLSNAP/ATL::CSnapInItemImpl::UpdateToolbarButton
- ATLSNAP/ATL::CSnapInItemImpl::m_bstrDisplayName
- ATLSNAP/ATL::CSnapInItemImpl::m_resultDataItem
- ATLSNAP/ATL::CSnapInItemImpl::m_scopeDataItem
helpviewer_keywords:
- snap-ins, data items
- snap-ins, ATL support for
- CSnapInItemImpl class
- snap-ins
ms.assetid: 52caefbd-9eae-49b0-add2-d55524271aa7
ms.openlocfilehash: a9ebcf8827d79a9613ce14251d361dd607aa6af3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496557"
---
# <a name="csnapinitemimpl-class"></a>CSnapInItemImpl クラス

このクラスには、スナップインノードオブジェクトを実装するためのメソッドが用意されています。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <class T, BOOL bIsExtension = FALSE>
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
から`CSnapInItemImpl`派生したクラス。

*bIsExtension*<br/>
オブジェクトがスナップイン拡張である場合は TRUE。それ以外の場合は FALSE。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CSnapInItemImpl:: CSnapInItemImpl](#csnapinitemimpl)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CSnapInItemImpl:: AddMenuItems](#addmenuitems)|メニュー項目をコンテキストメニューに追加します。|
|[CSnapInItemImpl:: Command](#command)|カスタムメニュー項目が選択されたときにコンソールによって呼び出されます。|
|[CSnapInItemImpl:: CreatePropertyPages](#createpropertypages)|スナップインのプロパティシートにページを追加します。|
|[CSnapInItemImpl:: FillData](#filldata)|スナップインオブジェクトの情報を指定したストリームにコピーします。|
|[CSnapInItemImpl:: Getresultimpl Info](#getresultpaneinfo)|スナップインの構造を取得します。 `RESULTDATAITEM`|
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|結果ペインによって使用されるビューの種類を決定します。|
|[CSnapInItemImpl:: GetScopePaneInfo](#getscopepaneinfo)|スナップインの構造を取得します。 `SCOPEDATAITEM`|
|[CSnapInItemImpl:: Notify](#notify)|コンソールによって呼び出され、ユーザーによって実行されるアクションのスナップインを通知します。|
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|スナップインノードがプロパティページをサポートしているかどうかを確認するために呼び出されます。|
|[CSnapInItemImpl:: SetMenuInsertionFlags](#setmenuinsertionflags)|スナップインオブジェクトのメニュー挿入フラグを変更します。|
|[CSnapInItemImpl:: SetToolbarButtonInfo](#settoolbarbuttoninfo)|指定したツールバーボタンの情報を設定します。|
|[CSnapInItemImpl:: UpdateMenuState](#updatemenustate)|コンテキストメニュー項目の状態を更新します。|
|[CSnapInItemImpl:: UpdateToolbarButton](#updatetoolbarbutton)|指定したツールバーボタンの状態を更新します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|スナップインオブジェクトの名前。|
|[CSnapInItemImpl:: m_resultDataItem](#m_resultdataitem)|オブジェクトによって使用される Windows `RESULTDATAITEM`構造体。 `CSnapInItemImpl`|
|[CSnapInItemImpl:: m_scopeDataItem](#m_scopedataitem)|オブジェクトによって使用される Windows `SCOPEDATAITEM`構造体。 `CSnapInItemImpl`|

## <a name="remarks"></a>Remarks

`CSnapInItemImpl`メニュー項目やツールバーの追加、スナップインノードのコマンドの転送など、スナップインノードオブジェクトの基本的な実装を提供します。 これらの機能は、いくつかの異なるインターフェイスとマップの種類を使用して実装されます。 既定の実装では、派生クラスの正しいインスタンスを決定し、適切なインスタンスにメッセージを転送することによって、node オブジェクトに送信される通知を処理します。

## <a name="inheritance-hierarchy"></a>継承階層

`CSnapInItem`

`CSnapInItemImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsnap. h

##  <a name="addmenuitems"></a>  CSnapInItemImpl::AddMenuItems

このメソッドは、Win32 関数[IExtendContextMenu:: AddMenuItems](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-addmenuitems)を実装します。

```
AddMenuItems(
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>パラメーター

*piCallback*<br/>
からコンテキストメニューに`IContextMenuCallback`項目を追加できるへのポインター。

*許可された ppg tion*<br/>
[入力、出力]Microsoft 管理コンソール (MMC) で定義されている、使用可能なメニュー項目の挿入ポイントを識別します。 これは、次のフラグの組み合わせにすることができます。

- CCM_INSERTIONALLOWED_TOP 項目は、コンテキストメニューの上部に挿入できます。

- CCM_INSERTIONALLOWED_NEW の項目は、[新規作成] サブメニューに挿入できます。

- CCM_INSERTIONALLOWED_TASK の項目は、[タスク] サブメニューに挿入できます。

- CCM_INSERTIONALLOWED_VIEW Items は、ツールバーの [表示] メニュー、または結果ペインのコンテキストメニューの [表示] サブメニューで挿入できます。

*type*<br/>
からオブジェクトの種類を指定します。 次のいずれかの値を指定できます。

- スコープペインコンテキストの CCT_SCOPE Data オブジェクト。

- 結果ペインのコンテキストの CCT_RESULT Data オブジェクト。

- スナップインマネージャーコンテキストの CCT_SNAPIN_MANAGER Data オブジェクト。

- CCT_UNINITIALIZED Data オブジェクトに無効な型が含まれています。

##  <a name="command"></a>CSnapInItemImpl:: Command

このメソッドは、Win32 関数[IExtendContextMenu:: Command](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-command)を実装します。

```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>パラメーター

*lCommandID*<br/>
からメニュー項目のコマンド id を指定します。

*type*<br/>
からオブジェクトの種類を指定します。 次のいずれかの値を指定できます。

- スコープペインコンテキストの CCT_SCOPE Data オブジェクト。

- 結果ペインのコンテキストの CCT_RESULT Data オブジェクト。

- スナップインマネージャーコンテキストの CCT_SNAPIN_MANAGER Data オブジェクト。

- CCT_UNINITIALIZED Data オブジェクトに無効な型が含まれています。

##  <a name="createpropertypages"></a>CSnapInItemImpl:: CreatePropertyPages

このメソッドは、Win32 関数[IExtendPropertySheet:: CreatePropertyPages](/windows/win32/api/mmc/nn-mmc-iextendpropertysheet2)を実装します。

```
CreatePropertyPages(
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>パラメーター

*lpProvider*<br/>
からインターフェイスへの`IPropertySheetCallback`ポインター。

*handle*<br/>
からMMCN_PROPERTY_CHANGE 通知メッセージを適切なデータクラスにルーティングするために使用するハンドルを指定します。

*pUnk*<br/>
からノードに関する`IExtendPropertySheet`コンテキスト情報を格納しているオブジェクト上のインターフェイスへのポインター。

*type*<br/>
からオブジェクトの種類を指定します。 次のいずれかの値を指定できます。

- スコープペインコンテキストの CCT_SCOPE Data オブジェクト。

- 結果ペインのコンテキストの CCT_RESULT Data オブジェクト。

- スナップインマネージャーコンテキストの CCT_SNAPIN_MANAGER Data オブジェクト。

- CCT_UNINITIALIZED Data オブジェクトに無効な型が含まれています。

##  <a name="csnapinitemimpl"></a>CSnapInItemImpl:: CSnapInItemImpl

`CSnapInItemImpl` オブジェクトを構築します。

```
CSnapInItemImpl();
```

##  <a name="filldata"></a>CSnapInItemImpl:: FillData

この関数は、項目に関する情報を取得するために呼び出されます。

```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```

### <a name="parameters"></a>パラメーター

*cf*<br/>
からクリップボードの形式 (テキスト、リッチテキスト、または OLE 項目を含むリッチテキスト)。

*pStream*<br/>
からオブジェクトデータを格納しているストリームへのポインター。

### <a name="remarks"></a>Remarks

この関数を適切に実装するには、 *cf*で示されたクリップボードの形式に応じて、正しい情報をストリーム (*pstream*) にコピーします。

##  <a name="getresultviewtype"></a>  CSnapInItemImpl::GetResultViewType

スナップインオブジェクトの結果ペインのビューの種類を取得するには、この関数を呼び出します。

```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```

### <a name="parameters"></a>パラメーター

*ppViewType*<br/>
入出力返されたビュー型のアドレスへのポインター。

*pViewOptions*<br/>
入出力MMC_VIEW_OPTIONS 列挙体へのポインター。コンソールには、所有しているスナップインによって指定されたオプションが用意されています。 この値には、次のいずれかを指定できます。

- MMC_VIEW_OPTIONS_NOLISTVIEWS = 0x00000001 は、 **[表示]** メニューに標準のリストビューの選択肢を表示しないようにコンソールに指示します。 スナップインで、結果ビューペインにのみ独自のカスタムビューを表示できるようにします。 これは、現時点で定義されている唯一のオプションフラグです。

- MMC_VIEW_OPTIONS_NONE = 0 に設定すると、既定の表示オプションが使用できます。

##  <a name="getscopepaneinfo"></a>CSnapInItemImpl:: GetScopePaneInfo

スナップインの`SCOPEDATAITEM`構造を取得するには、この関数を呼び出します。

```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```

### <a name="parameters"></a>パラメーター

*pScopeDataItem*<br/>
入出力オブジェクトの構造`SCOPEDATAITEM`体へのポインター。 `CSnapInItemImpl`

##  <a name="getresultpaneinfo"></a>  CSnapInItemImpl::GetResultPaneInfo

スナップインの`RESULTDATAITEM`構造を取得するには、この関数を呼び出します。

```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```

### <a name="parameters"></a>パラメーター

*pResultDataItem*<br/>
入出力オブジェクトの構造`RESULTDATAITEM`体へのポインター。 `CSnapInItemImpl`

##  <a name="m_bstrdisplayname"></a>  CSnapInItemImpl::m_bstrDisplayName

ノード項目に対して表示される文字列を格納します。

```
CComBSTR m_bstrDisplayName;
```

##  <a name="m_scopedataitem"></a>CSnapInItemImpl:: m_scopeDataItem

スナップインデータオブジェクトの構造。`SCOPEDATAITEM`

```
SCOPEDATAITEM m_scopeDataItem;
```

##  <a name="m_resultdataitem"></a>CSnapInItemImpl:: m_resultDataItem

スナップインデータオブジェクトの[Resultdataitem](/windows/win32/api/mmc/ns-mmc-resultdataitem)構造体。

```
RESULTDATAITEM m_resultDataItem;
```

##  <a name="notify"></a>  CSnapInItemImpl::Notify

スナップインオブジェクトがユーザーによって操作されるときに呼び出されます。

```
STDMETHOD(Notify)(
    MMC_NOTIFY_TYPE event,
    long arg,
    long param,
    IComponentData* pComponentData,
    IComponent* pComponent,
    DATA_OBJECT_TYPES type) = 0;
```

### <a name="parameters"></a>パラメーター

*event*<br/>
からユーザーによって実行されるアクションを識別します。 次の通知が可能です。

- MMCN_ACTIVATE は、ウィンドウがアクティブ化され、非アクティブになったときに送信されます。

- MMCN_ADD_IMAGES は、結果ペインに画像を追加するために送信されます。

- MMCN_BTN_CLICK は、ユーザーがツールバーのボタンのいずれかをクリックしたときに送信されます。

- MMCN_CLICK は、ユーザーがリストビュー項目でマウスボタンをクリックしたときに送信されます。

- MMCN_DBLCLICK は、ユーザーがリストビューアイテムのマウスボタンをダブルクリックしたときに送信されます。

- MMCN_DELETE は、オブジェクトを削除する必要があることをスナップインに通知するために送信されます。

- フォルダーの展開または MMCN_EXPAND が必要になったときに送信されます。

- MMCN_MINIMIZED は、ウィンドウが最小化または最大化されているときに送信されます。

- MMCN_PROPERTY_CHANGE スナップインオブジェクトのビューが変更されようとしていることをスナップインオブジェクトに通知するために送信されます。

- MMCN_REMOVE_CHILDREN は、スナップインが、指定されたノードの下に追加されたサブツリー全体を削除する必要があるときに送信されます。

- MMCN_RENAME は、名前を変更するために最初にクエリを実行したとき、2回目に名前の変更を行ったときに送信されます。

- MMCN_SELECT は、スコープまたは結果ビューペイン内の項目が選択されたときに送信されます。

- MMCN_SHOW は、スコープ項目が最初に選択または選択解除されたときに送信されます。

- MMCN_VIEW_CHANGE は、変更が発生したときにスナップインがすべてのビューを更新できるときに送信されます。

*arg*<br/>
から通知の種類によって異なります。

*param*<br/>
から通知の種類によって異なります。

*pComponentData*<br/>
入出力を実装`IComponentData`するオブジェクトへのポインター。 通知がから`IComponentData::Notify`転送されていない場合、このパラメーターは NULL になります。

*pComponent*<br/>
入出力を実装`IComponent`するオブジェクトへのポインター。 通知がから`IComponent::Notify`転送されていない場合、このパラメーターは NULL になります。

*type*<br/>
からオブジェクトの種類を指定します。 次のいずれかの値を指定できます。

- スコープペインコンテキストの CCT_SCOPE Data オブジェクト。

- 結果ペインのコンテキストの CCT_RESULT Data オブジェクト。

- スナップインマネージャーコンテキストの CCT_SNAPIN_MANAGER Data オブジェクト。

- CCT_UNINITIALIZED Data オブジェクトに無効な型が含まれています。

##  <a name="querypagesfor"></a>  CSnapInItemImpl::QueryPagesFor

スナップインノードがプロパティページをサポートしているかどうかを確認するために呼び出されます。

```
QueryPagesFor(DATA_OBJECT_TYPES type);
```

##  <a name="setmenuinsertionflags"></a>  CSnapInItemImpl::SetMenuInsertionFlags

この関数を呼び出して、スナップインオブジェクトの Pインサーター *Tionallowed*で指定されたメニュー挿入フラグを変更します。

```
void SetMenuInsertionFlags(
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```

### <a name="parameters"></a>パラメーター

*bBeforeInsertion*<br/>
から項目をコンテキストメニューに追加する前に関数を呼び出す必要がある場合は0以外の場合は。それ以外の場合は0です。

*許可された ppg tion*<br/>
[入力、出力]Microsoft 管理コンソール (MMC) で定義されている、使用可能なメニュー項目の挿入ポイントを識別します。 これは、次のフラグの組み合わせにすることができます。

- CCM_INSERTIONALLOWED_TOP 項目は、コンテキストメニューの上部に挿入できます。

- CCM_INSERTIONALLOWED_NEW の項目は、[新規作成] サブメニューに挿入できます。

- CCM_INSERTIONALLOWED_TASK の項目は、[タスク] サブメニューに挿入できます。

- CCM_INSERTIONALLOWED_VIEW Items は、ツールバーの [表示] メニュー、または結果ペインのコンテキストメニューの [表示] サブメニューで挿入できます。

### <a name="remarks"></a>Remarks

プライマリスナップインを開発している場合は、サードパーティの拡張機能によって追加できるメニュー項目の種類を制限する方法として、挿入フラグをリセットできます。 たとえば、プライマリスナップインでは、CCM_INSERTIONALLOWED_NEW フラグをクリアして、拡張機能によって独自の [新規作成] メニュー項目が追加されないようにすることができます。

最初はクリアされた Ppg *Tionallowed*にビットを設定しないようにしてください。 将来のバージョンの MMC では、現在定義されていないビットが使用される可能性があるため、現在定義されていないビットを変更することはできません。

##  <a name="settoolbarbuttoninfo"></a>CSnapInItemImpl:: SetToolbarButtonInfo

ツールバーが作成される前に、スナップインオブジェクトのツールバーボタンのスタイルを変更するには、この関数を呼び出します。

```
void SetToolbarButtonInfo(
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```

### <a name="parameters"></a>パラメーター

*ID*<br/>
から設定するツールバーボタンの ID。

*fsState*<br/>
からボタンの状態フラグ。 次の1つまたは複数を指定できます。

- TBSTATE_CHECKED ボタンに TBSTYLE_CHECKED スタイルがあり、押されています。

- TBSTATE_ENABLED ボタンはユーザー入力を受け入れます。 この状態を持たないボタンはユーザー入力を受け付けず、淡色表示になります。

- TBSTATE_HIDDEN ボタンが表示されず、ユーザー入力を受け取ることはできません。

- TBSTATE_INDETERMINATE ボタンがグレーで表示されます。

- TBSTATE_PRESSED ボタンが押されていることを示します。

- TBSTATE_WRAP をクリックすると、このボタンの後に改行が続きます。 このボタンには、TBSTATE_ENABLED も必要です。

*fsType*<br/>
からボタンの状態フラグ。 次の1つまたは複数を指定できます。

- TBSTYLE_BUTTON は、標準のプッシュボタンを作成します。

- TBSTYLE_CHECK は、ユーザーがクリックするたびに押された状態と押されていない状態を切り替えるボタンを作成します。 ボタンの背景色は、押された状態のときに異なります。

- TBSTYLE_CHECKGROUP は、グループ内の別のボタンが押されるまで押された状態を維持するチェックボタンを作成します。

- TBSTYLE_GROUP は、グループ内の別のボタンが押されるまで押されたままになるボタンを作成します。

- TBSTYLE_SEP によって区切り文字が作成され、ボタングループ間のギャップが小さくなります。 このスタイルのボタンは、ユーザー入力を受け取りません。

##  <a name="updatemenustate"></a>CSnapInItemImpl:: UpdateMenuState

スナップインオブジェクトのコンテキストメニューにメニュー項目を挿入する前に、この関数を呼び出してメニュー項目を変更します。

```
void UpdateMenuState(
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```

### <a name="parameters"></a>パラメーター

*ID*<br/>
から設定するメニュー項目の ID。

*pBuf*<br/>
から更新するメニュー項目の文字列へのポインター。

*flags*<br/>
から新しい状態フラグを指定します。 これは、次のフラグの組み合わせにすることができます。

- MF_POPUP は、これがショートカットメニュー内のサブメニューであることを指定します。 メニュー項目、挿入ポイント、およびその`lCommandID`他のサブメニューは、を`IInsertionPointID`として使用することで、このサブメニューに追加できます。

- MF_BITMAP および MF_OWNERDRAW これらのフラグは許可されていないため、E_INVALIDARG の戻り値が返されます。

- MF_SEPARATOR は、水平方向の区切り線を描画します。 MF_SEPARATOR `IContextMenuProvider` set を使用してメニュー項目を追加できるのはのみです。

- MF_CHECKED を指定すると、メニュー項目の横にチェックマークが表示されます。

- MF_DISABLED は選択できないようにメニュー項目を無効にしますが、このフラグはグレーではありません。

- MF_ENABLED では、メニュー項目を選択して淡色表示に戻すことができます。

- MF_GRAYED は、メニュー項目を無効にし、選択できないように graying します。

- MF_MENUBARBREAK は、メニューバーの MF_MENUBREAK フラグと同じように機能します。 ドロップダウンメニュー、サブメニュー、またはショートカットメニューの場合、新しい列は、前の列から縦線で区切られます。

- MF_MENUBREAK は、列を分離せずに、新しい行 (メニューバーの場合) または新しい列 (ドロップダウンメニュー、サブメニュー、またはショートカットメニューの場合) に項目を配置します。

- MF_UNCHECKED は、項目の横にチェックマークを付けません (既定)。

次のフラグのグループを一緒に使用することはできません。

- MF_DISABLED、MF_ENABLED、および MF_GRAYED。

- MF_MENUBARBREAK と MF_MENUBREAK。

- MF_CHECKED と MF_UNCHECKED。

##  <a name="updatetoolbarbutton"></a>CSnapInItemImpl:: UpdateToolbarButton

スナップインオブジェクトのツールバーボタンを表示する前に変更するには、この関数を呼び出します。

```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```

### <a name="parameters"></a>パラメーター

*ID*<br/>
更新するツールバーボタンのボタン ID を指定します。

*fsState*<br/>
ツールバーボタンの状態を指定します。 この状態を設定する場合は、TRUE を返します。 これは、次のフラグの組み合わせにすることができます。

- [有効] に設定すると、ユーザー入力が受け入れられます。 この状態を持たないボタンはユーザー入力を受け付けず、淡色表示になります。

- チェックボックスがオンになっていることを確認します。

- [非表示] ボタンは表示されず、ユーザー入力を受け取ることはできません。

- [不確定] ボタンがグレーで表示されます。

- BUTTONPRESSED れたボタンが押されています。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
